# DesignerWidgets example package

A small compiled extension demonstrating third-party LayoutKit registration.
Install `designerwidgets` with `layoutkit` and `editorkit`, import
`designerwidgets`, then call `RegisterDesignerWidgets(catalog)` explicitly in the
host before loading its source document.

The example registers a `designerwidgets.StatusBadge` control descriptor (source
spelling `StatusBadge`, resolved only in layouts that
`Import designerwidgets.DesignerWidgets`), a design-time renderer, `Tone`
property metadata, and a native Calm/Alert property editor
(`designerwidgets.StatusBadge.Tone`). The identity and editor id match
`plugin.json`, so a host that also loads the data-only descriptor keeps one
palette entry; calling `RegisterDesignerWidgets` again only adds missing pieces.
When combining both paths, discover the data-only descriptor first, call
`RegisterDesignerWidgets(catalog)` second, then load the layout source. Discovery
after compiled registration rejects the duplicate control symbol.
Registration and source inspection do not instantiate the runtime `StatusBadge` control.
Unknown expressions remain source text; the property editor submits changes
through the host's version-checked edit path.

It also shows how a package supplies its own palette icon:

- **Compiled:** `RegisterDesignerWidgets` calls
  `catalog.RegisterIcon("designerwidgets.StatusBadge", New StatusBadgeIcon())`. `StatusBadgeIcon`
  implements `LayoutIconPainter` and draws IGraphics vectors with light and dark
  variants.
- **Data only:** `resources/buoy-designer/plugin.json` declares `"category"`,
  `"description"`, a declarative `"icon"` recipe (24-unit grid, `darkColor` per
  step) and an `"iconImage"` (`icons/status-badge.png`). Discovery embeds the
  image in its index, prefers it, and falls back to the recipe and then to the
  generic package glyph. Nothing in the package is executed.

See [the demo](https://github.com/BuoyBay/layoutkit/blob/main/examples/layout_designer_demo.bui) and the
[LayoutKit catalog](https://github.com/BuoyBay/layoutkit/blob/main/docs/API.md) for the extension contracts.
This package is an example, not an automatically discovered plugin registry.
