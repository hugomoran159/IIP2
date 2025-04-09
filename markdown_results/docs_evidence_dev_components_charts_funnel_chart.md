[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Funnel Chart](https://docs.evidence.dev/components/charts/funnel-chart)

# Funnel Chart

Use funnel charts to display a single metric across a series of stages. Funnel charts are widely used for visualizing conversion.

preview

code

```text-sm markdown
<FunnelChart
    data={funnel_data}
    nameCol=stage
    valueCol=customers
/>
```

## [Examples](https://docs.evidence.dev/components/charts/funnel-chart\#examples)

### [Ascending](https://docs.evidence.dev/components/charts/funnel-chart\#ascending)

preview

code

```text-sm markdown
<FunnelChart
    data={funnel_data}
    nameCol=stage
    valueCol=customers
    funnelSort=ascending
/>
```

### [Alignment](https://docs.evidence.dev/components/charts/funnel-chart\#alignment)

preview

code

```text-sm markdown
<FunnelChart
    data={funnel_data}
    nameCol=stage
    valueCol=customers
    funnelAlign=left
/>
```

### [Show Percent Label](https://docs.evidence.dev/components/charts/funnel-chart\#show-percent-label)

preview

code

```text-sm markdown
<FunnelChart
    data={funnel_data}
    nameCol=stage
    valueCol=customers
    showPercent=true
/>
```

## [Options](https://docs.evidence.dev/components/charts/funnel-chart\#options)

### [Data](https://docs.evidence.dev/components/charts/funnel-chart\#data)

[data](https://docs.evidence.dev/components/charts/funnel-chart#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[nameCol](https://docs.evidence.dev/components/charts/funnel-chart#props-nameCol)

Required

Column to use for the name of the chart

Options:column name

[valueCol](https://docs.evidence.dev/components/charts/funnel-chart#props-valueCol)

Required

Column to use for the value of the chart

Options:column name

[emptySet](https://docs.evidence.dev/components/charts/funnel-chart#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/funnel-chart#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/funnel-chart\#formatting--styling)

[valueFmt](https://docs.evidence.dev/components/charts/funnel-chart#props-valueFmt)

Format to use for \`valueCol\` ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[outlineColor](https://docs.evidence.dev/components/charts/funnel-chart#props-outlineColor)

Border color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSLDefault:transparent

[outlineWidth](https://docs.evidence.dev/components/charts/funnel-chart#props-outlineWidth)

Border Width. It should be a natural number.

Options:numberDefault:1

[labelPosition](https://docs.evidence.dev/components/charts/funnel-chart#props-labelPosition)

Position of funnel item's label.

Options:

left right inside

Default:inside

[showPercent](https://docs.evidence.dev/components/charts/funnel-chart#props-showPercent)

Show percentage in data labels

Options:

true false

Default:false

[funnelSort](https://docs.evidence.dev/components/charts/funnel-chart#props-funnelSort)

Data sorting of the chart.

Options:

none ascending descending

Default:none

[funnelAlign](https://docs.evidence.dev/components/charts/funnel-chart#props-funnelAlign)

Alignment of funnel.

Options:

left right center

Default:center

[colorPalette](https://docs.evidence.dev/components/charts/funnel-chart#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

### [Chart](https://docs.evidence.dev/components/charts/funnel-chart\#chart)

[title](https://docs.evidence.dev/components/charts/funnel-chart#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/funnel-chart#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/funnel-chart#props-legend)

Turns legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true

[renderer](https://docs.evidence.dev/components/charts/funnel-chart#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/funnel-chart\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/funnel-chart#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/funnel-chart#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/funnel-chart#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/funnel-chart\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/funnel-chart#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/funnel-chart/index.md)