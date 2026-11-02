---
title: "designerwidgets typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["BadgeToneEditor", "BadgeToneView", "BadgeToneViewFactory", "StatusBadge", "StatusBadgeIcon", "StatusBadgeRenderer"]
dependencies: []
symbols: ["BadgeToneEditor", "BadgeToneView", "BadgeToneViewFactory", "StatusBadge", "StatusBadgeIcon", "StatusBadgeRenderer"]
related: ["api.md", "getting-started.md", "index.md"]
---

# designerwidgets typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## StatusBadge

`Public Class StatusBadge Inherits Canvas`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `ConstructorCalls` | `Integer` | No | Yes | `0` | — |
| `Tone` | `String` | No | No | `"calm"` | — |

### Constructor

`Public Sub Constructor()`

No parameters.

Returns: no value.

## StatusBadgeRenderer

`Public Class StatusBadgeRenderer Implements LayoutRenderer`

### RendererId

`Public Function RendererId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### Paint

`Public Sub Paint(g As IGraphics, x As Double, y As Double, width As Double, height As Double, values As JSONItem, selected As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `width` | `Double` | `ByVal` | Required |
| `height` | `Double` | `ByVal` | Required |
| `values` | `JSONItem` | `ByVal` | Required |
| `selected` | `Boolean` | `ByVal` | Required |

Returns: no value.

### ToneFor

`Public Function ToneFor(values As JSONItem) As String`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `values` | `JSONItem` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `String` |

## StatusBadgeIcon

`Public Class StatusBadgeIcon Implements LayoutIconPainter`

Compiled palette icon: a calm-tone badge silhouette drawn with IGraphics vectors on the 24-unit glyph grid. Hosts that import this package get it through RegisterDesignerWidgets; data-only discovery uses the plugin.json icon instead.

### PaintIcon

`Public Sub PaintIcon(g As IGraphics, x As Double, y As Double, size As Double, dark As Boolean)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `g` | `IGraphics` | `ByVal` | Required |
| `x` | `Double` | `ByVal` | Required |
| `y` | `Double` | `ByVal` | Required |
| `size` | `Double` | `ByVal` | Required |
| `dark` | `Boolean` | `ByVal` | Required |

Returns: no value.

## BadgeToneEditor

`Public Class BadgeToneEditor Implements LayoutPropertyEditor`

Nonvisual editor contract: unknown expressions and cancellation remain unchanged.

### EditorId

`Public Function EditorId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### EditExpression

`Public Function EditExpression(currentExpression As String) As Optional Of String`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `Optional Of String` |

## BadgeToneViewFactory

`Public Class BadgeToneViewFactory Implements LayoutPropertyViewFactory`

### EditorId

`Public Function EditorId() As String`

No parameters.

#### Returns

| Type |
| --- |
| `String` |

### CreateView

`Public Function CreateView(currentExpression As String, host As LayoutPropertyEditorHost) As View`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

#### Returns

| Type |
| --- |
| `View` |

## BadgeToneView

`Public Class BadgeToneView Inherits View Implements LayoutReusablePropertyViewV1`

### Constructor

`Public Sub Constructor(currentExpression As String, host As LayoutPropertyEditorHost)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

Returns: no value.

### RebindProperty

`Public Sub RebindProperty(currentExpression As String, host As LayoutPropertyEditorHost)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `currentExpression` | `String` | `ByVal` | Required |
| `host` | `LayoutPropertyEditorHost` | `ByVal` | Required |

Returns: no value.

### PerformChoice

`Public Sub PerformChoice(tone As String)`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `tone` | `String` | `ByVal` | Required |

Returns: no value.

### RegisterDesignerWidgets

`Public Sub RegisterDesignerWidgets(catalog As LayoutCatalog)`

The executable host calls this explicitly, before loading source. The descriptor uses the same stable identity, source spelling, import and editor id as the package's plugin.json, so source resolves it only through `Import designerwidgets.DesignerWidgets` (a project's own StatusBadge class is never painted with this renderer) and a host that also loads the data-only descriptor keeps one palette entry. After discovery, this call only adds the compiled pieces that are still missing; if discovery runs after this call it reports the package's duplicate control symbol and loads nothing.

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `catalog` | `LayoutCatalog` | `ByVal` | Required |

Returns: no value.
