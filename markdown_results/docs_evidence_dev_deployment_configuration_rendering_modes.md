[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Configuration](https://docs.evidence.dev/deployment/configuration) [Rendering Modes](https://docs.evidence.dev/deployment/configuration/rendering-modes)

# Rendering Modes

Evidence supports two rendering modes:

1. Static Site Generation (Default)
2. Single Page App (SPA)

## [Choosing a Rendering Mode](https://docs.evidence.dev/deployment/configuration/rendering-modes\#choosing-a-rendering-mode)

You should generally only use the SPA rendering mode if one of the following is true:

- **You have a large number of pages**, >1000+ is a good rule of thumb
- **You want to update your data frequently**, so short build times are desirable
- **Your data sources are large** (in which case you may want to combine this with Evidence's Cloud Execution Engine)

## [Comparison](https://docs.evidence.dev/deployment/configuration/rendering-modes\#comparison)

|  |  |  |
| --- | --- | --- |
| Rendering Mode | Static Site Generation | Single Page App |
| --- | --- | --- |
| Content Rendering | Pre-rendered at build time | Rendered on the client side |
| Page Generation | Each page generated ahead of time | Only one HTML file generated |
| Built Output | All pages have corresponding HTML files | Pages rendered on the fly using JavaScript |
| Build Duration | Slower due to building all pages | Fast as only one page is built |
| Performance | Fast page loads | Slower page loads |
| SEO | Rich SEO for all pages | Generic SEO for your whole app |

No Results

|  |  |  |
| --- | --- | --- |
| Rendering Mode | Static Site Generation | Single Page App |
| --- | --- | --- |
| Content Rendering | Pre-rendered at build time | Rendered on the client side |
| Page Generation | Each page generated ahead of time | Only one HTML file generated |
| Built Output | All pages have corresponding HTML files | Pages rendered on the fly using JavaScript |
| Build Duration | Slower due to building all pages | Fast as only one page is built |
| Performance | Fast page loads | Slower page loads |
| SEO | Rich SEO for all pages | Generic SEO for your whole app |

No Results

## [Enabling SPA Mode](https://docs.evidence.dev/deployment/configuration/rendering-modes\#enabling-spa-mode)

Note: To deploy an SPA mode app on Evidence Cloud, you currently need to deploy on a private site, using the Cloud Execution Engine.

SPA rendering mode is disabled by default.

To enable SPA rendering mode:

1. Update the build and preview scripts in `package.json`:

```text-sm json
"build": "VITE_EVIDENCE_SPA=true evidence build",
"preview": "VITE_EVIDENCE_SPA=true evidence preview",
```

2. Add svelte adapter-static as a dev dependency:

```text-sm bash
npm install --save-dev @sveltejs/adapter-static
```

3. Add a `svelte.config.js` file to the root of your project containing the following:

```text-sm javascript
import adapter from '@sveltejs/adapter-static';

/** @type {import("@sveltejs/kit").Config} */
export default {
    kit: {
        adapter: adapter({
            fallback: 'index.html'
        })
    },
};
```

4. If self-hosting an SPA it is important to redirect all URLs to index.html. For example in an NGINX server block you would put:

```text-sm code
root /path/to/your/project/build/;

location / {
    try_files $uri $uri/ $uri.html /index.html;
}
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/configuration/rendering-modes/index.md)