[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Mixed-Type Charts](https://docs.evidence.dev/components/charts/mixed-type-charts)

# Mixed-Type Charts

Use mixed-type charts to display multiple series types on the same chart, for example a bar for an amount, and a line for a related percentage.

Mixed-type charts can be confusing, so use them sparingly. To add reference lines, areas or points to a chart instead, see [Annotations](https://docs.evidence.dev/components/charts/annotations).

The easiest way to create mixed-type charts is setting up [a secondary y-axis in `LineChart`](https://docs.evidence.dev/components/charts/line-chart#secondary-axis-with-bar) or a [secondary axis in `BarChart`](https://docs.evidence.dev/components/charts/bar-chart#secondary-axis-with-line)

You can combine multiple chart types inside a single `<Chart>` tag to create mixed-type charts.

## [Examples](https://docs.evidence.dev/components/charts/mixed-type-charts\#examples)

### [Mixed-Type Chart](https://docs.evidence.dev/components/charts/mixed-type-charts\#mixed-type-chart)

This example uses multiple y columns and multiple series types (bar and line)

preview

code

![Mixed-Type Chart](https://docs.evidence.dev/img/exg-composable-multi-type-nt.svg)

```text-sm markdown
<Chart data={fda_recalls}>
    <Bar y=voluntary_recalls/>
    <Line y=fda_recalls/>
</Chart>
```

Because x is the first column in the dataset, an explicit `x` prop is not required.

This structure also gives you control over the individual series on your chart. For example, if you have a single series running through a component, you can override props specifically for that series. Since the FDA acronym was not fully capitalized above, you can rename that specific series inside the `<Line>` primitive:

preview

code

![Mixed-Type Chart Name Overide](https://docs.evidence.dev/img/exg-composable-name-override-nt.svg)

```text-sm markdown
<Chart data={fda_recalls}>
    <Bar y=voluntary_recalls/>
    <Line y=fda_recalls name="FDA Recalls"/>
</Chart>
```

# [Chart `<Chart>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#chart-ltchartgt)

```text-sm markdown
<Chart data={query_name}>
    Insert primitives here
</Chart>
```

## [Data](https://docs.evidence.dev/components/charts/mixed-type-charts\#data)

[data](https://docs.evidence.dev/components/charts/mixed-type-charts#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/mixed-type-charts#props-x)

Column to use for the x-axis of the chart

Options:column name

[y](https://docs.evidence.dev/components/charts/mixed-type-charts#props-y)

Column(s) to use for the y-axis of the chart

Options:column name \| array of column names

[sort](https://docs.evidence.dev/components/charts/mixed-type-charts#props-sort)

Whether to apply default sort to your data. Default is x ascending for number and date x-axes, and y descending for category x-axes

Options:

true false

Default:true

[series](https://docs.evidence.dev/components/charts/mixed-type-charts#props-series)

Column to use as the series (groups) in a multi-series chart

Options:column name

[xFmt](https://docs.evidence.dev/components/charts/mixed-type-charts#props-xFmt)

Format to use for x column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[yFmt](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yFmt)

Format to use for y column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[yLog](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yLog)

Whether to use a log scale for the y-axis

Options:

true false

Default:false

[yLogBase](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yLogBase)

Base to use when log scale is enabled

Options:numberDefault:10

[emptySet](https://docs.evidence.dev/components/charts/mixed-type-charts#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in build:strict. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/mixed-type-charts#props-emptyMessage)

Text to display when an empty dataset is received - only applies when emptySet is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

## [Chart](https://docs.evidence.dev/components/charts/mixed-type-charts\#chart)

[swapXY](https://docs.evidence.dev/components/charts/mixed-type-charts#props-swapXY)

Swap the x and y axes to create a horizontal chart

Options:

true false

Default:false

[title](https://docs.evidence.dev/components/charts/mixed-type-charts#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/mixed-type-charts#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/mixed-type-charts#props-legend)

Turns legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true for multiple series

[chartAreaHeight](https://docs.evidence.dev/components/charts/mixed-type-charts#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[xAxisTitle](https://docs.evidence.dev/components/charts/mixed-type-charts#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:

true string false

Default:false

[yAxisTitle](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[xGridlines](https://docs.evidence.dev/components/charts/mixed-type-charts#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/mixed-type-charts#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/mixed-type-charts#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/mixed-type-charts#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[yMin](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yMax)

Maximum value for the y-axis

Options:number

[yScale](https://docs.evidence.dev/components/charts/mixed-type-charts#props-yScale)

Whether to scale the y-axis to fit your data. yMin and yMax take precedence over yScale

Options:

true false

Default:false

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

[colorPalette](https://docs.evidence.dev/components/charts/mixed-type-charts#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

[seriesColors](https://docs.evidence.dev/components/charts/mixed-type-charts#props-seriesColors)

Apply a specific color to each series in your chart. Unspecified series will receive colors from the built-in palette as normal. Note the double curly braces required in the syntax `seriesColors={{"Canada": "red", "US": "blue"}}`

Options:object with series names and assigned colorsDefault:colors applied by order of series in data

[renderer](https://docs.evidence.dev/components/charts/mixed-type-charts#props-renderer)

[downloadableData](https://docs.evidence.dev/components/charts/mixed-type-charts#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/mixed-type-charts#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg).

Options:

canvas svg

Default:canvas

# [Line `<Line/>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#line-ltlinegt)

```text-sm markdown
<Chart data={query_name}>
    <Line/>
</Chart>
```

## [Options](https://docs.evidence.dev/components/charts/mixed-type-charts\#options)

[y](https://docs.evidence.dev/components/charts/mixed-type-charts#props-y-2)

Column(s) to use for the y-axis of the chart. Can be different than the y supplied to Chart

Options:column name \| array of column namesDefault:y supplied to Chart

[series](https://docs.evidence.dev/components/charts/mixed-type-charts#props-series-2)

Column to use as the series (groups) in a multi-series chart. Can be different than the series supplied to Chart

Options:column nameDefault:series supplied to Chart

[name](https://docs.evidence.dev/components/charts/mixed-type-charts#props-name)

Name to show in legend for a single series (to override column name)

Options:string

[lineColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-lineColor)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[lineOpacity](https://docs.evidence.dev/components/charts/mixed-type-charts#props-lineOpacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:1

[lineType](https://docs.evidence.dev/components/charts/mixed-type-charts#props-lineType)

Options to show breaks in a line (dashed or dotted)

Options:

solid dashed dotted

Default:solid

[lineWidth](https://docs.evidence.dev/components/charts/mixed-type-charts#props-lineWidth)

Thickness of line (in pixels)

Options:numberDefault:2

[markers](https://docs.evidence.dev/components/charts/mixed-type-charts#props-markers)

Turn on/off markers (shapes rendered onto the points of a line)

Options:

true false

Default:false

[markerShape](https://docs.evidence.dev/components/charts/mixed-type-charts#props-markerShape)

Shape to use if markers=true

Options:

circle emptyCircle rect triangle diamond

Default:circle

[markerSize](https://docs.evidence.dev/components/charts/mixed-type-charts#props-markerSize)

Size of each shape (in pixels)

Options:numberDefault:8

[handleMissing](https://docs.evidence.dev/components/charts/mixed-type-charts#props-handleMissing)

Treatment of missing values in the dataset

Options:

gap connect zero

Default:gap

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options-2)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

# [Area `<Area/>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#area-ltareagt)

```text-sm markdown
<Chart data={query_name}>
    <Area/>
</Chart>
```

## [Options](https://docs.evidence.dev/components/charts/mixed-type-charts\#options-1)

[y](https://docs.evidence.dev/components/charts/mixed-type-charts#props-y-3)

Column(s) to use for the y-axis of the chart. Can be different than the y supplied to Chart

Options:column name \| array of column namesDefault:y supplied to Chart

[series](https://docs.evidence.dev/components/charts/mixed-type-charts#props-series-3)

Column to use as the series (groups) in a multi-series chart. Can be different than the series supplied to Chart

Options:column nameDefault:series supplied to Chart

[name](https://docs.evidence.dev/components/charts/mixed-type-charts#props-name-2)

Name to show in legend for a single series (to override column name)

Options:string

[fillColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillColor)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[fillOpacity](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillOpacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:0.7

[line](https://docs.evidence.dev/components/charts/mixed-type-charts#props-line)

Show line on top of the area

Options:

true false

Default:true

[handleMissing](https://docs.evidence.dev/components/charts/mixed-type-charts#props-handleMissing-2)

Treatment of missing values in the dataset

Options:

gap connect zero

Default:gap (single series) \| zero (multi-series)

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options-3)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

# [Bar `<Bar/>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#bar-ltbargt)

```text-sm markdown
<Chart data={query_name}>
    <Bar/>
</Chart>
```

## [Options](https://docs.evidence.dev/components/charts/mixed-type-charts\#options-2)

[y](https://docs.evidence.dev/components/charts/mixed-type-charts#props-y-4)

Column to use for the y-axis of the chart

Options:column name

[name](https://docs.evidence.dev/components/charts/mixed-type-charts#props-name-3)

Name to show in legend for a single series (to override column name)

Options:string

[type](https://docs.evidence.dev/components/charts/mixed-type-charts#props-type)

Grouping method to use for multi-series charts

Options:

stacked grouped

Default:stacked

[stackName](https://docs.evidence.dev/components/charts/mixed-type-charts#props-stackName)

Name for an individual stack. If separate Bar components are used with different stackNames, the chart will show multiple stacks

Options:string

[fillColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillColor-2)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[fillOpacity](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillOpacity-2)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:1

[outlineWidth](https://docs.evidence.dev/components/charts/mixed-type-charts#props-outlineWidth)

Width of line surrounding each bar

Options:numberDefault:0

[outlineColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-outlineColor)

Color to use for outline if outlineWidth > 0

Options:CSS name \| hexademical \| RGB \| HSL

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options-4)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

# [Scatter `<Scatter/>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#scatter-ltscattergt)

```text-sm markdown
<Chart data={query_name}>
    <Scatter/>
</Chart>
```

## [Options](https://docs.evidence.dev/components/charts/mixed-type-charts\#options-3)

[y](https://docs.evidence.dev/components/charts/mixed-type-charts#props-y-5)

Column to use for the y-axis of the chart

Options:column name

[name](https://docs.evidence.dev/components/charts/mixed-type-charts#props-name-4)

Name to show in legend for a single series (to override column name)

Options:string

[shape](https://docs.evidence.dev/components/charts/mixed-type-charts#props-shape)

Options for which shape to use for scatter points

Options:

circle emptyCircle rect triangle diamond

Default:circle

[pointSize](https://docs.evidence.dev/components/charts/mixed-type-charts#props-pointSize)

Change size of all points on the chart

Options:numberDefault:10

[opacity](https://docs.evidence.dev/components/charts/mixed-type-charts#props-opacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:0.7

[fillColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillColor-3)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[outlineWidth](https://docs.evidence.dev/components/charts/mixed-type-charts#props-outlineWidth-2)

Width of line surrounding each shape

Options:numberDefault:0

[outlineColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-outlineColor-2)

Color to use for outline if outlineWidth > 0

Options:CSS name \| hexademical \| RGB \| HSL

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options-5)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

# [Bubble `<Bubble/>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#bubble-ltbubblegt)

```text-sm markdown
<Chart data={query_name}>
    <Bubble/>
</Chart>
```

## [Options](https://docs.evidence.dev/components/charts/mixed-type-charts\#options-4)

[y](https://docs.evidence.dev/components/charts/mixed-type-charts#props-y-6)

Column to use for the y-axis of the chart

Options:column name

[size](https://docs.evidence.dev/components/charts/mixed-type-charts#props-size)

Column to use to scale the size of the bubbles

Options:column name

[name](https://docs.evidence.dev/components/charts/mixed-type-charts#props-name-5)

Name to show in legend for a single series (to override column name)

Options:string

[shape](https://docs.evidence.dev/components/charts/mixed-type-charts#props-shape-2)

Options for which shape to use for bubble points

Options:

circle emptyCircle rect triangle diamond

Default:circle

[minSize](https://docs.evidence.dev/components/charts/mixed-type-charts#props-minSize)

Minimum bubble size

Options:numberDefault:200

[maxSize](https://docs.evidence.dev/components/charts/mixed-type-charts#props-maxSize)

Maximum bubble size

Options:numberDefault:400

[opacity](https://docs.evidence.dev/components/charts/mixed-type-charts#props-opacity-2)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:0.7

[fillColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillColor-4)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[outlineWidth](https://docs.evidence.dev/components/charts/mixed-type-charts#props-outlineWidth-3)

Width of line surrounding each shape

Options:numberDefault:0

[outlineColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-outlineColor-3)

Color to use for outline if outlineWidth > 0

Options:CSS name \| hexademical \| RGB \| HSL

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options-6)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

# [Hist `<Hist/>`](https://docs.evidence.dev/components/charts/mixed-type-charts\#hist-lthistgt)

```text-sm markdown
<Chart data={query_name}>
    <Hist/>
</Chart>
```

## [Options](https://docs.evidence.dev/components/charts/mixed-type-charts\#options-5)

[x](https://docs.evidence.dev/components/charts/mixed-type-charts#props-x-2)

Column which contains the data you want to summarize

Options:column name

[fillColor](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillColor-5)

Color to override default series color

Options:CSS name \| hexademical \| RGB \| HSL

[fillOpacity](https://docs.evidence.dev/components/charts/mixed-type-charts#props-fillOpacity-3)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:1

[options](https://docs.evidence.dev/components/charts/mixed-type-charts#props-options-7)

JavaScript object to add or override chart configuration settings (see Custom Charts page)

Options:object

### [Interactivity](https://docs.evidence.dev/components/charts/mixed-type-charts\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/mixed-type-charts#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same `connectGroup` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/mixed-type-charts\#annotations)

Mixed type charts can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<Chart data={sales_data} x=date y=sales>
  <Line y=sales/>
  <ReferenceLine data={target_data} y=target label=name/>
  <ReferenceArea xMin='2020-03-14' xMax='2020-05-01'/>
</Chart>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/mixed-type-charts/index.md)