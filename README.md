# Art Magic — Section 2: Homepage hero

`index.html` — the hero section, self-contained: no build step, no npm, no CDN,
no external fonts, no remote images, no JavaScript at all. It works with
JavaScript disabled.

`loader.html` — the Section 1 loading screen, kept here unchanged so it isn't
lost. It is not part of this section's deliverable.

## What is on the page

- `Art Magic` — the page's single `h1`.
- `Cakes Made With Love` — tagline.
- `Freshly baked celebration cakes, made to order.` — supporting line.
- A two-tier pink-and-cream celebration cake, drawn as inline SVG.
- One call to action: `Order on WhatsApp` → `https://wa.me/919732433427`,
  opening in a new tab with `rel="noopener noreferrer"`.

Nothing else: no navigation, no footer, no second button, no extra sections.

## Cake visual

Drawn as inline SVG (the brief's first preference). No photograph, no base64
image, no remote URL. It is marked decorative (`aria-hidden`), not focusable
and not clickable. To swap in a real photograph later, replace the `<svg
class="cake">` element with an `<img>` of the same aspect ratio — the layout
reserves the space either way.

## Placing it beneath the loader

The hero renders on its own and does not know the loader exists. To combine
them: make the loader the overlay (`position: fixed; inset: 0`) and put this
`<main class="hero">` in the document beneath it. The loader's honeycomb exit
reveals the hero already painted underneath, with no blank intermediate screen.

## Where to change things

- `:root` — background, ink, and the pink used by the button.
- `.hero` — padding, gaps, and the `100svh` minimum height.
- `.hero__art` — `max-width` of the cake block.
- `.cake` — `viewBox` and the SVG gradients for the cake itself.
- `@keyframes am-rise` — the entrance motion, and the `.rise--*` delays.

Reduced motion: with `prefers-reduced-motion: reduce` no entrance animation is
applied at all, so the final state is shown immediately.
