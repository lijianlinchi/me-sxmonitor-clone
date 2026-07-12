# Product

## Register

brand

## Platform

web


## Users

A niche audience of **power resellers and sourcing operators** on second-hand marketplaces (Xianyu, Goofish, Zhuanzhuan) who treat deal-sourcing as a competitive game. They run side gigs or full businesses that hinge on catching fresh listings within seconds of publication, filtering by price tiers, and snapping deals before slower competitors. Their context is split between a phone (alert + tap-to-act in real time) and a desktop client (always-on, multi-account, automation-heavy). Time-to-notification is the product. Missing a listing is lost margin.

Secondary audience: occasional individual resellers who find the tool through community referrals and want to graduate from manual browsing.

## Product Purpose

A real-time new-listing monitor for second-hand marketplaces, with phone-side alert/control and desktop-side always-on automation. Success means a user catches a desirable listing before any competitor sees it, executes a buy/lock order from their phone within the alert window, and never has to keep a browser open manually.

## Positioning

The fastest real-time monitor for second-hand marketplaces, with the only mobile-first control surface in the category: alert, decide, and act from the lock screen, while the desktop client keeps the watch running unattended.

## Conversion & proof

- Primary CTA: **Get activation code** (links to a WeChat contact section; the workflow is WeChat-driven in this market, not email).
- Secondary CTA: **View desktop edition** (anchors visitors who already know they need the heavier edition).
- The line a visitor remembers after 10 seconds: *Catch the listing before anyone else sees it.*
- Belief ladder (in order, before the primary CTA):
  1. The tool actually polls at the speed it claims (3-second cadence is the headline proof).
  2. It works on the device they already carry (phone demo in the hero).
  3. It pushes to a tool they already use (DingTalk demo in the cycling scene).
  4. The pricing is fair for the value (transparent mobile/desktop split with daily cost math).
  5. Contact and onboarding is low-friction (WeChat QR, not a sales call).
- Proof on hand: the in-hero phone demo *is* the proof. A live cycling mock of the dashboard and DingTalk push. No fabricated testimonials, no fake logo wall.

## Brand Personality

**Sharp. Electric. Pragmatic.** Three words, in that order.

Sharp because the product wins by milliseconds and the brand voice should feel like a precision instrument, not a friendly helper. Electric because the primary color (a saturated hazard yellow on near-black) reads as alert / live signal. The brand literally looks like a notification. Pragmatic because the audience is operators, not dreamers; they want to know what it does, what it costs, and how to start.

Tone: terse, declarative, no marketing fluff. Copy leads with the metric ("3-second", "fastest", "snap"), not adjectives.

## Anti-references

- Generic SaaS landing pages with hero-metric templates (big number + small label + supporting stats). This product *does* have metrics, but they live inside a phone demo, not as floating stat tiles around a stock illustration.
- Cream/sand/warm-neutral palette pages. The saturated-hazard-yellow identity is the opposite of safe-warm.
- "Friendly AI assistant" personality. Wrong audience, wrong register. The product is a tool for operators, not a coach.
- Marketing pages that bury the pricing. Operators bounce.
- Decorative CSS art / bokeh orbs as primary decoration. There is one radial glow in the hero, and it is functional (frames the phone), not atmosphere.

## Accessibility & Inclusion

- WCAG 2.2 AA target. Body text on near-black bg must hit 7:1 (we use near-white #E8EAED, comfortably above threshold).
- Primary yellow appears only as fill with black text. That pairing is the WCAG-cleared exception. Yellow never appears as body text on dark bg.
- Reduced-motion media query is required: phone scene auto-cycle, 3D tilt, parallax, and magnetic buttons all disable to a static, fully visible default.
- All interactive controls reachable by keyboard; visible focus rings on buttons and links.
- Tap targets >= 44x44 CSS px on mobile per HIG/Material guidelines.
- Color is never the sole signal: pricing tiers carry a "best value" text badge in addition to the yellow accent; status dots carry labels.

## Design Principles

1. **Show the product, not the marketing.** The hero's phone mockup is a live demonstration of the actual surface. Imagery and metrics sit inside the demo, not around it.
2. **Hazard-yellow does identity work, not decoration.** Yellow appears only where live signal / action / pricing lives. The rest is near-black ink.
3. **Operator voice, not consumer voice.** Copy reads like a tool description, not a benefit pitch. Numbers beat adjectives.
4. **Mobile-first demo, desktop-second edition.** The phone is the hero because that is where the user acts; desktop is positioned as the heavier automation layer, not the primary surface.
5. **One radial glow, one grid, one phone.** Restraint in atmospheric decoration. Every visual element earns its place by carrying information.