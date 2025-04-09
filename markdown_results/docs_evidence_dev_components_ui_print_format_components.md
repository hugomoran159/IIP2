[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Print Format Components](https://docs.evidence.dev/components/ui/print-format-components)

# Print Format Components

These components can be used to format your report content for PDF export or printing.

## [LineBreak](https://docs.evidence.dev/components/ui/print-format-components\#linebreak)

Inserts a line break on the page (in the UI as well as on print).

This can be helpful when working with many input components (filters, dropdowns, etc.)

```text-sm html
Text on original line <LineBreak/> Text on new line
```

### [Options](https://docs.evidence.dev/components/ui/print-format-components\#options)

[lines](https://docs.evidence.dev/components/ui/print-format-components#props-lines)

Number of line breaks to insert

Options:numberDefault:1

## [PageBreak](https://docs.evidence.dev/components/ui/print-format-components\#pagebreak)

On print, inserts a page break - pushing the next content onto the start of a new page.

```text-sm html
The purple line chart in this section will print on a new page.

<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
/>

<PageBreak/>

<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    lineColor=purple
/>

```

## [PrintGroup](https://docs.evidence.dev/components/ui/print-format-components\#printgroup)

- Combines content to be printed on the same page if possible
- Offers a `hidden` prop. If `true`, the content within the PrintGroup will not be printed

```text-sm html
<PrintGroup>

    The 2 heatmaps below will be printed on the same page if possible

    <Heatmap data={item_channel} x=channel y=item value=orders/>
    <Heatmap data={item_channel} x=channel y=item value=orders/>
</PrintGroup>
```

### [`hidden=true`](https://docs.evidence.dev/components/ui/print-format-components\#hiddentrue)

```text-sm html
The purple line chart will be hidden on print

<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
/>

<PrintGroup hidden=true>
    <LineChart
        data={orders_by_month}
        x=month
        y=sales_usd0k
        lineColor=purple
    />
</PrintGroup>
```

### [Options](https://docs.evidence.dev/components/ui/print-format-components\#options-1)

[hidden](https://docs.evidence.dev/components/ui/print-format-components#props-hidden)

If true, the content within the PrintGroup will not be printed

Options:

true false

Default:false

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/print-format-components/index.md)