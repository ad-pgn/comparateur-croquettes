# Visual identity

> Status: validated during the design phase (issue #9), completed during the mockups (issue #11).
> These values are the single source of truth for the Figma variables and the CSS custom properties of the web application.

## 1. Principles

- **Sober and calm**: one brand colour (sage), neutral greys, generous white space.
- **Neutral comparison (RG-12)**: no green/red or "good/bad" colour coding on product values. In comparison tables, extreme values are shown in bold with a neutral marker (▲ highest, ▼ lowest), explained by a legend. Red is reserved for errors and destructive actions.
- **Accessible (RGAA)**: every text colour reaches a contrast ratio of at least 4.5:1 on its background; interactive component boundaries (input borders, focus indicator) reach at least 3:1. All ratios below were calculated, not estimated.
- **Light theme only** in the MVP (dark theme: possible future evolution).
- **Eco-design**: one self-hosted font, two weights, no decorative images.

## 2. Colours

### Palette

| Token | Value | Use |
|---|---|---|
| `--color-bg` | `#FAFAF7` | Page background |
| `--color-surface` | `#FFFFFF` | Cards, tables, form fields |
| `--color-surface-alt` | `#F1F3F0` | Alternate rows, secondary areas, information tags |
| `--color-text` | `#1F2A2E` | Main text, headings |
| `--color-text-muted` | `#55626A` | Secondary text, metadata (dates, sources), placeholders |
| `--color-primary` | `#2F6B5A` | Primary buttons, links, focus indicator |
| `--color-primary-hover` | `#24564A` | Hover and active state of primary elements |
| `--color-on-primary` | `#FFFFFF` | Text on primary background |
| `--color-primary-soft` | `#E4EFEA` | Active filters, active navigation item, table group rows, success messages |
| `--color-primary-strong` | `#24564A` | Text on `--color-primary-soft` |
| `--color-border` | `#D9DDD8` | Decorative separators only |
| `--color-border-strong` | `#7F8984` | Form field borders, table header separator, interactive boundaries |
| `--color-error` | `#B42318` | Error text and borders, destructive actions |
| `--color-error-bg` | `#FDECEA` | Error message background, hover of destructive buttons |
| `--color-warning` | `#8A5A00` | Warning text (e.g. outdated price, RG-06) |
| `--color-warning-bg` | `#FDF3E1` | Warning message background |

`primary-hover` and `primary-strong` share the same value but have different roles, so that they can evolve separately.

### Contrast ratios (WCAG formula)

| Foreground | Background | Ratio | Required |
|---|---|---|---|
| `--color-text` | `--color-bg` | 14.05 | 4.5 |
| `--color-text` | `--color-surface` | 14.70 | 4.5 |
| `--color-text` | `--color-surface-alt` | 13.17 | 4.5 |
| `--color-text-muted` | `--color-bg` | 6.01 | 4.5 |
| `--color-text-muted` | `--color-surface-alt` | 5.63 | 4.5 |
| `--color-text-muted` | `--color-primary-soft` | 5.34 | 4.5 |
| `--color-primary` (links) | `--color-surface` | 6.23 | 4.5 |
| `--color-on-primary` | `--color-primary` | 6.23 | 4.5 |
| `--color-on-primary` | `--color-primary-hover` | 8.38 | 4.5 |
| `--color-primary-strong` | `--color-primary-soft` | 7.12 | 4.5 |
| `--color-error` | `--color-surface` | 6.57 | 4.5 |
| `--color-error` | `--color-error-bg` | 5.75 | 4.5 |
| `--color-warning` | `--color-warning-bg` | 5.39 | 4.5 |
| `--color-border-strong` | `--color-surface` | 3.61 | 3 |
| `--color-border-strong` | `--color-bg` | 3.45 | 3 |
| `--color-border-strong` | `--color-surface-alt` | 3.24 | 3 |
| `--color-primary` (focus ring) | `--color-bg` | 5.96 | 3 |

`--color-border` (1.37:1 on white) is only allowed for purely decorative separators, never to identify an interactive element.

## 3. Typography

**Font: Source Sans 3** (SIL Open Font License), self-hosted with `next/font/google`: visitors' browsers never contact Google servers.
Fallback: `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.

| Token | Size | Line height | Weight | Use |
|---|---|---|---|---|
| `--font-size-xs` | 0.875rem (14px) | 1.4 | 400 | Captions, metadata |
| `--font-size-sm` | 1rem (16px) | 1.5 | 400 | Body text (minimum size for body text) |
| `--font-size-sm` (strong) | 1rem (16px) | 1.5 | 600 | Button labels, emphasized text |
| `--font-size-md` | 1.125rem (18px) | 1.5 | 400 | Lead text |
| `--font-size-lg` | 1.25rem (20px) | 1.4 | 600 | Card titles, h4, group titles |
| `--font-size-xl` | 1.5rem (24px) | 1.3 | 600 | Section titles (h2) |
| `--font-size-2xl` | 1.875rem (30px) | 1.25 | 600 | Large section titles |
| `--font-size-3xl` | 2.25rem (36px) | 1.2 | 600 | Page title (h1), on all screen sizes |

- Two weights only: 400 (regular) and 600 (semibold).
- Sizes in `rem`: text follows the browser font size set by the user.
- The h1 keeps 36px on mobile: tested with a long product name, it stays within three lines at 393px.
- Numbers in tables and prices use **tabular figures** (`font-variant-numeric: tabular-nums`) so that values align in columns.
- French typography: a space between a number and its unit (`26 %`, `15 kg`, `3 937 kcal/kg`).

## 4. Spacing, sizes and layout

### Tokens

| Token | Value |
|---|---|
| `--space-1` | 0.25rem (4px) |
| `--space-2` | 0.5rem (8px) |
| `--space-3` | 0.75rem (12px) |
| `--space-4` | 1rem (16px) |
| `--space-5` | 1.5rem (24px) |
| `--space-6` | 2rem (32px) |
| `--space-7` | 3rem (48px) |
| `--space-8` | 4rem (64px) |

| Token | Value | Use |
|---|---|---|
| `--radius-xs` | 4px | Checkboxes |
| `--radius-sm` | 6px | Buttons, fields, tags, navigation items |
| `--radius-md` | 12px | Cards, dialogs |
| `--shadow-popover` | `0 4px 16px rgb(31 42 46 / 12%)` | Dialogs and dropdowns |
| `--shadow-bar` | `0 -4px 16px rgb(31 42 46 / 12%)` | Bars fixed at the bottom of the screen (shadow cast upwards) |
| `--focus-ring` | `0 0 0 2px var(--color-bg), 0 0 0 4px var(--color-primary)` | Keyboard focus (`:focus-visible`), applied as `box-shadow` |
| `--target-min` | 44px | Minimum size of touch targets |
| `--content-max` | 1200px | Maximum width of public pages content |
| `--form-max` | 1000px | Maximum width of back-office forms |

### Layout rules

| Rule | Mobile | Desktop |
|---|---|---|
| Reference screen | 393 × 852px (tested down to 360px) | 1440 × 1024px |
| Layout grid | 4 columns, 16px margins and gutters | 12 columns, 24px gutters, 120px margins (1200px content) |
| Space between page sections | 32px (`space-6`) | 48px (`space-7`) |
| Space between a title and its intro text | 12px (`space-3`) | 12px |
| Space between the intro and the search | 24px (`space-5`) | 24px |
| Back-office | — | 240px sidebar; content with 32px margins |

- Related elements are closer to each other than to unrelated elements (proximity).
- The footer stays at the bottom of the screen when the page is short (minimum page height equal to the viewport).
- When a bar is fixed at the bottom of the screen (comparison bar, filter actions), the page gets a bottom padding equal to its height, so that the last content is never hidden.

Breakpoints (mobile first): `600px` (large phones), `900px` (tablets), `1200px` (desktop).

## 5. Logos

| File | Use |
|---|---|
| `docs/design/logo/comparateur-croquettes-badge.svg` | Large formats: home illustration, social networks, dossier cover |
| Header brand: badge + name | 44px badge alone on mobile; 48px badge followed by "comparateur-croquettes" (`text/lg`, "croquettes" in `primary`) on desktop |
| `docs/design/logo/favicon/` | Browser tab (`favicon.ico`: 16, 32, 48px), Android (`icon-192.png`, `icon-512.png`), iOS (`apple-touch-icon.png`, 180px, opaque) |

- Origin: the badge was generated with an AI image service (OpenAI, according to the C2PA metadata of the image), then vectorized with VTracer and optimized with Scour. The favicon is a crop of the badge portrait.
- The header logo is a link to the home page, with the accessible name "comparateur-croquettes — accueil".

## 6. Icons

Library: **Lucide** (ISC licence), the same in Figma and in React (`lucide-react`). Icons are outlined (stroke 2px on a 24px grid); they are resized proportionally, stroke included.

Icons in use: `check`, `x`, `triangle-alert`, `circle-user-round`, `chevron-down`, `arrow-up`, `arrow-down`, `plus`.

## 7. Components

Component names and properties match the future React components and their props.

### Base components

| Component | Properties |
|---|---|
| `Button` | `variant`: primary, secondary, danger; `state`: default, hover, focus |
| `TextField` | `state`: default, focus, error; `hasLabel`, `hasHelp`, `hasError`, `hasToggle` |
| `Select` | `state`: default, focus, error; `hasLabel`, `hasError` |
| `Checkbox` | `checked`: true, false |
| `Tag` | Information label, not clickable |
| `Chip` | `variant`: link (quick access), active (active filter, removable) |
| `Alert` | `variant`: error, warning, success |
| `FilterSection` | `expanded`: true, false |
| `NavItem` | `active`: true, false |

### Composed components

| Component | Properties |
|---|---|
| `ProductCard` | `selected`: true, false; `priceStatus`: current, outdated |
| `Header` | `format`: mobile, desktop; `auth`: visitor, member |
| `Footer` | `format`: mobile, desktop |
| `Pagination` | `page`: first, middle |
| `SegmentedControl` | `value`: raw, dry |
| `Dialog` | `hasField` (password confirmation) |
| `TableCell` | `type`: header, body, body-alt, row-header, corner, group |
| `CompareBar` | `format`: mobile, desktop |
| `AdminSidebar` | — |
| `Brand` | `format`: mobile, desktop |

### Rules of use

- Colour is never the only way to convey information: errors also have a text message and an icon; links are underlined.
- One primary button per screen area at most. "Add" buttons are secondary; destructive actions (delete) use the danger variant.
- The focus ring is the same on every element and always uses `primary`, never the colour of the element.
- `Tag` (information) has no border; `Chip` (action) has a border and a 44px height: an information never looks clickable.
- In comparison tables, bold is reserved for extreme values, always followed by ▲ or ▼.
- Alternate row colours are used in comparison and value tables; back-office lists use plain rows separated by lines.
- A field whose label is visually hidden (toolbar, repeated rows) keeps a label read by screen readers.

## 8. CSS custom properties

```css
:root {
  --color-bg: #FAFAF7;
  --color-surface: #FFFFFF;
  --color-surface-alt: #F1F3F0;
  --color-text: #1F2A2E;
  --color-text-muted: #55626A;
  --color-primary: #2F6B5A;
  --color-primary-hover: #24564A;
  --color-on-primary: #FFFFFF;
  --color-primary-soft: #E4EFEA;
  --color-primary-strong: #24564A;
  --color-border: #D9DDD8;
  --color-border-strong: #7F8984;
  --color-error: #B42318;
  --color-error-bg: #FDECEA;
  --color-warning: #8A5A00;
  --color-warning-bg: #FDF3E1;

  --font-size-xs: 0.875rem;
  --font-size-sm: 1rem;
  --font-size-md: 1.125rem;
  --font-size-lg: 1.25rem;
  --font-size-xl: 1.5rem;
  --font-size-2xl: 1.875rem;
  --font-size-3xl: 2.25rem;

  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-5: 1.5rem;
  --space-6: 2rem;
  --space-7: 3rem;
  --space-8: 4rem;

  --radius-xs: 4px;
  --radius-sm: 6px;
  --radius-md: 12px;
  --shadow-popover: 0 4px 16px rgb(31 42 46 / 12%);
  --shadow-bar: 0 -4px 16px rgb(31 42 46 / 12%);
  --focus-ring: 0 0 0 2px var(--color-bg), 0 0 0 4px var(--color-primary);
  --target-min: 44px;
  --content-max: 1200px;
  --form-max: 1000px;
}
```
