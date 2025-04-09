[Home](https://docs.evidence.dev/) [Plugins](https://docs.evidence.dev/plugins) [Component Plugins](https://docs.evidence.dev/plugins/component-plugins)

# Component Plugins

Evidence includes a plugin system which can be used to add components and data sources to your app.

All Evidence projects include the Evidence `core-components` plugin by default. `core-components` has everything you need to build most use cases.

Component plugins are Svelte component packages which include one or more additional components which you can use in your markdown. Once you have installed and registered a component plugin, the included components will be available to use in your markdown files.

To use a plugin, you need to **install** and **register** it in your project.

## [Installing Component Plugins](https://docs.evidence.dev/plugins/component-plugins\#installing-component-plugins)

```text-sm bash
npm install @acme/charting
```

## [Registering Component Plugins](https://docs.evidence.dev/plugins/component-plugins\#registering-component-plugins)

Once the plugin is installed, add it to `evidence.config.yaml` to register it in your project.

```text-sm yaml
plugins:
    components:
        @evidence-dev/core-components: {}
        @acme/charting: {}
```

### [Component Aliases](https://docs.evidence.dev/plugins/component-plugins\#component-aliases)

If a plugin provides a component that you want to reference with another name, you can set up `aliases` when registering the component.

In this example, the `@acme/charting` plugin provides some component `LongNameForAChart`. After setting up `aliases`, it will be made available in the Evidence markdown as `AcmeChart`

```text-sm yaml
components:
    @acme/charting:
        aliases:
            LongNameForAChart: AcmeChart
```

### [Component Overrides](https://docs.evidence.dev/plugins/component-plugins\#component-overrides)

Component plugins have the ability to override components from other plugins (e.g. you want to replace the built-in `LineChart` with a chart from a plugin).

Overrides are specified in an `overrides` list. In the example below, Evidence's built-in `LineChart` will be overridden by the `LineChart` component from the `@acme/charting` plugin:

```text-sm yaml
components:
    @evidence-dev/core-components: {}
    @acme/charting:
        overrides:
            - LineChart
```

If you want to replace `LineChart` with a component named `CustomLineChart`, apply an alias to `CustomLineChart` first:

```text-sm yaml
components:
    @evidence-dev/core-components: {}
    @acme/charting:
        aliases:
            CustomLineChart: LineChart # Rename CustomLineChart
        overrides:
            - LineChart # Override LineChart with the now renamed CustomLineChart
```

### [(Advanced) Using generic Svelte component libraries](https://docs.evidence.dev/plugins/component-plugins\#advanced-using-generic-svelte-component-libraries)

If you want to use a Svelte component library that is _not_ an Evidence component plugin, you can use the `provides` field to
manually document the components that the library provides.

```text-sm yaml
components:
  @evidence-dev/core-components: {}
  carbon-components-svelte:
    provides:
      - Button
      - CodeSnippet
```

The components provided **must** be named exports, e.g. `import {ComponentName} from 'package';`, _not_ `import ComponentName from 'package/ComponentName.svelte;`.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/plugins/component-plugins/index.md)