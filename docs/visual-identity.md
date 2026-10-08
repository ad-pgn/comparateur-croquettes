# Visual identity

> Status: validated during the design phase (issue #9).
> These values are the single source of truth for the Figma variables and the CSS custom properties of the web application.

## 1. Principles

- **Sober and calm**: one brand colour (sage), neutral greys, generous white space.
- **Neutral comparison (RG-12)**: no green/red or "good/bad" colour coding on product values. Differences in the comparator are highlighted with neutral means (bold text, outline, icon). Red is reserved for form errors.
- **Accessible (RGAA)**: every text colour reaches a contrast ratio of at least 4.5:1 on its background; interactive component boundaries (input borders, focus indicator) reach at least 3:1. All ratios below were calculated, not estimated.
- **Light theme only** in the MVP (dark theme: possible future evolution).
- **Eco-design**: one self-hosted font, two weights, no decorative images.

## 2. Colours

### Palette

| Token | Value | Use |
|---|---|---|
| `--color-bg` | `#FAFAF7` | Page background |
| `--color-surface` | `#FFFFFF` | Cards, tables, form fields |
| `--color-surface-alt` | `#F1F3F0` | Alternate rows, secondary areas |
| `--color-text` | `#1F2A2E` | Main text, headings |
| `--color-text-muted` | `#55626A` | Secondary text, metadata (dates, sources) |
| `--color-primary` | `#2F6B5A` | Primary buttons, links, focus indicator |
| `--color-primary-hover` | `#24564A` | Hover and active state of primary elements |
| `--color-on-primary` | `#FFFFFF` | Text on primary background |
| `--color-primary-soft` | `#E4EFEA` | Tags, selected filters, light highlights |
| `--color-primary-strong` | `#24564A` | Text on `--color-primary-soft` |
| `--color-border` | `#D9DDD8` | Decorative separators only |
| `--color-border-strong` | `#7F8984` | Form field borders, interactive boundaries |
| `--color-error` | `#B42318` | Form error text and borders |
| `--color-error-bg` | `#FDECEA` | Error message background |
| `--color-warning` | `#8A5A00` | Warning text (e.g. outdated price, RG-06) |
| `--color-warning-bg` | `#FDF3E1` | Warning message background |

Success messages (e.g. "Comparison saved") use `--color-primary-strong` on `--color-primary-soft`.

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

### Rules of use

- Colour is never the only way to convey information: errors also have a text message and an icon; links are underlined.
- One primary button per screen area at most; other actions use secondary (outlined) buttons.
- In the comparator, extreme values are shown in bold with a neutral marker, never coloured.

## 3. Typography

**Font: Source Sans 3** (SIL Open Font License), self-hosted with `next/font/google`: visitors' browsers never contact Google servers.
Fallback: `system-ui, -apple-system, "Segoe UI", Roboto, sans-serif`.

Reasons: humanist and warm while serious; very readable in tables; tabular figures available.

| Token | Size | Line height | Weight | Use |
|---|---|---|---|---|
| `--font-size-xs` | 0.875rem (14px) | 1.4 | 400 | Captions, metadata |
| `--font-size-sm` | 1rem (16px) | 1.5 | 400 | Body text (minimum size for body text) |
| `--font-size-md` | 1.125rem (18px) | 1.5 | 400 | Lead text |
| `--font-size-lg` | 1.25rem (20px) | 1.4 | 600 | Card titles, h4 |
| `--font-size-xl` | 1.5rem (24px) | 1.3 | 600 | h3 |
| `--font-size-2xl` | 1.875rem (30px) | 1.25 | 600 | h2 |
| `--font-size-3xl` | 2.25rem (36px) | 1.2 | 600 | h1 (1.75rem on mobile) |

- Two weights only: 400 (regular) and 600 (semibold).
- Sizes in `rem`: text follows the browser font size set by the user.
- Numbers in tables and prices use **tabular figures** (`font-variant-numeric: tabular-nums`) so that values align in columns.

## 4. Spacing, sizes and layout

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
| `--radius-sm` | 6px | Buttons, fields, tags |
| `--radius-md` | 12px | Cards, dialogs |
| `--shadow-popover` | `0 4px 16px rgb(31 42 46 / 12%)` | Dropdowns and dialogs only |
| `--focus-ring` | `2px solid var(--color-primary)`, offset 2px | Keyboard focus (`:focus-visible`) |
| `--target-min` | 44px | Minimum size of touch targets |
| `--content-max` | 1200px | Maximum content width |

Breakpoints (mobile first): `600px` (large phones), `900px` (tablets), `1200px` (desktop).

## 5. Base components

Built once, reused everywhere (public site and back office):

| Component | Variants and states |
|---|---|
| Button | Primary, secondary (outlined); default, hover, focus, active, loading |
| Text field | Default, focus, error (message + icon), with help text |
| Select, checkbox, radio | Default, focus, checked, error |
| Tag / filter chip | Default, selected, removable |
| Product card | Name, brand, range, lowest price per kg with date, add to comparison |
| Data table | Header, rows, alternate rows, tabular figures, horizontal scroll on mobile |
| Alert | Error, warning, success, information |
| Dialog | Confirmation (native `<dialog>` element) |
| Pagination | Previous, page numbers, next |
| Header and footer | Logo, navigation, account access; legal links, data sources attribution |

## 6. CSS custom properties

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

  --radius-sm: 6px;
  --radius-md: 12px;
  --shadow-popover: 0 4px 16px rgb(31 42 46 / 12%);
  --target-min: 44px;
  --content-max: 1200px;
}
```
