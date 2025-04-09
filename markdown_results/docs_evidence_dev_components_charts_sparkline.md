[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Sparkline](https://docs.evidence.dev/components/charts/sparkline)

# Sparkline

Use sparklines to display a compact visual representation of a single metric over time or a continuous range.

preview

code

```text-sm markdown
<Sparkline
    data={sales_by_date}
    dateCol=date
    valueCol=sales
/>
```

## [Examples](https://docs.evidence.dev/components/charts/sparkline\#examples)

### [Connected Sparkline](https://docs.evidence.dev/components/charts/sparkline\#connected-sparkline)

preview

code

```text-sm html
<Sparkline data={sales_by_date} dateCol=date valueCol=sales type=bar  valueFmt=eur dateFmt=mmm connectGroup=mysparkline/>
<Sparkline data={sales_by_date} dateCol=date valueCol=sales type=area color=maroon valueFmt=eur dateFmt=mmm connectGroup=mysparkline/>
<Sparkline data={sales_by_date} dateCol=date valueCol=sales type=line color=purple valueFmt=eur dateFmt=mmm connectGroup=mysparkline/>
```

## [Options](https://docs.evidence.dev/components/charts/sparkline\#options)

### [Data](https://docs.evidence.dev/components/charts/sparkline\#data)

[data](https://docs.evidence.dev/components/charts/sparkline#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[dateCol](https://docs.evidence.dev/components/charts/sparkline#props-dateCol)

Required

Categorical column to use for the x-axis

Options:column name

[valueCol](https://docs.evidence.dev/components/charts/sparkline#props-valueCol)

Required

Numeric column to use for the y-axis

Options:column name

[type](https://docs.evidence.dev/components/charts/sparkline#props-type)

Chart type for sparkline

Options:

line area bar

Default:line

[emptySet](https://docs.evidence.dev/components/charts/sparkline#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/sparkline#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/sparkline\#formatting--styling)

[color](https://docs.evidence.dev/components/charts/sparkline#props-color)

Color to use for the visualization. For area sparklines, choose the color for the line and the area color will be automatically appplied in a lighter shade.

Options:CSS name \| hexademical \| RGB \| HSL

[valueFmt](https://docs.evidence.dev/components/charts/sparkline#props-valueFmt)

Format to use for value column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[dateFmt](https://docs.evidence.dev/components/charts/sparkline#props-dateFmt)

Format to use for date column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

### [Axes](https://docs.evidence.dev/components/charts/sparkline\#axes)

[yScale](https://docs.evidence.dev/components/charts/sparkline#props-yScale)

Whether to truncate the y-axis to enhance visibility

Options:

true false

Default:false

### [Sizing](https://docs.evidence.dev/components/charts/sparkline\#sizing)

[height](https://docs.evidence.dev/components/charts/sparkline#props-height)

Height of sparkline in pixels

Options:numberDefault:15

[width](https://docs.evidence.dev/components/charts/sparkline#props-width)

Width of sparkline in pixels

Options:numberDefault:50

### [Interactivity](https://docs.evidence.dev/components/charts/sparkline\#interactivity)

[interactive](https://docs.evidence.dev/components/charts/sparkline#props-interactive)

Turn on or off tooltip behaviour on hover. If off, chart will be a staticly rendered SVG (better for page performance). If on, you will be able to see dates/values when hovering over the sparkline

Options:

true false

Default:true

[connectGroup](https://docs.evidence.dev/components/charts/sparkline#props-connectGroup)

Group name to connect this sparkline to other charts for synchronized tooltip hovering. Charts with the same `connectGroup` name will become connected

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/sparkline/index.md)