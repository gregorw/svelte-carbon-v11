# Svelte with @carbon/styles

Button uses `@carbon/styles/scss/components/button` as suggested in https://github.com/carbon-design-system/carbon-components-svelte/pull/1496#issuecomment-1372388427.

The idea is to make it easier for developers to consume and use the individual components including styles. This draft looks promising to me.

At the same time, I believe it is required to load some global resets and styles anyways. Also, I’m not entirely sure how configuration works like this, e.g. `$use-flexbox-grid`, `$prefix`, …

As far as I can tell a global import will be required anyways. Total bundle sizes of full `@carbon/styles` are below:

```
 68K bundle.css
4.9K bundle.js
 86K bundle.js.map
```

Build duration is ~10s.

When including styles within the components, some warnings may come up like this:

```
Plugin svelte: Unused CSS selector ".cds--btn-set--stacked .cds--btn.cds--btn--disabled:first-of-type"
```

Since this is a Svelte warning it won’t be shown on a global Scss import.

I wonder what the benefit of a per-component import really is. It seems to me that handing down global configuration into each component and dealing with a number of warnings could be cumbersome, but it’s certainly worth trying. I may also be missing something since I have limited expericens with Dart Sass.



## Limitation

IBM Plex font is not working in this draft.
