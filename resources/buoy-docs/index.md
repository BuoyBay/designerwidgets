---
title: "DesignerWidgets"
summary: "A packaged status badge demonstrating layout descriptors, renderers, and reusable native property editors."
category: "Overview"
order: 0
keywords: ["designer", "status badge", "property editor", "palette"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# DesignerWidgets

DesignerWidgets is a small example extension for LayoutKit and LayoutCanvas. It supplies a runtime `StatusBadge Inherits Canvas`, a design-time renderer, a nonvisual Tone editor, and a reusable native editor View. The badge uses the recommended `calm` and `alert` tones.

There are two integration paths. A trusted compiled host imports this package and calls `RegisterDesignerWidgets(catalog)` explicitly. A data-only host can discover the packaged `resources/buoy-designer/plugin.json` descriptor through the shipped designer discovery helper. Descriptor discovery paints a declarative preview and supplies choice metadata without instantiating runtime controls or executing package callbacks.

## Choose the integration path

Use compiled registration to demonstrate native editor factories and the renderer interface. Use descriptor discovery when the host should inspect installed package metadata without executing extensions. Register built-in controls once before adding extensions. The package requires LayoutKit and EditorKit; a full editing surface also needs LayoutCanvas.

Source inspection does not run a `StatusBadge` constructor. `StatusBadge.ConstructorCalls` exists to help demonstrate that separation in tests.

## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
