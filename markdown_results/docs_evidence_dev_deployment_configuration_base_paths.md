[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Configuration](https://docs.evidence.dev/deployment/configuration) [Base Paths](https://docs.evidence.dev/deployment/configuration/base-paths)

# Base Paths

Evidence supports serving your app from a subdirectory. For example, you can serve your app from `https://acme.com/analytics`.

This can be useful for embedded reporting, where you want to use the root domain for your main app and serve Evidence reports from a subdirectory.

## [Configuring the Base Path](https://docs.evidence.dev/deployment/configuration/base-paths\#configuring-the-base-path)

Add the following to `evidence.config.yaml` at the project root:

```text-sm yaml
deployment:
  basePath: /my-base-path
```

**All links in your markdown files will be automatically adjusted** to include the base path.

The base path must:

- Start with a `/`
- **Not** end with a `/`
- Be a valid URL path

Your `pages/index.md` file will be served from `https://my-domain.com/my-base-path`, and other pages will be served relative to this path.

## [Configuring the Build Directory in `package.json`](https://docs.evidence.dev/deployment/configuration/base-paths\#configuring-the-build-directory-in-packagejson)

Evidence builds your app to the `build` directory, rather than to `build/my-base-path`.

To modify the build directory, set the `EVIDENCE_BUILD_DIR` environment variable in `package.json`

```text-sm json
  "build": "EVIDENCE_BUILD_DIR=./build/my-base-path evidence build"
```

This is required to use the `npm run preview` command, or else the preview will not run correctly.

## [Custom Components](https://docs.evidence.dev/deployment/configuration/base-paths\#custom-components)

[Custom components](https://docs.evidence.dev/components/custom/custom-component) links are **not automatically adjusted** to include the base path. Links should be adjusted using the `addBasePath` utility function, which adjusts relative links to include the base path.

For example:

`CustomLink.svelte`:

```text-sm svelte
<script>
  export let link;
  import { addBasePath } from '@evidence-dev/sdk/utils/svelte';
</script>

<a href={addBasePath(link)}>My Component</a>
```

## [Evidence Cloud](https://docs.evidence.dev/deployment/configuration/base-paths\#evidence-cloud)

Deploying apps with custom base paths is supported in Evidence Cloud's [Enterprise plan](https://evidence.dev/cloud).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/configuration/base-paths/index.md)