# Design

## Theme

Dark, single-mode. The brand identity is hazard-yellow on near-black; offering a light theme would dilute the alert-signal association. WCAG 2.2 AA on body text (>= 7:1 contrast); primary yellow as fill only with black text.

## Palette (OKLCH)

Identity-preservation: the primary yellow anchor matches the source brand exactly. The rest of the palette is composed around it for the operator/instrument register.

- `--bg`: `oklch(0.122 0.014 264)` -- near-black with the faintest cool tint, intentionally not pure black so the radial glow reads.
- `--surface`: `oklch(0.165 0.013 263)` -- bg pulled toward ink by ~10%, holds panels.
- `--surface-elevated`: `oklch(0.205 0.012 262)` -- raised cards inside panels.
- `--ink`: `oklch(0.940 0.005 250)` -- body text, ~12.4:1 vs `--bg`. Comfortably above WCAG AAA.
- `--ink-muted`: `oklch(0.780 0.008 250)` -- secondary text, 5.3:1 vs `--bg`. Above the 4.5:1 AA bar for body text, intentionally not lighter to avoid the gray-text-on-dark washed-out look.
- `--ink-subtle`: `oklch(0.620 0.010 250)` -- tertiary, captions, labels. 3.5:1 vs `--bg`. Used only for non-essential text (timestamps, helper lines).
- `--primary`: `oklch(0.918 0.182 102)` -- saturated hazard yellow (#FFE60F equivalent). Identity anchor. Used as fill only; text on it is black.
- `--primary-soft`: `oklch(0.918 0.182 102 / 0.12)` -- tinted backgrounds (badges, glow).
- `--primary-glow`: `oklch(0.918 0.182 102 / 0.35)` -- outer-glow shadow color (CTAs, phone glow).
- `--primary-dark`: `oklch(0.860 0.165 102)` -- hover state for primary fills; slightly darker, still readable with black text.
- `--accent`: `oklch(0.700 0.150 30)` -- alert red-orange, used ONLY for the live signal pulse on the hero badge (so the yellow stays reserved for action). Different hue AND lightness from primary, satisfying the 1.7 contrast rule.
- `--border`: `oklch(1 0 0 / 0.08)` -- hairline separators.
- `--border-strong`: `oklch(1 0 0 / 0.14)` -- panel borders.

## Typography

Single-family strategy (the operator voice does not need display+body contrast; one geometric sans in committed weight/size contrast is stronger than a timid pair).

- `--font-sans`: `Inter Variable, Inter, -apple-system, BlinkMacSystemFont, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", system-ui, sans-serif`. Inter is on the reflex-reject list as a default; we use it deliberately because it is a metric instrument (uniform widths, no character surprises) that fits the operator voice, NOT as a safe modern pick. For a real client-shipped version we would license a custom geometric (NB International Pro, Soehne, or a Chinese-first choice like Smiley Sans for headings + Source Han Sans for body). Note in the deliverable that the production stack should swap Inter for a licensed family before launch.
- `--font-mono`: `JetBrains Mono, "SF Mono", ui-monospace, monospace` -- used only inside the phone mockup for stat numbers and the small status pill text, not for editorial accent.

Type scale (fluid clamp):

- `--fs-xs`: 0.8125rem (13px) -- captions, labels
- `--fs-sm`: 0.9375rem (15px) -- secondary text, nav links
- `--fs-base`: 1.0625rem (17px) -- body, buttons. Larger than the 16px default; reader-friendly for non-native Chinese.
- `--fs-lg`: 1.1875rem (19px) -- section descriptions
- `--fs-xl`: 1.375rem (22px) -- card titles, metric values
- `--fs-2xl`: 1.6875rem (27px) -- phone mockup titles
- `--fs-h3`: clamp(1.875rem, 3.2vw, 2.625rem) -- section headings
- `--fs-h2`: clamp(2.25rem, 4.0vw, 3.25rem) -- pricing block title
- `--fs-h1`: clamp(2.625rem, 5.6vw, 3.75rem) -- hero title (96px ceiling respected; sits below the shouting line)

Letter-spacing: -0.04em on display headings (-0.03em on section h3, since longer lines). Never tighter than -0.04em.

Line-height: 1.65 default body, 1.45 for headings, 1.85 for long-form section descriptions. Light text on dark bg gets +0.05 above what light-mode typography would use.

text-wrap: balance on h1-h3; text-wrap: pretty on long prose blocks.

Body line length capped at 65ch (well within the 65-75ch band). The hero description caps at 480px to keep the headline column from racing ahead of the phone mockup on wide viewports.

## Spacing

8px base, fluid clamp on section padding.

- space-1 through space-12 at 4/8/12/16/24/32/48/64/96/128/160/192 px
- Section vertical padding: clamp(72px, 9vw, 120px) -- breathes on desktop, still substantial on mobile
- Container max-width: 1120px
- Side padding: clamp(24px, 5vw, 56px) -- avoids the wall-of-text look on small viewports
- Card / panel radius: 14px (small), 20px (large)
- Phone mockup radius: 36px (real phone corner radius for a modern device)
- Button radius: 999px (pill) for all CTAs -- consistent pill shape reinforces the operator/instrument voice

## Components

- Header: fixed, transparent over the hero band (translucent + 16px backdrop blur). On scroll past the hero, switches to a solid surface with stronger blur. Transition: 0.3s ease on background/border/shadow.
- Hero badge: pill with status dot. Dot uses the accent red with 2.4s pulse; never the primary yellow (yellow is reserved for action).
- Primary button: filled --primary with black text, 15/32 padding, pill radius, --primary-glow shadow that intensifies on hover. transform: scale(0.98) on :active. Magnetic displacement on mousemove (desktop fine-pointer only).
- Ghost button: 1px hairline border (--border), transparent bg. Hover: border lifts to --border-strong, bg gets 4% white tint.
- Phone mockup: 290px wide, 36px corner radius, 1px border + 24/64 box-shadow + 60px primary glow. Two stacked scenes (dashboard / DingTalk) that auto-cycle every ~7s, each with its own internal sub-animation (the DingTalk scene plays a 980ms send animation, then settles). Magnetic 3D tilt on hover (max 14deg, idle pose retained when not hovered).
- Section panel: surface bg, --border-strong border, large radius, shadow-sm. Used for the pricing block to frame a heavy data table without becoming a card-grid.
- Section label: small all-caps tracked label with a 20x2px primary bar before it. Used ONCE in features and pricing sections, NOT as a per-section reflex. The source design uses this same kicker deliberately as a single brand system; we replicate it once, not as a habit.
- Pricing card: surface-elevated bg, --border border, large radius, padding 24. Featured variant has a primary border and best-value pill badge. Cards vary in width (auto-fit) but share the same internal rhythm (name / price / daily cost / one-line note).
- Step item: numbered list (1, 2, 3, 4) for the user-flow section. The numbers are content, not scaffolding -- they describe a real sequential workflow.
- QR card: small image with explicit fallback (the source uses an external asset; we generate a deterministic placeholder SVG so the file works offline). WeChat ID rendered as plain text below.
- Footer: single line, primary-soft border-top, no columns (avoids the social-icon-row reflex).

## Motion

- Easing: cubic-bezier(0.22, 1, 0.36, 1) (ease-out-quint) for reveals; cubic-bezier(0.23, 1, 0.32, 1) for the phone tilt interpolation. No bounce. No elastic.
- Durations: 0.2s for hovers, 0.35s for state swaps, 0.45s for the phone 3D transition, 0.85s for hero entrance choreography, 0.98s for the DingTalk send animation.
- Hero entrance: badge -> title -> slogan -> actions -> metrics, each staggered by 110ms with translateY(28px) -> 0 and opacity 0 -> 1.
- Scroll reveal: IntersectionObserver at threshold 0.12, rootMargin -40px bottom. Reveals use a translateY(20px) + opacity 0 -> 1, 0.7s ease-out-quint. Group staggering via --reveal-delay set per-item (0.08s step).
- Hero parallax: bg layer translates 0 -> 36px as the band scrolls past; grid layer 0 -> 52px. Different magnitudes = atmospheric depth without obvious motion.
- Magnetic buttons: 0.14 lerp factor, max displacement ~6px on x, ~8px on y. Disabled on touch / reduced-motion.
- Phone 3D tilt: 14deg max tilt, idle pose = rotateX(-5deg) rotateY(11deg), hover lerps to pointer-relative position. Disabled on touch / reduced-motion.
- Phone scene cycle: dashboard 4.2s + dingtalk 6.8s = 11s loop. Stage height is measured and locked to the tallest panel so the layout does not jump during scene swaps.
- Reduced motion: every animation has a prefers-reduced-motion: reduce override that freezes motion to the end-state and disables the scene cycle. Reveal items are made visible immediately.

## Layout

- Hero: 1fr / 380px two-column grid, gap 48. Collapses to single column at <= 960px; phone mockup moves BELOW the copy (operator reads the headline first, then sees the demo).
- Features list: single column with alternating alignment (icon left / right) on desktop, stacks to single column on mobile. The list shape (not a card grid) avoids the identical-card-grid reflex.
- Step list: 2x2 grid on desktop, single column on mobile. Numbers carry sequence information; this is a real sequential workflow, so numbered eyebrows are content here, not scaffolding.
- Pricing: single column with two editions (mobile / desktop), each edition has a 4-column auto-fit grid of tier cards (minmax(220px, 1fr) so it does not collapse awkwardly on tablet).
- Contact: single centered column, max-width 560px, no card chrome -- the QR is the visual element.

## Responsive

- Breakpoints used: 640px (sm), 800px (md), 960px (lg). Mobile-first; the grid collapse happens at 960px because the hero two-column cannot survive narrower than that with a 290px phone.
- Hero metrics: 4 columns on desktop, 2x2 on mobile.
- Pricing tier grid: 4 columns on desktop, 2x2 on tablet, single column on narrow mobile.
- Header nav collapses links to icon-only buttons at <= 640px; the CTA pill remains.

## Imagery

Zero raster imagery. All visual content is type, layout, and the in-page phone mockup. The QR card uses an inline SVG placeholder so the file works without external assets. No stock photos -- the product is a tool, not a destination; the phone demo IS the imagery.

## Asset whitelist

- Inline SVG for the QR placeholder (deterministic, no network).
- Inline SVG for the section-label bar (small, primary-tinted rectangle).
- No web fonts loaded over the network -- falls back through system fonts. (Production should self-host Inter Variable or a licensed alternative to avoid the CDN dependency and to keep LCP tight.)
- No JS frameworks; the entire interactivity is one IIFE of ~280 lines of vanilla JS.
