---
title: "DesignerWidgets API"
summary: "Public APIs and lifecycle contracts for DesignerWidgets."
category: "Reference"
order: 20
keywords: ["designer", "status badge", "property editor", "palette"]
symbols: ["RegisterDesignerWidgets", "StatusBadge", "StatusBadge.Tone", "StatusBadge.ConstructorCalls", "StatusBadgeRenderer", "BadgeToneEditor", "BadgeToneViewFactory", "BadgeToneView", "BadgeToneView.RebindProperty", "BadgeToneView.PerformChoice"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# DesignerWidgets API

## Runtime control

| Symbol | Behavior |
| --- | --- |
| `StatusBadge` | Canvas subclass with a default control size of 180 by 36. |
| `Tone As String` | Runtime tone value; use `calm` or `alert` for the two designed appearances. |
| `ConstructorCalls` | Shared construction counter used by isolation tests. |

## Compiled design integration

| Symbol | Behavior |
| --- | --- |
| `RegisterDesignerWidgets(catalog)` | Registers the control descriptor, renderer, nonvisual editor, and native editor factory. |
| `StatusBadgeRenderer` | Implements `LayoutRenderer`; paints through `IGraphics` from descriptor values. |
| `BadgeToneEditor` | Implements `LayoutPropertyEditor`; an expression-oriented fallback. |
| `BadgeToneViewFactory` | Implements `LayoutPropertyViewFactory` and creates a native View. |
| `BadgeToneView` | Implements `LayoutReusablePropertyViewV1`; contains Calm/Alert choices. |
| `RebindProperty(currentExpression, host)` | Replaces displayed state and the revision-bound callback host. |
| `PerformChoice(tone)` | Submits the selected expression through the current commit host. |

The compiled descriptor’s `Tone` property has kind `string`, a quoted default expression, and quoted string choices. The runtime property and the source expression are different representations. Catalog registration alone does not open the runtime control.

## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)

[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
