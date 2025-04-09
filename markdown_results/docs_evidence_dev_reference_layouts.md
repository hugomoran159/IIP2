[Home](https://docs.evidence.dev/) [Reference](https://docs.evidence.dev/reference) [Layouts](https://docs.evidence.dev/reference/layouts)

# Layouts

Customize the layout of your app by overwriting or modifying the default layout.

## [Custom Layout](https://docs.evidence.dev/reference/layouts\#custom-layout)

Evidence will use any `+layout.svelte` file in the `/pages` directory to override the default layout.

**Creating a Custom Layout**

The recommended approach is to copy and edit the default layout file. You can do this with the `Add Custom Layout` command in VS Code or with the CLI command below:

```text-sm bash
cp .evidence/template/src/pages/+layout.svelte pages
```

This file can also be found in the [Evidence GitHub repo](https://github.com/evidence-dev/evidence/blob/main/sites/example-project/src/pages/+layout.svelte).

You can customize the `EvidenceDefaultLayout` with the options below, or replace the contents of the file with an entirely new layout. If you include a `+layout.svelte` file in a directory, markdown files in that directory (and its subdirectories) will use this layout file instead of the default layout.

You can also add your own HTML elements to the default page layout.

## [Examples](https://docs.evidence.dev/reference/layouts\#examples)

### [Hide sidebar on all pages](https://docs.evidence.dev/reference/layouts\#hide-sidebar-on-all-pages)

```text-sm html
<EvidenceDefaultLayout {data} hideSidebar=true >
	<slot slot="content" />
</EvidenceDefaultLayout>
```

### [Add a custom logo](https://docs.evidence.dev/reference/layouts\#add-a-custom-logo)

With a logo file in `./static/my-logo.png`.

```text-sm html
<EvidenceDefaultLayout {data} logo="/my-logo.png" >
	<slot slot="content" />
</EvidenceDefaultLayout>
```

If you want to use a different logo in light and dark mode, use the `lightLogo` and `darkLogo` props instead of `logo`.

### [Add a custom favicon](https://docs.evidence.dev/reference/layouts\#add-a-custom-favicon)

To add your own favicon image, create a `static` folder in the root of your project and include images to override the below images loaded by Evidence. Please note that you will need to include all of these with identical names, as different browsers use different images:

- apple-touch-icon.png
- favicon.ico
- icon-192.png
- icon-512.png
- icon.svg

### [Add a custom browser tab title](https://docs.evidence.dev/reference/layouts\#add-a-custom-browser-tab-title)

The browser tab title is controlled via the frontmatter `title` option:

```text-sm markdown
---
title: My New Page Title
---
```

## [Options](https://docs.evidence.dev/reference/layouts\#options)

The `EvidenceDefaultLayout` component includes a number of features on every page that can be removed or customized via props

### [Page Settings](https://docs.evidence.dev/reference/layouts\#page-settings)

[title](https://docs.evidence.dev/reference/layouts#props-title)

App title that will replace the Evidence Logo.

Options:Any string

[logo](https://docs.evidence.dev/reference/layouts#props-logo)

Link to an image which will replace the Evidence logo. This will also override any app title in the header. If the image is in your project's static directory, the link should be relative to the static directory.

Options:/logo.png

[lightLogo](https://docs.evidence.dev/reference/layouts#props-lightLogo)

Link to an image which will replace the Evidence logo in light mode. This will also override any app title in the header. If the image is in your project's static directory, the link should be relative to the static directory.

Options:/lightLogo.png

[darkLogo](https://docs.evidence.dev/reference/layouts#props-darkLogo)

Link to an image which will replace the Evidence logo in dark mode. This will also override any app title in the header. If the image is in your project's static directory, the link should be relative to the static directory.

Options:/darkLogo.png

[homePageName](https://docs.evidence.dev/reference/layouts#props-homePageName)

Name of the home page in the sidebar.

Options:Any stringDefault:Home

[fullWidth](https://docs.evidence.dev/reference/layouts#props-fullWidth)

Sets the width of the app content to the full width of the screen.

Options:

true false

Default:false

[maxWidth](https://docs.evidence.dev/reference/layouts#props-maxWidth)

Sets the width of the app content in pixels. The default layout is about 1,280 px wide.

Options:Any number

[builtWithEvidence](https://docs.evidence.dev/reference/layouts#props-builtWithEvidence)

Display a subtle link to the Evidence website at the bottom of the sidebar.

Options:

true false

Default:false

### [Hide Elements](https://docs.evidence.dev/reference/layouts\#hide-elements)

[neverShowQueries](https://docs.evidence.dev/reference/layouts#props-neverShowQueries)

Removes the option to show queries when the app is deployed. Has no effect in development.

Options:

true false

Default:false

[hideSidebar](https://docs.evidence.dev/reference/layouts#props-hideSidebar)

Hides the sidebar navigation

Options:

true false

Default:false

[sidebarDepth](https://docs.evidence.dev/reference/layouts#props-sidebarDepth)

Sets the depth of pages that will be shown in the sidebar. Reduce to 2 to hide third level pages.

Options:

2 3

Default:3

[hideHeader](https://docs.evidence.dev/reference/layouts#props-hideHeader)

Hides the page header

Options:

true false

Default:false

[hideBreadcrumbs](https://docs.evidence.dev/reference/layouts#props-hideBreadcrumbs)

Hides the breadcrumbs which appear at the top of the page

Options:

true false

Default:false

[hideTOC](https://docs.evidence.dev/reference/layouts#props-hideTOC)

Hides the table of contents (on-page links at top right of page)

Options:

true false

Default:false

### [Social Links & Search](https://docs.evidence.dev/reference/layouts\#social-links--search)

[githubRepo](https://docs.evidence.dev/reference/layouts#props-githubRepo)

Link to a Github Repo which will appear in the header using the Github Logo

Default:https://github.com/evidence-dev/evidence

[xProfile](https://docs.evidence.dev/reference/layouts#props-xProfile)

Link to an X (Twitter) profile which will appear in the header using the X Logo

Default:https://twitter.com/evidence\_dev

[blueskyProfile](https://docs.evidence.dev/reference/layouts#props-blueskyProfile)

Link to a Bluesky profile which will appear in the header using the Bluesky Logo

Default:https://bsky.app/profile/evidence.dev

[slackCommunity](https://docs.evidence.dev/reference/layouts#props-slackCommunity)

Link to a slack community which will appear in the header using the slack Logo

Default:https://slack.evidence.dev

[algolia](https://docs.evidence.dev/reference/layouts#props-algolia)

Object containing Algolia docsearch credentials

Options:{{appId: 'xxx', apiKey: 'xxx', indexName: 'xxx'}}

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/reference/layouts/index.md)