# REST API contract

> Status: designed during the design phase (issue #8). Nothing described here is implemented yet.
> An OpenAPI specification will be written alongside the code during development.

## 1. General conventions

| Topic | Convention |
|---|---|
| Base path | `/api` (same origin as the web application, see `docs/architecture.md`) |
| Versioning | No version in the URL: the API has a single client, deployed together with it |
| Format | JSON (`Content-Type: application/json`), UTF-8 |
| Paths | Plural nouns, `kebab-case` (`/api/product-lines`) |
| JSON fields | `camelCase` (`netWeightG`, `pricePerKg`); database columns stay in `snake_case` |
| Public identifiers | Slugs for pages indexed by search engines (`/api/products/{slug}`); numeric ids elsewhere |
| Dates | ISO 8601, UTC (`2026-10-05T14:30:00Z`); dates without time as `2026-10-05` |
| Decimal values | JSON numbers (prices rounded to 2 decimals) |
| Authentication | Session cookie (see `docs/architecture.md`, section 4) |
| Access levels | **Public**, **Member** (logged-in user), **Admin** |

## 2. Responses

### Success

A single resource:

```json
{ "data": { "id": 12, "name": "Adult Large Breed" } }
```

A list, with pagination metadata:

```json
{
  "data": [ { "id": 12, "name": "Adult Large Breed" } ],
  "meta": { "page": 1, "pageSize": 20, "totalItems": 43, "totalPages": 3 }
}
```

### Errors

Errors follow the **Problem Details** standard (RFC 9457), content type `application/problem+json`, with two extension fields: a machine-readable `code` and, for validation errors, the list of invalid fields.

```json
{
  "type": "about:blank",
  "title": "Validation failed",
  "status": 400,
  "code": "VALIDATION_ERROR",
  "detail": "Some fields are invalid.",
  "errors": [
    { "field": "email", "message": "Must be a valid email address." },
    { "field": "password", "message": "Must contain at least 12 characters." }
  ]
}
```

No stack trace, SQL message or internal detail is ever returned.

### Status codes

| Code | Use |
|---|---|
| 200 OK | Successful read or update |
| 201 Created | Resource created (with a `Location` header) |
| 204 No Content | Successful deletion or action without content |
| 400 Bad Request | Invalid input (malformed JSON, invalid field, invalid query parameter) |
| 401 Unauthorized | Not authenticated |
| 403 Forbidden | Authenticated but not allowed (role), or rejected `Origin` header |
| 404 Not Found | Resource not found (also returned for unpublished products on public routes) |
| 409 Conflict | Uniqueness violation, resource in use, concurrent modification (`VERSION_CONFLICT`) |
| 422 Unprocessable Content | Valid input breaking a business rule that cannot be checked by validation alone (e.g. publication conditions, RG-10) |
| 429 Too Many Requests | Rate limit reached (login attempts) |
| 500 Internal Server Error | Unexpected error |
| 502 / 503 / 504 | External service error (Open Pet Food Facts import) |

## 3. Pagination, sorting and filtering

### Pagination

Page-based: `?page=2&pageSize=20`. Default page size 20, maximum 50.
Page numbers fit the user interface (numbered pages) and give shareable URLs; cursor-based pagination is not needed for a catalogue of this size.

### Sorting

`?sort=<field>`; a leading `-` means descending order.

| Value | Order |
|---|---|
| `name` (default) | Product name |
| `pricePerKg`, `-pricePerKg` | Lowest recorded price per kg; products without price come last (US-04) |
| `<constituent code>`, `-<constituent code>` | Value of an analytical constituent, e.g. `-protein` |

### Product filters (`GET /api/products`)

| Parameter | Example | Meaning |
|---|---|---|
| `q` | `q=adult` | Name or brand contains the text (at least 2 characters) |
| `brand` | `brand=3,7` | Brand ids (any of) |
| `productLine` | `productLine=12` | Product line ids (any of) |
| `lifeStage` | `lifeStage=2` | Life stage ids (any of) |
| `bodySize` | `bodySize=4` | Size ids (any of) |
| `need` | `need=1,5` | Specific need ids (all of) |
| `grainFree` | `grainFree=true` | Grain-free claim |
| `range` | `range=protein:25:30&range=fat::15` | Constituent value range `<code>:<min>:<max>` (empty bound = unbounded), repeatable |
| `excludeIngredients` | `excludeIngredients=8,41` | Products containing none of these ingredients (RG-14) |
| `excludeAdditives` | `excludeAdditives=3` | Products containing none of these additives |
| `excludeFunctionalGroups` | `excludeFunctionalGroups=colourants` | Products containing no additive of these groups |
| `maxPricePerKg` | `maxPricePerKg=8.5` | Lowest recorded price per kg below this value |

All filters are combined with AND. Unknown or invalid parameters return 400.

## 4. Endpoints

### Health

| Method | Path | Access | Description | Responses |
|---|---|---|---|---|
| GET | `/api/health` | Public | Service and database status (deployment checks) | 200, 503 |

### Catalogue (public)

| Method | Path | Access | Description | Responses | Story |
|---|---|---|---|---|---|
| GET | `/api/products` | Public | Published products: search, filters, sorting, pagination | 200, 400 | US-01 to US-04 |
| GET | `/api/products/{slug}` | Public | Published product detail, with prices, sources and dry matter values | 200, 404 | US-05, US-08 |
| GET | `/api/products/compare?ids=12,15,21` | Public | 2 to 4 published products, aligned for comparison, with as-fed and dry matter values | 200, 400, 404 | US-07, US-08 |
| GET | `/api/brands` | Public | Brands having published products | 200 | US-02 |
| GET | `/api/product-lines?brand=3` | Public | Product lines (optionally of a brand) | 200 | US-02 |
| GET | `/api/life-stages` | Public | Life stages | 200 | US-02 |
| GET | `/api/body-sizes` | Public | Sizes | 200 | US-02 |
| GET | `/api/specific-needs` | Public | Specific needs | 200 | US-02 |
| GET | `/api/constituents` | Public | Constituents (code, name, unit, display order) | 200 | US-02, US-07 |
| GET | `/api/ingredients?q=chick` | Public | Ingredient search for the exclusion filter | 200, 400 | US-03 |
| GET | `/api/additives?q=E1` | Public | Additive search for the exclusion filter | 200, 400 | US-03 |

Calculated values (price per kg, dry matter values, outdated price flag) are computed by the API; the web application contains no business logic.

### Authentication

| Method | Path | Access | Description | Responses | Story |
|---|---|---|---|---|---|
| POST | `/api/auth/register` | Public | Create a member account | 201, 400, 409 | US-09 |
| POST | `/api/auth/login` | Public | Log in (new session id) | 200, 400, 401, 429 | US-10 |
| POST | `/api/auth/logout` | Member | Log out (session deleted) | 204 | US-10 |
| GET | `/api/auth/me` | Public | Current user, or 401 if not logged in | 200, 401 | US-10 |

Login errors always return the same generic message, whether the email address exists or not.

### Member area

| Method | Path | Access | Description | Responses | Story |
|---|---|---|---|---|---|
| GET | `/api/me/favorites` | Member | Favourite products | 200, 401 | US-11 |
| PUT | `/api/me/favorites/{productId}` | Member | Add a favourite (idempotent: adding twice changes nothing) | 204, 401, 404 | US-11 |
| DELETE | `/api/me/favorites/{productId}` | Member | Remove a favourite | 204, 401 | US-11 |
| GET | `/api/me/comparisons` | Member | Saved comparisons | 200, 401 | US-13 |
| POST | `/api/me/comparisons` | Member | Save a comparison (`name`, 2 to 4 `productIds`) | 201, 400, 401 | US-12 |
| GET | `/api/me/comparisons/{id}` | Member | Saved comparison, archived products flagged as withdrawn | 200, 401, 404 | US-13 |
| DELETE | `/api/me/comparisons/{id}` | Member | Delete a saved comparison | 204, 401, 404 | US-13 |
| POST | `/api/me/deletion` | Member | Delete the account (password confirmation in the body) | 204, 400, 401 | US-14 |

A member can only access their own data: a comparison of another member returns 404 (its existence is not revealed).
Account deletion uses `POST` with a body rather than `DELETE`, because a body on a `DELETE` request has no defined meaning in HTTP.

### Back office

All routes under `/api/admin` require the **Admin** role: 401 if not logged in, 403 for a member (US-15).

| Method | Path | Description | Responses | Story |
|---|---|---|---|---|
| GET, POST | `/api/admin/brands` | List, create brands | 200, 201, 400, 409 | US-16 |
| PATCH, DELETE | `/api/admin/brands/{id}` | Update, delete (refused if in use) | 200, 204, 400, 404, 409 | US-16 |
| GET, POST | `/api/admin/product-lines` | List, create product lines | 200, 201, 400, 409 | US-16 |
| PATCH, DELETE | `/api/admin/product-lines/{id}` | Update, delete (refused if in use) | 200, 204, 400, 404, 409 | US-16 |
| GET, POST | `/api/admin/{reference}` | List, create reference items | 200, 201, 400, 409 | US-18 |
| PATCH, DELETE | `/api/admin/{reference}/{id}` | Update, delete (refused if in use) | 200, 204, 400, 404, 409 | US-18 |
| GET, POST | `/api/admin/sellers` | List, create sellers | 200, 201, 400, 409 | US-19 |
| PATCH, DELETE | `/api/admin/sellers/{id}` | Update, delete (refused if in use) | 200, 204, 400, 404, 409 | US-19 |
| GET | `/api/admin/products?status=draft` | All products, any status | 200, 400 | US-17 |
| POST | `/api/admin/products` | Create a complete product in one transaction (optional `importId`) | 201, 400, 409, 422 | US-17, US-20 |
| GET | `/api/admin/products/{id}` | Complete product, including its `version` | 200, 404 | US-17 |
| PUT | `/api/admin/products/{id}` | Replace a complete product; the request must contain the `version` read | 200, 400, 404, 409, 422 | US-17 |
| DELETE | `/api/admin/products/{id}` | Delete (refused if used by members: archive instead) | 204, 404, 409 | US-21 |
| PATCH | `/api/admin/products/{id}/status` | Change status (`draft`, `published`, `archived`) | 200, 400, 404, 422 | US-21 |
| POST | `/api/admin/price-records` | Record a dated price for a package size | 201, 400, 404 | US-19 |
| GET | `/api/admin/price-records?outdated=true` | Price records to update (older than 90 days) | 200 | US-19 |
| POST | `/api/admin/imports` | Import a barcode from Open Pet Food Facts; returns the pre-filled proposal | 201, 400, 404, 409, 502, 503, 504 | US-20 |
| GET | `/api/admin/imports/{id}` | Import and its proposal | 200, 404 | US-20 |
| PATCH | `/api/admin/imports/{id}` | Reject an import (`status: rejected`) | 200, 400, 404 | US-20 |

`{reference}` is one of: `ingredients`, `additives`, `constituents`, `specific-needs`, `life-stages`, `body-sizes`.

**Concurrent modification (RG-18)**: `PUT /api/admin/products/{id}` compares the `version` sent with the stored one. If they differ, the update is refused with 409 and the code `VERSION_CONFLICT`; the administrator reloads the product.

**Publication (RG-10)**: if conditions are not met, `PATCH /api/admin/products/{id}/status` returns 422 with the code `PUBLICATION_REQUIREMENTS_NOT_MET` and the list of missing items in `errors`.

## 5. Examples

### Product in a list

```json
{
  "id": 12,
  "slug": "royal-canin-maxi-adult",
  "name": "Maxi Adult",
  "brand": { "id": 3, "name": "Royal Canin", "slug": "royal-canin" },
  "productLine": { "id": 7, "name": "Size Health Nutrition" },
  "grainFree": false,
  "lowestPricePerKg": { "value": 6.12, "seller": "Zooplus", "recordedOn": "2026-09-28", "isOutdated": false }
}
```

Values are illustrative only: they are not real product data.

### Version conflict

```json
{
  "type": "about:blank",
  "title": "Conflict",
  "status": 409,
  "code": "VERSION_CONFLICT",
  "detail": "This product was modified by another administrator. Reload it before saving again."
}
```

## 6. Security rules applied to every endpoint

- Every input (body, path, query) is validated with Zod schemas before reaching the controllers.
- State-changing requests (`POST`, `PUT`, `PATCH`, `DELETE`) are rejected with 403 if the `Origin` header is not the application origin.
- Roles are checked by middleware on the API, never only by the user interface.
- Public routes only expose published products; drafts and archived products return 404.
- Login is rate limited; request bodies are size limited.
