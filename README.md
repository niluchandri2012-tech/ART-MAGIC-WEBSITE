# Art Magic — Loading Section (Section 1)

A single self-contained `index.html`: no build step, no npm, no CDN, no external
fonts, no remote images. Drop it in a GitHub Pages repo root and it runs.

## Integration

The loader is an overlay with a public API. It auto-mounts once in this
standalone file; for real use, mount it above your homepage:

```js
window.ArtMagicLoader.mount({
  container: document.body,
  onComplete: () => {
    // the loader has been removed from the DOM; show the site
  }
});

// anywhere later:
window.ArtMagicLoader.destroy();
```

On success it removes itself from the DOM, restores the body styles it changed,
cancels its animation frames and timers, calls `onComplete` exactly once and
dispatches `artmagic:loader-complete` exactly once on `document`. It never
touches `window.location` or history.

Because this file is the loader only, the page is blank white after the exit —
that is intentional. Mount it over the real homepage and the honeycomb
transition reveals the page beneath.

## Where to change things

- `GEO` — wheel centre, radius, angular spacing, arc radius, blob and pointer
  geometry (design px in a 1152 x 2048 space that is uniformly scaled to fit).
- `MOTION` — tilt, selection magnification, opacity falloff.
- `TIMING` — entrance, spin, spring, hold, honeycomb, overshoot in item
  positions, and the start angle. Total is ~3.1 s.
- `HONEY` — honeycomb cell size and the DOM-node cap.

The faint rim arc is the `.am-arc` SVG in the markup. Delete that element to
remove it; nothing else depends on it.

## Reduced motion

`prefers-reduced-motion: reduce` shows the settled Baking state briefly, exits
with a short fade and completes normally.
