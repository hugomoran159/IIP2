[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Link](https://docs.evidence.dev/components/ui/link)

# Link

Note that you can also use [markdown syntax for links](https://docs.evidence.dev/reference/markdown#links). This component is useful when you need to customize the behavior or styling of the link (e.g., opening in new tab vs. current tab)

Use the `Link` component to add styled and accessible links to your markdown pages. This component allows you to control the destination URL, link text, and whether it opens in a new tab.

## [Default usage](https://docs.evidence.dev/components/ui/link\#default-usage)

preview

code

[Visit Example](https://github.com/evidence-dev/evidence)

```text-sm markdown
<Link
    url="https://github.com/evidence-dev/evidence"
    label="Visit Example"
/>
```

### [Open in a new tab](https://docs.evidence.dev/components/ui/link\#open-in-a-new-tab)

preview

code

[Visit Example](https://github.com/evidence-dev/evidence)

```text-sm markdown
<Link
    url="https://github.com/evidence-dev/evidence"
    label="Visit Example"
    newTab=true
/>
```

## [Options](https://docs.evidence.dev/components/ui/link\#options)

[url](https://docs.evidence.dev/components/ui/link#props-url)

Required

The destination URL of the link. It can accept either a full external link (e.g. `https://google.com`) or link to another page within your evidence app (e.g. `/sales/performance`).

Options:string

[label](https://docs.evidence.dev/components/ui/link#props-label)

The text displayed for the link.

Default:Click here

[newTab](https://docs.evidence.dev/components/ui/link#props-newTab)

Whether the link should open in a new tab

Options:

true false

Default:false

[class](https://docs.evidence.dev/components/ui/link#props-class)

Pass custom classes to style the link. Supports [Tailwind classes](https://tailwindcss.com/).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/link/index.md)