# Mobile Design System & UX Standards

## 1. Visual Identity & Brand Philosophy
The design language reflects the rugged natural beauty of Northern Vietnam: pine forests, misty cloud peaks, and earthen trails, combined with a modern, high-contrast, map-first utility feel.

### Color Palette
- **Forest Moss (Primary)**: `#1E4D2B` (Brand, main buttons, verified badges)
- **Campfire Orange (Accent / CTA)**: `#E65100` (Urgent actions, booking triggers, heat markers)
- **Mist Grey (Surface / Neutral)**: `#F4F6F4` (Screen background, card containers)
- **Deep Slate (Typography & Dark Theme)**: `#111827` (Primary text, dark mode base)
- **Warning Ochre (Alerts)**: `#F59E0B` (Weather warnings, rough road conditions)
- **Danger Red (Hazard)**: `#DC2626` (Restricted military areas, flash flood alerts)

---

## 2. Typography & Vietnamese Font Support
Vietnamese diacritics (*dấu tiếng Việt*) frequently clip in standard fonts. The design system uses:
- **Font Family**: `Inter` or `Plus Jakarta Sans` with full Latin Extended glyph support.
- Minimum tap targets: `48 x 48 dp` for touch reliability while wearing gloves or in damp outdoor conditions.
- Strict WCAG AA contrast ratio (4.5:1 minimum) for sunlight readability.

---

## 3. Map-First UX Patterns
1. **Interactive Half-Sheet Bottom Drawer**:
   - The map occupies the entire background.
   - Campsite summary cards sit in a draggable bottom sheet that expands to full screen upon tapping.
2. **Filter Chips**:
   - One-tap horizontal chips: `Gần tôi` (Near me), `Có nhà vệ sinh` (Toilet available), `Ô tô vào tận nơi` (Car accessible), `Săn mây` (Cloud hunting), `Glamping`.
3. **Offline Badge & Graceful Degradation**:
   - Highlighting downloaded campsite packages with a green offline shield icon.
