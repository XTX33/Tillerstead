# SCSS Structure

This directory contains the modular SCSS source files for the Tillerstead website theme.

## Directory Structure

```
_sass/
├── _common.scss              # Base styles, reset, typography
├── theme.scss                # Main entry point (imports all modules)
├── components/               # UI Components
│   ├── _buttons.scss         # Button styles
│   ├── _cards.scss           # Card components
│   ├── _header.scss          # Site header (enhanced professional design)
│   ├── _footer.scss          # Site footer
│   ├── _hero.scss            # Hero section
│   └── _forms.scss           # Form elements
├── layouts/                  # Page layouts
│   ├── _page.scss            # Page layout styles
│   └── _sections.scss        # Section layouts and grids
└── utilities/                # Utility classes
    ├── _spacing.scss         # Margin, padding, gap utilities
    └── _text.scss            # Text, color, and styling utilities
```

## Building CSS

To compile SCSS to CSS:

```bash
# One-time build
npm run build:css

# Watch mode (auto-compile on changes)
npm run watch:css
```

This compiles `_sass/theme.scss` into `assets/css/theme-compiled.css`.

## Design Tokens

All design tokens (colors, spacing, typography, etc.) are defined in `src/styles/tokens.css` and imported into the SCSS files. This ensures consistency across the entire site.

## Making Changes

1. **Never edit `assets/css/theme-compiled.css` directly** - it's auto-generated
2. Edit files in `_sass/` instead
3. Run `npm run build:css` to compile
4. The compiled CSS is committed to the repository for deployment

## Header Enhancements

The header (`components/_header.scss`) includes:
- Modern gradient background with transparency
- Backdrop blur for glass effect
- Professional box shadows for elevation
- Improved color contrast with primary color accents
- Smooth hover states and transitions
- Responsive mobile navigation

## Component Organization

Each component is self-contained in its own file:
- **Buttons**: Primary, secondary, ghost, and accent button variants
- **Cards**: Card layouts, blog cards, and KPI cards
- **Header**: Site header with navigation and mobile menu
- **Footer**: Site footer with branding
- **Hero**: Hero section layouts
- **Forms**: Form inputs, labels, and validation styles

## Utility Classes

Utility classes follow a consistent naming pattern:
- Spacing: `.mt-4`, `.mb-6`, `.p-5`
- Text: `.text-primary`, `.text-center`, `.font-bold`
- Backgrounds: `.bg-gradient`, `.bg-surface-elevated`
- Borders: `.rounded-lg`, `.rounded-pill`
- Shadows: `.shadow-soft`, `.shadow-lift`

## Legacy Compatibility

The theme includes token mappings for legacy `--ts-*` variable names to maintain backward compatibility with existing styles.
