[Home](https://docs.evidence.dev/) [Plugins](https://docs.evidence.dev/plugins) [Create Component Plugin](https://docs.evidence.dev/plugins/create-component-plugin)

# Create Component Plugin

You can build a component plugin to publish your own custom components, or to make existing open source component libraries easily available for Evidence users.

Evidence Labs is deprecated and should not be used as a plugin in your Evidence app. This section of the documentation will be updated in the future.

An example component library [Evidence Labs](https://github.com/evidence-dev/labs) is available on GitHub, with a live demo of the components [here](https://labs.evidence.dev/).

## [Basic Steps](https://docs.evidence.dev/plugins/create-component-plugin\#basic-steps)

1. Clone the [Evidence Labs example repo](https://github.com/evidence-dev/labs)
2. Add your components to the `src/lib` directory in place of the existing components
3. Add pages in the `pages` directory to show your components, in place of the existing pages
4. Set up component exporting (see section below)
5. Test that your components work by running the dev server with `npm run dev` and inspecting the pages you created
6. Edit the name in `package.json` from `@evidence-dev/labs` to `your-plugin-name` and set the version to `0.0.1`
7. Publish to npm with `npm publish` (You will need to be logged in to an [npm](https://www.npmjs.com/signup) account)
8. Install your plugin by following [the steps here](https://docs.evidence.dev/plugins/component-plugins)
9. Make changes to your plugin and republish with `npm publish` \- _note that you need to bump the version number in `package.json` each time you do this_

## [Component Exporting](https://docs.evidence.dev/plugins/create-component-plugin\#component-exporting)

Plugins must "export" their components to make them available to your Evidence apps.

There are two ways to set up component exporting in your plugin:

1. [Module Exports](https://docs.evidence.dev/plugins/create-component-plugin#module-exports) (recommended)
2. [Manifest](https://docs.evidence.dev/plugins/create-component-plugin#manifest) \- this method can be used in cases when a large component library already exists

_Note that these are mutually exclusive, and the manifest takes priority._

### [Module Exports](https://docs.evidence.dev/plugins/create-component-plugin\#module-exports)

When writing a plugin from scratch, this is the preferred method.

#### [Steps](https://docs.evidence.dev/plugins/create-component-plugin\#steps)

1. Add the following to each component in your plugin to "flag" the component as something that should be imported as part of the plugin (at the top of the component's `.svelte` file)

```text-sm html
<script context="module">
    export const evidenceInclude = true;
</script>
```

2. Add an `index.js` file to the `src/lib` directory
3. Add one line to `index.js` per component in your plugin. This will export the components, making them available in Evidence:


```text-sm javascript
export {default as ComponentOne} from "./ComponentOne";
export {default as ComponentTwo} from "./ComponentTwo";
```


### [Manifest](https://docs.evidence.dev/plugins/create-component-plugin\#manifest)

If you would prefer not to flag each individual component file, another approach is to maintain an `evidence.manifest.yaml` file. The structure of the file is a single array of component names.

#### [Steps](https://docs.evidence.dev/plugins/create-component-plugin\#steps-1)

1. Add an `evidence.manifest.yaml` to your `src/lib` directory
2. Add a line to the file for each component in your plugin:


```text-sm yaml
components:
- ComponentOne
- ComponentTwo
```

3. Add an `index.js` file to the `src/lib` directory
4. Add one line to `index.js` per component in your plugin. This will export the components, making them available in Evidence:


```text-sm javascript
export {default as ComponentOne} from "./ComponentOne";
export {default as ComponentTwo} from "./ComponentTwo";
```


## [Promoting Your Plugin](https://docs.evidence.dev/plugins/create-component-plugin\#promoting-your-plugin)

If you are building a plugin for other Evidence users, [let us know in Slack](https://slack.evidence.dev/) and we can share it with the community.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/plugins/create-component-plugin/index.md)