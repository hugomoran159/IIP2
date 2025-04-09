[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Line Chart](https://docs.evidence.dev/components/charts/line-chart)

# Line Chart

Use line charts to display how one or more metrics vary over time. Line charts are suitable for plotting a large number of data points on the same chart.

preview

code

```text-sm svelte
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    yAxisTitle="Sales per Month"
/>
```

## [Examples](https://docs.evidence.dev/components/charts/line-chart\#examples)

### [Line](https://docs.evidence.dev/components/charts/line-chart\#line)

preview

code

```text-sm svelte
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    yAxisTitle="Sales per Month"
    title="Monthly Sales"
    subtitle="Includes all categories"
/>
```

### [Multi-Series Line](https://docs.evidence.dev/components/charts/line-chart\#multi-series-line)

preview

code

```text-sm markdown
<LineChart
    data={orders_by_category}
    x=month
    y=sales_usd0k
    yAxisTitle="Sales per Month"
    series=category
/>
```

### [Multi-Series Line with Steps](https://docs.evidence.dev/components/charts/line-chart\#multi-series-line-with-steps)

preview

code

```text-sm svelte
<LineChart
    data={orders_by_category}
    x=month
    y=sales_usd0k
    yAxisTitle="Sales per Month"
    series=category
    step=true
/>
```

### [Multiple y Columns](https://docs.evidence.dev/components/charts/line-chart\#multiple-y-columns)

preview

code

```text-sm svelte
<LineChart
    data={orders_by_month}
    x=month
    y={['sales_usd0k','orders']}
    yAxisTitle="Sales per Month"
/>
```

### [Secondary y Axis](https://docs.evidence.dev/components/charts/line-chart\#secondary-y-axis)

preview

code

```text-sm markdown
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    y2=orders
    yAxisTitle="Sales per Month"
/>
```

### [Secondary Axis with Bar](https://docs.evidence.dev/components/charts/line-chart\#secondary-axis-with-bar)

preview

code

```text-sm markdown
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    y2=orders
    y2SeriesType=bar
    yAxisTitle="Sales per Month"
/>
```

### [Value Labels](https://docs.evidence.dev/components/charts/line-chart\#value-labels)

preview

code

```text-sm markdown
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    yAxisTitle="Sales per Month"
    labels=true
/>
```

### [Custom Color Palette](https://docs.evidence.dev/components/charts/line-chart\#custom-color-palette)

preview

code

```text-sm markdown
<LineChart
    data={orders_by_category}
    x=month
    y=sales_usd0k
    yAxisTitle="Sales per Month"
    series=category
    colorPalette={
        [\
        '#cf0d06',\
        '#eb5752',\
        '#e88a87',\
        '#fcdad9',\
        ]
    }
/>
```

### [Markers](https://docs.evidence.dev/components/charts/line-chart\#markers)

#### [Default](https://docs.evidence.dev/components/charts/line-chart\#default)

preview

code

```text-sm svelte
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    markers=true
/>
```

#### [`markerShape=emptyCircle`](https://docs.evidence.dev/components/charts/line-chart\#markershapeemptycircle)

preview

code

```text-sm svelte
<LineChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    markers=true
    markerShape=emptyCircle
/>
```

## [Options](https://docs.evidence.dev/components/charts/line-chart\#options)

### [Data](https://docs.evidence.dev/components/charts/line-chart\#data)

[data](https://docs.evidence.dev/components/charts/line-chart#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/line-chart#props-x)

Required

Column to use for the x-axis of the chart

Options:column name

[y](https://docs.evidence.dev/components/charts/line-chart#props-y)

Required

Column(s) to use for the y-axis of the chart

Options:column name \| array of column names

[y2](https://docs.evidence.dev/components/charts/line-chart#props-y2)

Column(s) to include on a secondary y-axis

Options:column name \| array of column names

[y2SeriesType](https://docs.evidence.dev/components/charts/line-chart#props-y2SeriesType)

Chart type to apply to the series on the y2 axis

Options:

line bar scatter

Default:line

[series](https://docs.evidence.dev/components/charts/line-chart#props-series)

Column to use as the series (groups) in a multi-series chart

Options:column name

[sort](https://docs.evidence.dev/components/charts/line-chart#props-sort)

Whether to apply default sort to your data. Default is x ascending for number and date x-axes, and y descending for category x-axes

Options:

true false

Default:true

[handleMissing](https://docs.evidence.dev/components/charts/line-chart#props-handleMissing)

Treatment of missing values in the dataset

Options:

gap connect zero

Default:gap

[emptySet](https://docs.evidence.dev/components/charts/line-chart#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/line-chart#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:string

### [Formatting & Styling](https://docs.evidence.dev/components/charts/line-chart\#formatting--styling)

[xFmt](https://docs.evidence.dev/components/charts/line-chart#props-xFmt)

Format to use for x column

Options:Excel-style format \| built-in format name \| custom format name

[yFmt](https://docs.evidence.dev/components/charts/line-chart#props-yFmt)

Format to use for y column(s)

Options:Excel-style format \| built-in format name \| custom format name

[y2Fmt](https://docs.evidence.dev/components/charts/line-chart#props-y2Fmt)

Format to use for y2 column(s)

Options:Excel-style format \| built-in format name \| custom format name

[seriesLabelFmt](https://docs.evidence.dev/components/charts/line-chart#props-seriesLabelFmt)

Format to use for series label ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[step](https://docs.evidence.dev/components/charts/line-chart#props-step)

Specifies whether the chart is displayed as a step line

Options:

true false

Default:false

[stepPosition](https://docs.evidence.dev/components/charts/line-chart#props-stepPosition)

Configures the position of turn points for a step line chart

Options:

start middle end

Default:end

[lineColor](https://docs.evidence.dev/components/charts/line-chart#props-lineColor)

Color to override default series color. Only accepts a single color

Options:CSS name \| hexademical \| RGB \| HSL

[lineOpacity](https://docs.evidence.dev/components/charts/line-chart#props-lineOpacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:1

[lineType](https://docs.evidence.dev/components/charts/line-chart#props-lineType)

Options to show breaks in a line (dashed or dotted)

Options:

solid dashed dotted

Default:solid

[lineWidth](https://docs.evidence.dev/components/charts/line-chart#props-lineWidth)

Thickness of line (in pixels)

Options:numberDefault:2

[markers](https://docs.evidence.dev/components/charts/line-chart#props-markers)

Turn on/off markers (shapes rendered onto the points of a line)

Options:

true false

Default:false

[markerShape](https://docs.evidence.dev/components/charts/line-chart#props-markerShape)

Shape to use if markers=true

Options:

circle emptyCircle rect triangle diamond

Default:circle

[markerSize](https://docs.evidence.dev/components/charts/line-chart#props-markerSize)

Size of each shape (in pixels)

Options:numberDefault:8

[colorPalette](https://docs.evidence.dev/components/charts/line-chart#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)

[seriesColors](https://docs.evidence.dev/components/charts/line-chart#props-seriesColors)

Apply a specific color to each series in your chart. Unspecified series will receive colors from the built-in palette as normal. Note the double curly braces required in the syntax \`seriesColors=\[object Object\]\`

Options:object with series names and assigned colors

[seriesOrder](https://docs.evidence.dev/components/charts/line-chart#props-seriesOrder)

Apply a specific order to the series in a multi-series chart.

Options:Array of series names in the order they should be used in the chart seriesOrder={\['series one', 'series two'\]}Default:default order implied by the data

[labels](https://docs.evidence.dev/components/charts/line-chart#props-labels)

Show value labels

Options:

true false

Default:false

[labelSize](https://docs.evidence.dev/components/charts/line-chart#props-labelSize)

Font size of value labels

Options:numberDefault:11

[labelPosition](https://docs.evidence.dev/components/charts/line-chart#props-labelPosition)

Where label will appear on your series

Options:

above middle below

Default:above

[labelColor](https://docs.evidence.dev/components/charts/line-chart#props-labelColor)

Font color of value labels

Options:CSS name \| hexademical \| RGB \| HSL

[labelFmt](https://docs.evidence.dev/components/charts/line-chart#props-labelFmt)

Format to use for value labels

Options:Excel-style format \| built-in format name \| custom format name

[yLabelFmt](https://docs.evidence.dev/components/charts/line-chart#props-yLabelFmt)

Format to use for value labels for series on the y axis. Overrides any other formats

Options:Excel-style format \| built-in format name \| custom format name

[y2LabelFmt](https://docs.evidence.dev/components/charts/line-chart#props-y2LabelFmt)

Format to use for value labels for series on the y2 axis. Overrides any other formats

Options:Excel-style format \| built-in format name \| custom format name

[showAllLabels](https://docs.evidence.dev/components/charts/line-chart#props-showAllLabels)

Allow all labels to appear on chart, including overlapping labels

Options:

true false

Default:false

[leftPadding](https://docs.evidence.dev/components/charts/line-chart#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[rightPadding](https://docs.evidence.dev/components/charts/line-chart#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[xLabelWrap](https://docs.evidence.dev/components/charts/line-chart#props-xLabelWrap)

Whether to wrap x-axis labels when there is not enough space. Default behaviour is to truncate the labels.

Options:

true false

Default:false

### [Axes](https://docs.evidence.dev/components/charts/line-chart\#axes)

[yLog](https://docs.evidence.dev/components/charts/line-chart#props-yLog)

Whether to use a log scale for the y-axis

Options:

true false

Default:false

[yLogBase](https://docs.evidence.dev/components/charts/line-chart#props-yLogBase)

Base to use when log scale is enabled

Options:numberDefault:10

[xAxisTitle](https://docs.evidence.dev/components/charts/line-chart#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:

true string false

Default:false

[yAxisTitle](https://docs.evidence.dev/components/charts/line-chart#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[y2AxisTitle](https://docs.evidence.dev/components/charts/line-chart#props-y2AxisTitle)

Name to show beside y2 axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[xGridlines](https://docs.evidence.dev/components/charts/line-chart#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/line-chart#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[y2Gridlines](https://docs.evidence.dev/components/charts/line-chart#props-y2Gridlines)

Turns on/off gridlines extending from y2-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/line-chart#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/line-chart#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[y2AxisLabels](https://docs.evidence.dev/components/charts/line-chart#props-y2AxisLabels)

Turns on/off value labels on the y2-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/line-chart#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/line-chart#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[y2Baseline](https://docs.evidence.dev/components/charts/line-chart#props-y2Baseline)

Turns on/off thick axis line (line appears directly alongside the y2-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/line-chart#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/line-chart#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[y2TickMarks](https://docs.evidence.dev/components/charts/line-chart#props-y2TickMarks)

Turns on/off tick marks for each of the y2-axis labels

Options:

true false

Default:false

[yMin](https://docs.evidence.dev/components/charts/line-chart#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/line-chart#props-yMax)

Maximum value for the y-axis

Options:number

[yScale](https://docs.evidence.dev/components/charts/line-chart#props-yScale)

Whether to scale the y-axis to fit your data. \`yMin\` and \`yMax\` take precedence over \`yScale\`

Options:

true false

Default:false

[y2Min](https://docs.evidence.dev/components/charts/line-chart#props-y2Min)

Starting value for the y2-axis

Options:number

[y2Max](https://docs.evidence.dev/components/charts/line-chart#props-y2Max)

Maximum value for the y2-axis

Options:number

[y2Scale](https://docs.evidence.dev/components/charts/line-chart#props-y2Scale)

Whether to scale the y-axis to fit your data. \`y2Min\` and \`y2Max\` take precedence over \`y2Scale\`

Options:

true false

Default:false

### [Chart](https://docs.evidence.dev/components/charts/line-chart\#chart)

[title](https://docs.evidence.dev/components/charts/line-chart#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/line-chart#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/line-chart#props-legend)

Turn legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true for multiple series

[chartAreaHeight](https://docs.evidence.dev/components/charts/line-chart#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[renderer](https://docs.evidence.dev/components/charts/line-chart#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

[downloadableData](https://docs.evidence.dev/components/charts/line-chart#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/line-chart#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/line-chart\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/line-chart#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/line-chart#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/line-chart#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/line-chart\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/line-chart#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/line-chart\#annotations)

Line charts can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<LineChart data="{sales_data}" x="date" y="sales">
	<ReferenceLine data="{target_data}" y="target" label="name" />
	<ReferenceArea xMin="2020-03-14" xMax="2020-05-01" />
</LineChart>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/line-chart/index.md)