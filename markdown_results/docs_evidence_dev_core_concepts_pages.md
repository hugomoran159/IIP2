[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Pages](https://docs.evidence.dev/core-concepts/pages)

# Pages

Evidence renders markdown files into web pages. When developing, the markdown file `/pages/example.md` is rendered at [localhost:3000/example](http://localhost:3000/example).

Evidence instantly reloads pages when their markdown files are edited and saved.

## [File Based Routing](https://docs.evidence.dev/core-concepts/pages\#file-based-routing)

The URL to access a page is determined by the path to the markdown file in the `/pages` directory:

- `pages/index.md` is the homepage
- `pages/weekly-sales.md` creates the `/weekly-sales` page
- `pages/marketing/attribution.md` creates the `/marketing/attribution` page

This allows you to organize your pages in a way that makes sense for your users, for example:

- by department
- by product
- by customer
- by time period

## [Templated Pages](https://docs.evidence.dev/core-concepts/pages\#templated-pages)

- `pages/customers/[customer].md` creates a page for each customer using the `[customer].md` template. See [templated pages](https://docs.evidence.dev/core-concepts/templated-pages) for details.

## [Frontmatter](https://docs.evidence.dev/core-concepts/pages\#frontmatter)

You can include page metadata, such as a title, using [frontmatter](https://docs.evidence.dev/reference/markdown#frontmatter).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/pages/index.md)