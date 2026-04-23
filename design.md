# design.md
_Source Figma: [Design System Foundation](https://www.figma.com/design/ru0GC5cCGWfFFWk5bnjBI5/%F0%9F%93%95-Design-System_Foundation?node-id=6676-527&p=f&t=TMIux3rFXfWTgoXv-0)_

## Product Design DNA (Google Stitch Style)
Design for trust, speed, and clarity:
- Functional first: every visual choice supports user intent.
- System over custom: compose from shared tokens and variants.
- Scalable consistency: icon, illustration, and badge language stay coherent across all domains (General UI, Wine, Payment, Status).

## Foundation Areas in This System
This design system currently organizes visual language into:
- WW_Color
- WW_Illustration
- General UI
- Actions
- Status
- Wine Related
- Navigation
- Social Media
- Payment

## Icon and Illustration Rules

### 1) Grid and Sizing
- Build icons on a keyline grid (2px noted in foundation).
- Core icon sizes in this system include 16, 24, 32, 36, 40, 42, 48, 50, 55, 60, and 80.
- Do not introduce non-token icon dimensions unless explicitly required by brand assets.

### 2) Variant Structure
Use explicit property-based variants (already present in Figma), for example:
- Property 1=delivery, Property 2=standard|express|other courier|premium delivery
- Noti=off|on, State=default|hover
- Type=..., Color=..., Direction=..., Tail=..., Size=...
- Platform=iOS|aOS (download app icon family)
- Language=EN|TC|SC (badge/label families)

Rule: prefer additive variant axes (Type, State, Color) rather than creating one-off duplicate components.

### 3) Domain Families
Maintain distinct but harmonized families:
- General UI: utility and product chrome icons.
- Actions: cart/fav/home/search/account interactions.
- Status: caution/progress/delivery-state indicators.
- Wine Related: tier/member/wine-specific iconography.
- Social Media: channel-specific logos and share sets.
- Payment: payment logos plus secure checkout visuals.
- Illustration: richer 42x42 semantic illustrations and workflow sequences.

### 4) State Behavior
Interactive icon components should support:
- default
- hover
- active/pressed (where relevant)
- disabled (when actionable)
- notification overlays (Noti=No|Yes|Pop where applicable)

### 5) Color Application
- Keep icon/illustration colors token-driven (no direct hex in product implementation).
- Preserve semantic intent across themes and locales (especially for status and payment confidence marks).
- For multi-color brand/payment assets, isolate as approved brand components and avoid recoloring.

## Naming Conventions
Follow existing naming patterns and normalize where possible:
- Icon/<Category>/<Name>
- Illustration/<Domain>/<Name>
- Label/<Surface>/<Type>
- Variant axes in explicit keys:
  - State=Default
  - Color=Gold
  - Language=EN

Avoid mixed-case drift like on/On, Calander/Calendar, and aOS/iOS without a migration note.

## Component Contract (Code Mapping)
Every icon/illustration component in code should expose:
- name or semantic component id (delivery, payment, wishlist, etc.)
- size
- state
- optional tone/color
- optional domain-specific axes (for example direction, language, platform)

Implementation rules:
- Map Figma variants 1:1 to component props.
- Keep visual assets in a single source package.
- For locales (EN/TC/SC), language is a variant prop, not a separate component tree.

## Accessibility Requirements
- Icons that carry meaning must not rely on color alone.
- Interactive icons need visible focus states and minimum hit area.
- Decorative icons must be marked non-semantic in code.
- Status icons should be paired with text labels in critical flows.

## Quality Checklist (Ship Gate)
- [ ] Uses existing icon/illustration family; no ad-hoc new style.
- [ ] Variant added in existing component set (not duplicated as new component).
- [ ] Size and spacing follow keyline and scale rules.
- [ ] Token-based color usage only.
- [ ] Accessibility pass for semantics and interactions.
- [ ] Localized/brand variants validated if applicable (EN/TC/SC, payment/social logos).

## Governance
When adding new icons/illustrations:
1. Confirm family and usage domain.
2. Add/extend variant axes instead of cloning.
3. Document intended usage plus anti-patterns.
4. Add code mapping in component library.
5. Review with design and frontend for naming consistency.
