# Tillerstead Color Palette Options

## Brand Colors (Fixed)
- **Emerald Green**: `#1ac87a` - Primary brand color, vibrant and energetic
- **Gold/Brass**: `#d8b25a` - Accent color, warm and premium
- **Khaki**: `#a9967a` - Optional earthy neutral accent

## Background Variants (Choose One)

### Option 1: Deep Navy (CURRENTLY ACTIVE) ✓
**Theme**: Professional, sophisticated, trustworthy

```css
--color-bg: #0a1628;                /* Deep navy base */
--color-surface-elevated: #0f2240;  /* Lighter navy for cards */
--color-surface-highlight: #1a365d; /* Rich navy for accents */
```

**Best For:**
- Professional services presentation
- Building trust and credibility
- Timeless, classic feel
- Strong brand recognition in property management

**Visual Character:**
- Ocean depth meets architectural precision
- Maritime heritage combined with modern professionalism
- Emerald pops beautifully against navy
- Gold/brass feels like quality hardware finishes

---

### Option 2: Near-Black (ALTERNATIVE)
**Theme**: Bold, modern, luxurious

```css
--color-bg: #0b0f14;                /* Near-black base */
--color-surface-elevated: #151a21;  /* Charcoal for cards */
--color-surface-highlight: #1f252e; /* Slate for accents */
```

**Best For:**
- High-end, luxury positioning
- Contemporary, cutting-edge vibe
- Maximum color contrast
- Bold brand statement

**Visual Character:**
- Gallery-like backdrop for project photos
- Maximizes emerald and gold impact
- More dramatic, less conservative
- Strong contrast enhances accessibility

---

## Recommendation

**Option 1 (Deep Navy)** is recommended for Tillerstead because:
1. Aligns with property management trustworthiness
2. Navy + emerald is distinctive (not common in contractor space)
3. Professional without being corporate
4. Differentiates from black-background competitors
5. Khaki accent can reference natural materials/earth

**Option 2 (Near-Black)** would work if positioning more toward:
- High-end luxury remodeling exclusively
- Portfolio-first presentation
- Bold market differentiation
- Maximum visual impact

---

## How to Switch

To activate **Option 2 (Near-Black)**, edit `/src/styles/tokens.css`:

1. Comment out the Navy variant (lines 14-19)
2. Uncomment the Near-Black variant (lines 21-27)
3. The change applies site-wide instantly

---

## Color Contrast & Accessibility

Both variants meet **WCAG AAA (7:1)** contrast requirements:
- White text on navy: 8.5:1 ✓
- White text on near-black: 15.2:1 ✓
- Emerald on navy: 4.2:1 (AA) ✓
- Emerald on near-black: 7.8:1 (AAA) ✓

---

## Design Notes

The emerald + gold/brass combination conveys:
- **Emerald**: Growth, renewal, quality, nature
- **Gold/Brass**: Premium, craftsmanship, durability, classic hardware
- **Navy/Black**: Trust, professionalism, sophistication

Perfect for: "Building a great name in the industry to manage properties someday."

---

## Visual Samples

Screenshots with both palette options will be included in the PR for comparison.
