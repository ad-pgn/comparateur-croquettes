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
