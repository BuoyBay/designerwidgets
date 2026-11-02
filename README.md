# Canvas StatusBadge + tone editor for the layout catalog

A small compiled extension demonstrating third-party LayoutKit registration of a Canvas-based StatusBadge.
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

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add designerwidgets --git https://github.com/BuoyBay/designerwidgets.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.
BPM also resolves `layoutkit`.

## Example

```basic
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

## Build and API reference

Source is in `modules/`, with native/runtime inputs where required. Use the
[package guide](docs/API.md) for backend-specific build prerequisites, ownership
rules and supported targets. Rebuilding a native backend requires that target's
compiler and SDK; sealing an archive alone does not rebuild the backend.

## Local Buoy setup

On your own machine, install Buoy and run:

```sh
buoy ai init --both
```


## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
