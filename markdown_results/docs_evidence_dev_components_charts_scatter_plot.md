[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Scatter Plot](https://docs.evidence.dev/components/charts/scatter-plot)

# Scatter Plot

Use scatter plots to show the correlation between two metrics for categorical values, or a set of samples.

preview

code

```text-sm markdown
<ScatterPlot
    data={price_vs_volume}
    x=price
    y=number_of_units
    xFmt=usd0
    series=category
/>
```

## [Examples](https://docs.evidence.dev/components/charts/scatter-plot\#examples)

### [Default](https://docs.evidence.dev/components/charts/scatter-plot\#default)

preview

code

```text-sm markdown
<ScatterPlot
    data={price_vs_volume}
    x=price
    y=number_of_units
/>
```

### [Multi-Series](https://docs.evidence.dev/components/charts/scatter-plot\#multi-series)

preview

code

```text-sm markdown
<ScatterPlot
    data={price_vs_volume}
    x=price
    y=number_of_units
    series=category
/>
```

## [Options](https://docs.evidence.dev/components/charts/scatter-plot\#options)

### [Data](https://docs.evidence.dev/components/charts/scatter-plot\#data)

[data](https://docs.evidence.dev/components/charts/scatter-plot#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/scatter-plot#props-x)

Required

Column to use for the x-axis of the chart

Options:column nameDefault:First column

[y](https://docs.evidence.dev/components/charts/scatter-plot#props-y)

Required

Column(s) to use for the y-axis of the chart

Options:column name \| array of column namesDefault:Any non-assigned numeric columns

[series](https://docs.evidence.dev/components/charts/scatter-plot#props-series)

Column to use as the series (groups) in a multi-series chart

Options:column name

[sort](https://docs.evidence.dev/components/charts/scatter-plot#props-sort)

Whether to apply default sort to your data. Default is x ascending for number and date x-axes, and y descending for category x-axes

Options:

true false

Default:true

[tooltipTitle](https://docs.evidence.dev/components/charts/scatter-plot#props-tooltipTitle)

Column to use as the title for each tooltip. Typically, this is a name to identify each point.

Options:column name

[emptySet](https://docs.evidence.dev/components/charts/scatter-plot#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/scatter-plot#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/scatter-plot\#formatting--styling)

[xFmt](https://docs.evidence.dev/components/charts/scatter-plot#props-xFmt)

Format to use for x column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[yFmt](https://docs.evidence.dev/components/charts/scatter-plot#props-yFmt)

Format to use for y column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[seriesLabelFmt](https://docs.evidence.dev/components/charts/scatter-plot#props-seriesLabelFmt)

Format to use for series label ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[shape](https://docs.evidence.dev/components/charts/scatter-plot#props-shape)

Options for which shape to use for scatter points

Options:circle \| emptyCircle \| rect \| triangle \| diamondDefault:circle

[pointSize](https://docs.evidence.dev/components/charts/scatter-plot#props-pointSize)

Change size of all points on the chart

Options:numberDefault:10

[opacity](https://docs.evidence.dev/components/charts/scatter-plot#props-opacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:0.7

[fillColor](https://docs.evidence.dev/components/charts/scatter-plot#props-fillColor)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[outlineWidth](https://docs.evidence.dev/components/charts/scatter-plot#props-outlineWidth)

Width of line surrounding each shape

Options:numberDefault:0

[outlineColor](https://docs.evidence.dev/components/charts/scatter-plot#props-outlineColor)

Color to use for outline if outlineWidth > 0

Options:CSS name \| hexademical \| RGB \| HSL

[colorPalette](https://docs.evidence.dev/components/charts/scatter-plot#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

[seriesColors](https://docs.evidence.dev/components/charts/scatter-plot#props-seriesColors)

Apply a specific color to each series in your chart. Unspecified series will receive colors from the built-in palette as normal. Note the double curly braces required in the syntax `seriesColors={{"Canada": "red", "US": "blue"}}`

Options:object with series names and assigned colorsDefault:colors applied by order of series in data

[seriesOrder](https://docs.evidence.dev/components/charts/scatter-plot#props-seriesOrder)

Apply a specific order to the series in a multi-series chart.

Options:Array of series names in the order they should be used in the chart seriesOrder={\['series one', 'series two'\]}Default:default order implied by the data

[leftPadding](https://docs.evidence.dev/components/charts/scatter-plot#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[rightPadding](https://docs.evidence.dev/components/charts/scatter-plot#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[xLabelWrap](https://docs.evidence.dev/components/charts/scatter-plot#props-xLabelWrap)

Whether to wrap x-axis labels when there is not enough space. Default behaviour is to truncate the labels.

Options:

true false

Default:false

### [Axes](https://docs.evidence.dev/components/charts/scatter-plot\#axes)

[yLog](https://docs.evidence.dev/components/charts/scatter-plot#props-yLog)

Whether to use a log scale for the y-axis

Options:

true false

Default:false

[yLogBase](https://docs.evidence.dev/components/charts/scatter-plot#props-yLogBase)

Base to use when log scale is enabled

Options:numberDefault:10

[xAxisTitle](https://docs.evidence.dev/components/charts/scatter-plot#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:true \| string \| falseDefault:true

[yAxisTitle](https://docs.evidence.dev/components/charts/scatter-plot#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:true \| string \| falseDefault:true

[xGridlines](https://docs.evidence.dev/components/charts/scatter-plot#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/scatter-plot#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/scatter-plot#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/scatter-plot#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/scatter-plot#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/scatter-plot#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/scatter-plot#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/scatter-plot#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[xMin](https://docs.evidence.dev/components/charts/scatter-plot#props-xMin)

Starting value for the x-axis

Options:number

[xMax](https://docs.evidence.dev/components/charts/scatter-plot#props-xMax)

Maximum value for the x-axis

Options:number

[yMin](https://docs.evidence.dev/components/charts/scatter-plot#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/scatter-plot#props-yMax)

Maximum value for the y-axis

Options:number

### [Chart](https://docs.evidence.dev/components/charts/scatter-plot\#chart)

[title](https://docs.evidence.dev/components/charts/scatter-plot#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/scatter-plot#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/scatter-plot#props-legend)

Turns legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true for multiple series

[chartAreaHeight](https://docs.evidence.dev/components/charts/scatter-plot#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[renderer](https://docs.evidence.dev/components/charts/scatter-plot#props-renderer)

[downloadableData](https://docs.evidence.dev/components/charts/scatter-plot#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/scatter-plot#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg).

Options:canvas \| svgDefault:canvas

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/scatter-plot\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/scatter-plot#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/scatter-plot#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using `echartsOptions` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/scatter-plot#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/scatter-plot\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/scatter-plot#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same `connectGroup` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/scatter-plot\#annotations)

Scatter plots can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<ScatterPlot data={sales_data} x=date y=sales>
  <ReferenceLine data={target_data} y=target label=name/>
  <ReferenceArea xMin='2020-03-14' xMax='2020-05-01'/>
</ScatterPlot>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/scatter-plot/index.md)