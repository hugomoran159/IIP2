[Home](https://docs.evidence.dev/) [Reference](https://docs.evidence.dev/reference) [Markdown](https://docs.evidence.dev/reference/markdown)

# [Markdown Reference](https://docs.evidence.dev/reference/markdown\#markdown-reference)

Evidence supports most markdown syntax. Below are some of the most common markdown features. For more details, check out [Markdown Guide](https://www.markdownguide.org/cheat-sheet).

## [Text Paragraphs](https://docs.evidence.dev/reference/markdown\#text-paragraphs)

```text-sm markdown
This is a paragraph. It can be as long as you want.

Add line breaks by leaving a blank line between paragraphs.
```

## [Text Styles](https://docs.evidence.dev/reference/markdown\#text-styles)

```text-sm markdown
**Bold** text is wrapped in double asterisks
_Italic_ text is wrapped in single asterisks
~~Strikethrough~~ text is wrapped in double tildes
`Inline code` is wrapped in backticks
```

## [Lists](https://docs.evidence.dev/reference/markdown\#lists)

```text-sm markdown
- This is a unordered list
- It uses dashes
- To indicate items

1. This is an ordered list
1. It uses numbers to indicate order
1. The numbers you type don't matter, they will be automatically numbered
```

## [Headers](https://docs.evidence.dev/reference/markdown\#headers)

```text-sm markdown
# H1 Header

## H2 Header

### H3 Header

#### H4 Header

##### H5 Header

###### H6 Header
```

## [Links](https://docs.evidence.dev/reference/markdown\#links)

```text-sm markdown
[External link](https://google.com)

[Internal link](/another/page)
```

## [Images](https://docs.evidence.dev/reference/markdown\#images)

```text-sm markdown
![An online image](https://i.imgur.com/xyI27iZ.gif)

![An image stored in the project's static folder](/my-image.png)
```

#### [Storing Images and Static Files](https://docs.evidence.dev/reference/markdown\#storing-images-and-static-files)

Evidence looks for images in the `/static` folder in the root of your project. Create it if it doesn't exist.

```text-sm bash
+-- pages/
|   `-- index.md
`-- static/
    `-- my-image.png
```

## [Code Fences](https://docs.evidence.dev/reference/markdown\#code-fences)

In Evidence, most code fences execute SQL queries and display the results in a table.

````text-sm markdown
This code fence will execute a SQL query and display the results:

```sql orders
SELECT *
FROM needful_things.orders
WHERE category = 'Sinister Toys'
```
````

The exception is if you use one of the [reserved language names](https://github.com/evidence-dev/evidence/blob/main/packages/lib/preprocess/src/utils/supportedLanguages.cjs), which will render the code in a code block.

````text-sm markdown
```python
names = ["Alice", "Bob", "Charlie"]

for name in names:
    print("Hello, " + name)
```

```r
names <- c("Alice", "Bob", "Charlie")

for (name in names) {
    print(paste("Hello, ", name))
}
```
````

## [Tables](https://docs.evidence.dev/reference/markdown\#tables)

```text-sm markdown
| Column 1 | Column 2 | Column 3 |
| -------- | -------- | -------- |
| Row 1    | Row 1    | Row 1    |
| Row 2    | Row 2    | Row 2    |
```

To display data in a table, use a [Data Table](https://docs.evidence.dev/components/data/data-table) instead.

## [Blockquotes](https://docs.evidence.dev/reference/markdown\#blockquotes)

```text-sm markdown
> This is a blockquote
>
> It can span multiple lines
>
> > And can be nested
```

> This is a blockquote
>
> It can span multiple lines
>
> > And can be nested

## [Horizontal Rule](https://docs.evidence.dev/reference/markdown\#horizontal-rule)

```text-sm markdown
Below is a horizontal rule

---
```

Below is a horizontal rule

* * *

## [Frontmatter](https://docs.evidence.dev/reference/markdown\#frontmatter)

Frontmatter does not support Javascript statements at this time; and things may behave unexpectedly if wrapped in `{}`

To attach metadata (e.g. a title) to your page, you can use Frontmatter. Note that frontmatter _must_ appear as the first thing in your page; no content can come before it, or it won't be loaded properly.

Frontmatter is formatted like this:

```text-sm markdown
---
title: Evidence Docs
---
```

You can put whatever data you would like here, and it uses a [yaml syntax](https://yaml.org/), but some properties are special:

[title](https://docs.evidence.dev/reference/markdown#props-title)

Changes the name of the tab, the title displayed in the sidebar, adds a header to your page, and changes the breadcrumb for the page.

[hide\_title](https://docs.evidence.dev/reference/markdown#props-hide-title)

If true, the title will not show as a header on the page

Options:

true false

[description](https://docs.evidence.dev/reference/markdown#props-description)

Is used for search engines

[og](https://docs.evidence.dev/reference/markdown#props-og)

Changes how your link shows up when shared on things like Slack, Facebook, Twitter, Discord, etc

[og.title](https://docs.evidence.dev/reference/markdown#props-og-title)

Changes the title that appears in the embed; if this is not specified, but \`title\` is, then \`title\` is used (and vice versa)

[og.description](https://docs.evidence.dev/reference/markdown#props-og-description)

Changes the body of the embed

[og.image](https://docs.evidence.dev/reference/markdown#props-og-image)

Will appear in the embed if specified, but it is not required.

[queries](https://docs.evidence.dev/reference/markdown#props-queries)

References SQL queries stored in the /queries directory.

[sidebar](https://docs.evidence.dev/reference/markdown#props-sidebar)

Changes the visibility of the sidebar. 'show' results in a responsive sidebar, 'hide' results in a sidebar accessible via hamburger button and 'never' hides both - the sidebar and the hamburger button.

Options:

show hide never

[sidebar\_position](https://docs.evidence.dev/reference/markdown#props-sidebar-position)

Changes the position of the page in the sidebar. When used in index.md pages, changes the position of their parent in the sidebar.

Options:positive integer

[sidebar\_link](https://docs.evidence.dev/reference/markdown#props-sidebar-link)

When set to false, no link to the page appears in the sidebar. When used in index.md pages, the parent directory will still appear in the sidebar but it will not function as a link.

Options:

true false

[breadcrumb](https://docs.evidence.dev/reference/markdown#props-breadcrumb)

Specify a query that returns a column named breadcrumb. The query can use `${params.my_param}` to reference the URL parameters for the page.

E.g.
`breadcrumb: "select customer_name as breadcrumb from customers_table where customer_id = ${params.customer_id}"`

[hide\_header](https://docs.evidence.dev/reference/markdown#props-hide-header)

If true, header will not be shown on the page

Options:

true false

[hide\_toc](https://docs.evidence.dev/reference/markdown#props-hide-toc)

If true, table of contents will not be shown on the page

Options:

true false

[hide\_breadcrumbs](https://docs.evidence.dev/reference/markdown#props-hide-breadcrumbs)

If true, breadcrumbs will not be shown on the page

Options:

true false

[full\_width](https://docs.evidence.dev/reference/markdown#props-full-width)

Sets the width of the app content to the full width of the screen.

Options:

true false

[max\_width](https://docs.evidence.dev/reference/markdown#props-max-width)

Sets the width of the app content in pixels. The default layout is about 1,280 px wide.

Options:Any number

Anything outside of these values won't do anything on their own, but they will be accessible as [variables](https://docs.evidence.dev/core-concepts/syntax#expressions) on the page.

## [Partials](https://docs.evidence.dev/reference/markdown\#partials)

Partials do not support live reload, or hot module replacement. You will need to refresh the page when you change a partial.

`./pages/index.md`

```text-sm markdown
{@partial "my-first-partial.md"}

And some content specific to this page.
```

`./partials/my-first-partial.md`

```text-sm markdown
# This is my first partial

This is some content in the partial.
```

Evidence supports re-using chunks of Evidence markdown using Partials.

Partials are placed in the `./partials` folder, and can be referenced in your markdown with `{@partial "path/to/partial.md"}` (do not include the `/partial` folder in the path).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/reference/markdown/index.md)