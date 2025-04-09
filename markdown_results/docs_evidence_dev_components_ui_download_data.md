[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Download Data](https://docs.evidence.dev/components/ui/download-data)

# Download Data

Display a standalone button to download a specified dataset as a CSV file. Note that this component is not visible on small screen widths.

preview

code

Download

```text-sm svelte
<DownloadData data={categories}/>
```

## [Examples](https://docs.evidence.dev/components/ui/download-data\#examples)

### [Custom Text](https://docs.evidence.dev/components/ui/download-data\#custom-text)

preview

code

Click Here

```text-sm svelte
<DownloadData data={categories} text="Click Here"/>
```

### [Custom Query ID](https://docs.evidence.dev/components/ui/download-data\#custom-query-id)

preview

code

Download

```text-sm svelte
<DownloadData data={categories} queryID=my_file/>
```

## [Options](https://docs.evidence.dev/components/ui/download-data\#options)

[data](https://docs.evidence.dev/components/ui/download-data#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[display](https://docs.evidence.dev/components/ui/download-data#props-display)

Whether link is visible. If using as part of a custom component, you can pass a variable representing the hover state of your component to control visibility.

Options:

true false

Default:true

[text](https://docs.evidence.dev/components/ui/download-data#props-text)

Label to show on the link

Options:stringDefault:Download

[queryID](https://docs.evidence.dev/components/ui/download-data#props-queryID)

Label to include as the start of the CSV filename. If no queryID is supplied, "evidence\_download" is used.

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/download-data/index.md)