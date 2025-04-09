[Home](https://docs.evidence.dev/) [Plugins](https://docs.evidence.dev/plugins) [Data Source Plugins](https://docs.evidence.dev/plugins/source-plugins)

# Data Source Plugins

Evidence includes a plugin system which can be used to add components and data sources to your app.

Source plugins enable you to add new data source types to your app. Once you have installed and registered a source plugin, you will be able to configure any associated connection settings in the settings UI.

To use a plugin, you need to **install** and **register** it in your project.

## [Installing Source Plugins](https://docs.evidence.dev/plugins/source-plugins\#installing-source-plugins)

```text-sm bash
npm install @cool-new-db/evidence-source-plugin
```

## [Registering Source Plugins](https://docs.evidence.dev/plugins/source-plugins\#registering-source-plugins)

Once the plugin is installed, add it to `evidence.config.yaml` to register it in your project.

```text-sm yaml
plugins:
    components:
        @evidence-dev/core-components: {}
    datasources:
        @cool-new-db/evidence-source-plugin
```

## [Configuring Source Plugins](https://docs.evidence.dev/plugins/source-plugins\#configuring-source-plugins)

Restart the development server after installing and registering the plugin, then visit `localhost:3000/settings`.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/plugins/source-plugins/index.md)