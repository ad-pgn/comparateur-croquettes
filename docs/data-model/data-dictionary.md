# Data dictionary

> Status: conceptual data model (issue #5). Types are MySQL types.
> Constraints (NOT NULL, UNIQUE, CHECK, foreign keys, indexes) are finalised in the logical data model (issue #6).
> "Req." = required (cannot be empty).

## Naming conventions

- English, `snake_case`, singular table names.
- Each identifier is named `<entity>_id` (e.g. `brand_id`), so that generated foreign keys keep a meaningful name.
- MySQL reserved words are avoided (e.g. `range`, `rank`, `user`), as well as ambiguous keywords (`source`, `value`, `type`, `format`).
- Dates: `*_on` for a date (`recorded_on`), `*_at` for a date and time (`created_at`).
- Booleans: `is_*` or an adjective (`grain_free`).
- In the conceptual data model (Looping), entity names are written in uppercase, following the Merise convention; physical table names are lowercase.

---

## 1. Catalogue

### brand — Brand (marque)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `brand_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(100) | Yes | Brand name, unique |
| `slug` | VARCHAR(120) | Yes | URL-friendly name, unique (e.g. `royal-canin`) |
| `website_url` | VARCHAR(2048) | No | Official website |

### product_line — Product line (gamme)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `product_line_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(100) | Yes | Line name, unique within its brand |
| `slug` | VARCHAR(120) | Yes | URL-friendly name |

### product — Product (produit)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `product_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(200) | Yes | Product name as sold |
| `slug` | VARCHAR(220) | Yes | URL-friendly name, unique |
| `label_composition` | TEXT | No | Composition exactly as written on the label |
| `grain_free` | BOOLEAN | Yes | Grain-free claim declared by the manufacturer (default: false) |
| `status` | VARCHAR(20) | Yes | `draft`, `published` or `archived` (RG-09) |
| `verification_status` | VARCHAR(20) | Yes | `verified` or `unverified` (RG-08) |
| `created_at` | DATETIME | Yes | Creation date |
| `updated_at` | DATETIME | Yes | Last update date |
| `version` | INT | Yes | Optimistic locking counter, incremented on each update (RG-18) |

### packaging — Package size (format)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `packaging_id` | INT, auto-increment | Yes | Identifier |
| `net_weight_g` | INT | Yes | Net weight in grams (integer: no rounding issues) |
| `ean` | VARCHAR(14) | No | Barcode, unique. Stored as text: leading zeros must be kept and no calculation is done on it |

### species — Species (espèce)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `species_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(50) | Yes | Species name, unique |

### food_type — Food type (type d'aliment)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `food_type_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(50) | Yes | Food type name, unique |

### life_stage — Life stage (stade de vie)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `life_stage_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(50) | Yes | Life stage name, unique within its species |

### body_size — Dog size (gabarit)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `body_size_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(50) | Yes | Size name, unique within its species |

### specific_need — Specific need (besoin spécifique)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `specific_need_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(100) | Yes | Need name, unique |

---

## 2. Composition

### ingredient — Ingredient (ingrédient normalisé)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `ingredient_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(150) | Yes | Normalised ingredient name, unique |

### additive — Additive (additif)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `additive_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(150) | Yes | Additive name |
| `eu_code` | VARCHAR(20) | No | EU identification number, unique |
| `category` | VARCHAR(50) | Yes | EU additive category (e.g. nutritional, technological, sensory) |
| `functional_group` | VARCHAR(100) | No | Functional group (e.g. colourants) |

### constituent — Analytical constituent (constituant analytique)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `constituent_id` | INT, auto-increment | Yes | Identifier |
| `code` | VARCHAR(30) | Yes | Stable technical code, unique (e.g. `protein`, `fat`, `fibre`, `ash`, `moisture`); used by business rules (RG-07) and API filters |
| `name` | VARCHAR(100) | Yes | Constituent name, unique |
| `unit` | VARCHAR(20) | Yes | Unit (`%`, `mg/kg`, `IU/kg`…) |
| `is_mandatory` | BOOLEAN | Yes | Mandatory on the label (used by publication rule RG-10) |
| `display_order` | SMALLINT | Yes | Order in product pages and comparison tables |

---

## 3. Prices and traceability

### price_record — Price record (relevé de prix)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `price_record_id` | INT, auto-increment | Yes | Identifier |
| `price` | DECIMAL(7,2) | Yes | Price including VAT, in euros. DECIMAL avoids floating-point rounding errors |
| `price_type` | VARCHAR(20) | Yes | `rrp` (brand recommended price), `direct` (brand direct sale) or `retailer` (RG-03) |
| `recorded_on` | DATE | Yes | Date of the price record |
| `url` | VARCHAR(2048) | Yes | Page where the price was recorded |

The price per kg is **not stored**: it is calculated from `price` and `net_weight_g` (RG-05).

### seller — Seller (enseigne)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `seller_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(100) | Yes | Retailer or brand website name, unique |
| `website_url` | VARCHAR(2048) | No | Website |

### data_source — Data source (source des données d'un produit)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `data_source_id` | INT, auto-increment | Yes | Identifier |
| `source_type` | VARCHAR(30) | Yes | `manufacturer_website`, `label` or `open_pet_food_facts` |
| `url` | VARCHAR(2048) | No | Source page |
| `consulted_on` | DATE | Yes | Consultation date (RG-08) |
| `external_id` | VARCHAR(100) | No | Identifier in the external source (e.g. Open Pet Food Facts barcode) |

---

## 4. Users

### user_account — User account (utilisateur)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `user_account_id` | INT, auto-increment | Yes | Identifier |
| `email` | VARCHAR(254) | Yes | Email address, unique (254: maximum length of an email address) |
| `password_hash` | VARCHAR(255) | Yes | Argon2id hash, never the password itself |
| `role` | VARCHAR(20) | Yes | `member` or `admin` |
| `privacy_accepted_at` | DATETIME | Yes | Acceptance of the privacy policy (proof of consent) |
| `created_at` | DATETIME | Yes | Account creation date |

### comparison — Saved comparison (comparaison)

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `comparison_id` | INT, auto-increment | Yes | Identifier |
| `name` | VARCHAR(100) | Yes | Name given by the member |
| `created_at` | DATETIME | Yes | Creation date |

---

## 5. Associations

### One-to-many associations (no table of their own)

| Association | Entity (cardinality) | Entity (cardinality) |
|---|---|---|
| `offers` | brand (0,n) | product_line (1,1) |
| `groups` | product_line (0,n) | product (1,1) |
| `concerns` | species (0,n) | product (1,1) |
| `classifies` | food_type (0,n) | product (1,1) |
| `defines_stage` | species (0,n) | life_stage (1,1) |
| `defines_size` | species (0,n) | body_size (1,1) |
| `is_sold_as` | product (0,n) | packaging (1,1) |
| `is_priced` | packaging (0,n) | price_record (1,1) |
| `supplies` | seller (0,n) | price_record (1,1) |
| `documents` | product (0,n) | data_source (1,1) |
| `creates` | user_account (0,n) | comparison (1,1) |

### Many-to-many associations (they become tables)

| Association | Entity (cardinality) | Entity (cardinality) | Attributes |
|---|---|---|---|
| `product_life_stage` | product (0,n) | life_stage (0,n) | — |
| `product_body_size` | product (0,n) | body_size (0,n) | — |
| `product_specific_need` | product (0,n) | specific_need (0,n) | — |
| `product_ingredient` | product (0,n) | ingredient (0,n) | see below |
| `product_additive` | product (0,n) | additive (0,n) | see below |
| `product_constituent` | product (0,n) | constituent (0,n) | see below |
| `favorite` | user_account (0,n) | product (0,n) | see below |
| `comparison_product` | comparison (1,n) | product (0,n) | see below |

#### product_ingredient

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `label_order` | SMALLINT | Yes | Position of the ingredient on the label (1 = first) |
| `percentage` | DECIMAL(5,2) | No | Percentage declared on the label, if any |
| `label_wording` | VARCHAR(255) | No | Exact wording on the label |

#### product_additive

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `quantity` | DECIMAL(10,3) | No | Declared quantity |
| `unit` | VARCHAR(20) | No | Unit of the quantity (`mg/kg`, `IU/kg`…) |

#### product_constituent

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `amount` | DECIMAL(10,3) | Yes | Declared value, in the unit of the constituent |

#### favorite

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `added_at` | DATETIME | Yes | Date the product was added to favourites |

#### comparison_product

| Attribute | Type | Req. | Description |
|---|---|---|---|
| `display_order` | SMALLINT | Yes | Column position of the product in the comparison |

---

## 6. Rules not expressed in the model

These rules cannot be expressed with cardinalities; they are enforced by the API service layer:

- a comparison contains 2 to 4 products (RG-13);
- a product can only be published when complete (RG-10);
- the life stages and sizes of a product belong to the same species as the product;
- a price record comes from an allowed seller (RG-04).

---

## 7. Logical data model

Generated with Looping from the conceptual data model: 25 tables (17 entities and 8 join tables).
The physical SQL script (MySQL) is written and tested in milestone M2.

### Relational schema

Notation: primary key in **bold**, foreign key prefixed with `#`.

- brand(**brand_id**, name, slug, website_url)
- product_line(**product_line_id**, name, slug, #brand_id)
- species(**species_id**, name)
- food_type(**food_type_id**, name)
- life_stage(**life_stage_id**, name, #species_id)
- body_size(**body_size_id**, name, #species_id)
- specific_need(**specific_need_id**, name)
- product(**product_id**, name, slug, label_composition, grain_free, status, verification_status, created_at, updated_at, version, #product_line_id, #species_id, #food_type_id)
- packaging(**packaging_id**, net_weight_g, ean, #product_id)
- seller(**seller_id**, name, website_url)
- price_record(**price_record_id**, price, price_type, recorded_on, url, #packaging_id, #seller_id)
- data_source(**data_source_id**, source_type, url, consulted_on, external_id, #product_id)
- ingredient(**ingredient_id**, name)
- additive(**additive_id**, name, eu_code, category, functional_group)
- constituent(**constituent_id**, code, name, unit, is_mandatory, display_order)
- user_account(**user_account_id**, email, password_hash, role, privacy_accepted_at, created_at)
- comparison(**comparison_id**, name, created_at, #user_account_id)
- product_life_stage(**#product_id, #life_stage_id**)
- product_body_size(**#product_id, #body_size_id**)
- product_specific_need(**#product_id, #specific_need_id**)
- product_ingredient(**#product_id, #ingredient_id**, label_order, percentage, label_wording)
- product_additive(**#product_id, #additive_id**, quantity, unit)
- product_constituent(**#product_id, #constituent_id**, amount)
- favorite(**#user_account_id, #product_id**, added_at)
- comparison_product(**#comparison_id, #product_id**, display_order)

The composite primary key of a join table also prevents duplicates: for example, a product can only be added once
to a member's favourites (RG-16).

### Unique constraints

In addition to primary keys and the single-column unique constraints listed above:

| Table | Columns | Reason |
|---|---|---|
| `product_line` | (`brand_id`, `name`) | A line name is unique within its brand |
| `product_line` | (`brand_id`, `slug`) | A line slug is unique within its brand |
| `life_stage` | (`species_id`, `name`) | A life stage is unique within its species |
| `body_size` | (`species_id`, `name`) | A size is unique within its species |
| `product_ingredient` | (`product_id`, `label_order`) | Two ingredients cannot share the same position on a label |

### Check constraints

List values are stored as `VARCHAR` with a `CHECK` constraint rather than MySQL `ENUM`
(`ENUM` sorts by declaration order and is MySQL-specific).

| Table.column | Condition |
|---|---|
| `product.status` | in (`draft`, `published`, `archived`) |
| `product.verification_status` | in (`verified`, `unverified`) |
| `user_account.role` | in (`member`, `admin`) |
| `price_record.price_type` | in (`rrp`, `direct`, `retailer`) |
| `data_source.source_type` | in (`manufacturer_website`, `label`, `open_pet_food_facts`) |
| `packaging.net_weight_g` | > 0 |
| `price_record.price` | > 0 |
| `product_ingredient.label_order` | >= 1 |
| `product_ingredient.percentage` | between 0 and 100 |
| `product_additive.quantity` | >= 0 |
| `product_constituent.amount` | >= 0 |
| `comparison_product.display_order` | between 1 and 4 (maximum of RG-13; the minimum of 2 products is checked by the API) |

### Foreign keys and delete behaviour

`RESTRICT`: deletion is refused while the row is referenced. `CASCADE`: dependent rows are deleted too.
Identifiers are surrogate keys that never change, so no `ON UPDATE` action is needed.

| Foreign key | References | On delete | Reason |
|---|---|---|---|
| `product_line.brand_id` | `brand` | RESTRICT | A brand in use cannot be deleted (US-16) |
| `product.product_line_id` | `product_line` | RESTRICT | A line in use cannot be deleted (US-16) |
| `product.species_id` | `species` | RESTRICT | Reference data |
| `product.food_type_id` | `food_type` | RESTRICT | Reference data |
| `life_stage.species_id` | `species` | RESTRICT | Reference data |
| `body_size.species_id` | `species` | RESTRICT | Reference data |
| `packaging.product_id` | `product` | CASCADE | A package size does not exist without its product |
| `price_record.packaging_id` | `packaging` | CASCADE | A price record does not exist without its package size |
| `price_record.seller_id` | `seller` | RESTRICT | A price record keeps its source |
| `data_source.product_id` | `product` | CASCADE | A source does not exist without its product |
| `product_life_stage.product_id`, `product_body_size.product_id`, `product_specific_need.product_id`, `product_ingredient.product_id`, `product_additive.product_id`, `product_constituent.product_id` | `product` | CASCADE | Links are deleted with the product |
| `product_life_stage.life_stage_id`, `product_body_size.body_size_id`, `product_specific_need.specific_need_id`, `product_ingredient.ingredient_id`, `product_additive.additive_id`, `product_constituent.constituent_id` | reference tables | RESTRICT | A reference item in use cannot be deleted (US-18) |
| `comparison.user_account_id` | `user_account` | CASCADE | Account deletion erases the member's data (RG-17) |
| `favorite.user_account_id` | `user_account` | CASCADE | Same reason (RG-17) |
| `comparison_product.comparison_id` | `comparison` | CASCADE | Links are deleted with the comparison |
| `favorite.product_id` | `product` | RESTRICT | A product used by a member is archived, never deleted (RG-11) |
| `comparison_product.product_id` | `product` | RESTRICT | Same reason (RG-11) |

Consequence: only products never used by members (typically drafts) can be deleted; published products are archived.

### Additional indexes

InnoDB automatically indexes every foreign key column. Additional indexes are created only for known queries:

| Index | Query |
|---|---|
| `product(status)` | Public pages only show published products |
| `price_record(packaging_id, recorded_on)` | Latest price record of a package size |
| `product_constituent(constituent_id, amount)` | Range filters on analytical constituents (US-02) |

### To be handled in the physical script (milestone M2)

- Lowercase table names, InnoDB engine (transactions and foreign keys).
- `utf8mb4` character set with an accent-insensitive collation (a search for "proteines" finds "protéines").
- `INT AUTO_INCREMENT` identifiers and `BOOLEAN` columns (the Looping script uses generic types).
- Default values: `version` = 0, `created_at` and `updated_at` set automatically.
- `session` table for authentication sessions: created by the script, because the application database user
  is not allowed to create tables (least privilege).