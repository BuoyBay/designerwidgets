---
title: "DesignerWidgets getting started"
summary: "Register the compiled extension."
category: "Guides"
order: 10
keywords: ["designer", "status badge", "property editor", "palette"]
related: ["index.md", "api.md", "typed-api.md"]
---

# DesignerWidgets getting started

Place the sealed `designerwidgets`, `layoutkit`, and `editorkit` archives in the consumer project’s `packages/` directory. Import `designerwidgets` for its entry module and `layoutkit.LayoutCatalog` for the catalog types. This complete example registers a descriptor and inspects its default width without opening a native window or constructing the badge. The descriptor identity is `designerwidgets.StatusBadge`; layout source spells the control `StatusBadge` and must `Import designerwidgets.DesignerWidgets` for the designer to resolve it.

When combining data-only discovery with compiled registration, call `LayoutDiscovery.DiscoverDirectory` or `LoadIndex` first, then `RegisterDesignerWidgets(catalog)`, then load the layout snapshot. Discovery after compiled registration rejects the duplicate control symbol.

For an editing host, pass the populated catalog to the LayoutCanvas editor before loading a layout snapshot. After mutating a live catalog, ask the editor to refresh its palette.

The reusable `BadgeToneView` replaces its current expression and commit host on `RebindProperty`. Hosts from an older snapshot must stay expired; the View must not retain them as active callbacks. Unknown source expressions remain source text rather than becoming an arbitrary native choice.

```buoy
Import designerwidgets
Import layoutkit.LayoutCatalog

Sub Main()
    Dim catalog As New LayoutCatalog()
    catalog.RegisterBuiltinControls()
    RegisterDesignerWidgets(catalog)
    Dim badge As LayoutControlDescriptor = catalog.Find("designerwidgets.StatusBadge")
    If badge <> Nil Then Print badge.DefaultWidth
End Sub
```

The example checks compiled registration only. Run the repository’s LayoutKit GUI tests and designer demo to exercise native painting, reused property Views, version rejection, and source preservation. A compiler check does not establish interactive rendering on every OS.

## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
