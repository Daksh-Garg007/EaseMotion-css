# Aurora Glow Tabs

**Issue:** #73554 — CSS Tab: Aurora Glow Variation #301
**Track:** Standard (HTML/CSS) — `submissions/examples/`
**Author suffix:** `-dg`

## What does this do?

A pure CSS, accessible segmented tab control where the active tab is highlighted by a soft, animated aurora-style gradient glow that slides beneath the selected label — no JavaScript required.

## How is it used?

The pattern uses hidden radio inputs + `<label>` elements for tab switching, so it works with just HTML and CSS:

```html
<div class="aurora-tabs" role="tablist" aria-label="Aurora Glow Tabs Demo">

  <input type="radio" name="aurora-tabs-dg" id="tab-1-dg" class="aurora-tabs__input" checked>
  <input type="radio" name="aurora-tabs-dg" id="tab-2-dg" class="aurora-tabs__input">
  <input type="radio" name="aurora-tabs-dg" id="tab-3-dg" class="aurora-tabs__input">

  <div class="aurora-tabs__list">
    <label for="tab-1-dg" class="aurora-tabs__tab" role="tab" aria-selected="true">Overview</label>
    <label for="tab-2-dg" class="aurora-tabs__tab" role="tab" aria-selected="false">Features</label>
    <label for="tab-3-dg" class="aurora-tabs__tab" role="tab" aria-selected="false">Pricing</label>
    <div class="aurora-tabs__glow" aria-hidden="true"></div>
  </div>

  <section class="aurora-tabs__panel" id="panel-1-dg" role="tabpanel">...</section>
  <section class="aurora-tabs__panel" id="panel-2-dg" role="tabpanel">...</section>
  <section class="aurora-tabs__panel" id="panel-3-dg" role="tabpanel">...</section>

</div>
```

To add more tabs, add another radio input, label, panel, and update the `--aurora-tab-count` custom property and the `:checked ~` translateX rules for the new index.

## Why is it useful?

- **Pure CSS, zero dependencies** — fits EaseMotion's "no JS required" philosophy for interactive-feeling components.
- **Hardware accelerated** — only `transform` and `opacity`/`background-position` are animated, keeping it smooth on low-power devices.
- **Dark mode compatible** — all colors are driven by CSS custom properties and swapped automatically via `prefers-color-scheme`.
- **Accessible** — real `role="tablist"`/`role="tab"`/`role="tabpanel"` semantics, keyboard-focusable labels with a visible focus ring, and an `aurora-tabs__glow` element marked `aria-hidden` since it's purely decorative.
- **Respects user preferences** — all animation and transition is disabled under `prefers-reduced-motion: reduce`.
- **Responsive** — stacks into a vertical segmented control on narrow viewports instead of overflowing.

## Notes for the maintainer

- Raw class names use the `aurora-tabs__*` prefix per contribution guidelines (no `ease-` prefixing done on my end — happy to have this standardized on integration).
- The `-dg` suffix is appended to all IDs/`name` attributes per the unique-identifier naming rule to avoid collisions with parallel submissions for the same issue.
