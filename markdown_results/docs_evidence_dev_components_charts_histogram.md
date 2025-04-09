[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Histogram](https://docs.evidence.dev/components/charts/histogram)

# Histogram

Use histograms to display the distribution of a metric along a continuous range, aggregated into buckets.

preview

code

```text-sm markdown
<Histogram
    data={orders}
    x=sales
/>
```

## [Examples](https://docs.evidence.dev/components/charts/histogram\#examples)

### [Histogram](https://docs.evidence.dev/components/charts/histogram\#histogram)

preview

code

```text-sm markdown
<Histogram
    data={orders_week}
    x=sales
    xAxisTitle="Weekly Sales"
/>
```

## [Options](https://docs.evidence.dev/components/charts/histogram\#options)

### [Data](https://docs.evidence.dev/components/charts/histogram\#data)

[data](https://docs.evidence.dev/components/charts/histogram#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/histogram#props-x)

Required

Column which contains the data you want to summarize

Options:column name

[emptySet](https://docs.evidence.dev/components/charts/histogram#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/histogram#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/histogram\#formatting--styling)

[xFmt](https://docs.evidence.dev/components/charts/histogram#props-xFmt)

Format to use for x column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[fillColor](https://docs.evidence.dev/components/charts/histogram#props-fillColor)

Color to override default series color

Options:CSS name \| hexademical \| RGB \| HSL

[fillOpacity](https://docs.evidence.dev/components/charts/histogram#props-fillOpacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:1

[colorPalette](https://docs.evidence.dev/components/charts/histogram#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

[leftPadding](https://docs.evidence.dev/components/charts/histogram#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[rightPadding](https://docs.evidence.dev/components/charts/histogram#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[xLabelWrap](https://docs.evidence.dev/components/charts/histogram#props-xLabelWrap)

Whether to wrap x-axis labels when there is not enough space. Default behaviour is to truncate the labels.

Options:

true false

Default:false

### [Axes](https://docs.evidence.dev/components/charts/histogram\#axes)

[xAxisTitle](https://docs.evidence.dev/components/charts/histogram#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:

true string false

Default:false

[yAxisTitle](https://docs.evidence.dev/components/charts/histogram#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[xGridlines](https://docs.evidence.dev/components/charts/histogram#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/histogram#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/histogram#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/histogram#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/histogram#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/histogram#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/histogram#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/histogram#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[yMin](https://docs.evidence.dev/components/charts/histogram#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/histogram#props-yMax)

Maximum value for the y-axis

Options:number

### [Chart](https://docs.evidence.dev/components/charts/histogram\#chart)

[title](https://docs.evidence.dev/components/charts/histogram#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/histogram#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/histogram#props-legend)

Turns legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true for multiple series

[chartAreaHeight](https://docs.evidence.dev/components/charts/histogram#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[renderer](https://docs.evidence.dev/components/charts/histogram#props-renderer)

[downloadableData](https://docs.evidence.dev/components/charts/histogram#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/histogram#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg).

Options:

canvas svg

Default:canvas

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/histogram\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/histogram#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/histogram#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using `echartsOptions` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/histogram#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/histogram\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/histogram#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same `connectGroup` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/histogram\#annotations)

Histograms can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<Histogram data={sales_data} x=category>
  <ReferenceLine y=20/>
  <ReferenceArea xMin=3 xMax=8/>
</Histogram>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/histogram/index.md)