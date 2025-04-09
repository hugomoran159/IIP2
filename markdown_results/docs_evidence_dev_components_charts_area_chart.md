[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Area Chart](https://docs.evidence.dev/components/charts/area-chart)

# Area Chart

Use area charts to track how a metric with multiple series changes over time, or a continuous range. Area charts emphasize changes in the sum of series over the individual series.

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_month}
    x=month
    y=sales
/>
```

## [Examples](https://docs.evidence.dev/components/charts/area-chart\#examples)

### [Area](https://docs.evidence.dev/components/charts/area-chart\#area)

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_month}
    x=month
    y=sales
/>
```

### [Stacked](https://docs.evidence.dev/components/charts/area-chart\#stacked)

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
/>
```

### [100% Stacked](https://docs.evidence.dev/components/charts/area-chart\#100-stacked)

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
    type=stacked100
/>
```

### [Stepped Line](https://docs.evidence.dev/components/charts/area-chart\#stepped-line)

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
    step=true
/>
```

### [Y-Axis Formatting](https://docs.evidence.dev/components/charts/area-chart\#y-axis-formatting)

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_month}
    x=month
    y=sales
    yFmt=usd0
/>
```

### [Labels](https://docs.evidence.dev/components/charts/area-chart\#labels)

preview

code

```text-sm markdown
<AreaChart
    data={orders_by_month}
    x=month
    y=sales
    labels=true
    labelFmt=usd0k
/>
```

## [Options](https://docs.evidence.dev/components/charts/area-chart\#options)

### [Data](https://docs.evidence.dev/components/charts/area-chart\#data)

[data](https://docs.evidence.dev/components/charts/area-chart#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/area-chart#props-x)

Required

Column to use for the x-axis of the chart

Options:column nameDefault:First column

[y](https://docs.evidence.dev/components/charts/area-chart#props-y)

Required

Column(s) to use for the y-axis of the chart

Options:column name \| array of column namesDefault:Any non-assigned numeric columns

[series](https://docs.evidence.dev/components/charts/area-chart#props-series)

Column to use as the series (groups) in a multi-series chart

Options:column name

[sort](https://docs.evidence.dev/components/charts/area-chart#props-sort)

Whether to apply default sort to your data. Default sort is x ascending for number and date x-axes, and y descending for category x-axes

Options:

true false

Default:true

[type](https://docs.evidence.dev/components/charts/area-chart#props-type)

Grouping method to use for multi-series charts

Options:

stacked stacked100

Default:stacked

[handleMissing](https://docs.evidence.dev/components/charts/area-chart#props-handleMissing)

Treatment of missing values in the dataset

Options:

gap connect zero

Default:gap (single series) \| zero (multi-series)

[emptySet](https://docs.evidence.dev/components/charts/area-chart#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/area-chart#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/area-chart\#formatting--styling)

[xFmt](https://docs.evidence.dev/components/charts/area-chart#props-xFmt)

Format to use for x column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[yFmt](https://docs.evidence.dev/components/charts/area-chart#props-yFmt)

Format to use for y column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[seriesLabelFmt](https://docs.evidence.dev/components/charts/area-chart#props-seriesLabelFmt)

Format to use for series label ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[step](https://docs.evidence.dev/components/charts/area-chart#props-step)

Specifies whether the chart is displayed as a step line.

Options:

true false

Default:false

[stepPosition](https://docs.evidence.dev/components/charts/area-chart#props-stepPosition)

Configures the position of turn points for a step line chart.

Options:

start middle end

Default:end

[fillColor](https://docs.evidence.dev/components/charts/area-chart#props-fillColor)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[lineColor](https://docs.evidence.dev/components/charts/area-chart#props-lineColor)

Color to override default line color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[fillOpacity](https://docs.evidence.dev/components/charts/area-chart#props-fillOpacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:0.7

[line](https://docs.evidence.dev/components/charts/area-chart#props-line)

Show line on top of the area

Options:

true false

Default:true

[colorPalette](https://docs.evidence.dev/components/charts/area-chart#props-colorPalette)

Array of custom colours to use for the chart E.g., \['#cf0d06','#eb5752','#e88a87'\] Note that the array must be surrounded by curly braces.

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

[seriesColors](https://docs.evidence.dev/components/charts/area-chart#props-seriesColors)

Apply a specific color to each series in your chart. Unspecified series will receive colors from the built-in palette as normal. Note the double curly braces required in the syntax

Options:object with series names and assigned colors seriesColors={{'Canada': 'red', 'US': 'blue'}}Default:colors applied by order of series in data

[seriesOrder](https://docs.evidence.dev/components/charts/area-chart#props-seriesOrder)

Apply a specific order to the series in a multi-series chart.

Options:Array of series names in the order they should be used in the chart seriesOrder={\['series one', 'series two'\]}Default:default order implied by the data

[leftPadding](https://docs.evidence.dev/components/charts/area-chart#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[rightPadding](https://docs.evidence.dev/components/charts/area-chart#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[xLabelWrap](https://docs.evidence.dev/components/charts/area-chart#props-xLabelWrap)

Whether to wrap x-axis labels when there is not enough space. Default behaviour is to truncate the labels.

Options:

true false

Default:false

### [Value Labels](https://docs.evidence.dev/components/charts/area-chart\#value-labels)

[labels](https://docs.evidence.dev/components/charts/area-chart#props-labels)

Show value labels

Options:

true false

Default:false

[labelSize](https://docs.evidence.dev/components/charts/area-chart#props-labelSize)

Font size of value labels

Options:numberDefault:11

[labelPosition](https://docs.evidence.dev/components/charts/area-chart#props-labelPosition)

Where label will appear on your series

Options:

above middle below

Default:above

[labelColor](https://docs.evidence.dev/components/charts/area-chart#props-labelColor)

Font color of value labels

Options:CSS name \| hexademical \| RGB \| HSLDefault:Automatic based on color contrast of background

[labelFmt](https://docs.evidence.dev/components/charts/area-chart#props-labelFmt)

Format to use for value labels ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format nameDefault:same as y column

[showAllLabels](https://docs.evidence.dev/components/charts/area-chart#props-showAllLabels)

Allow all labels to appear on chart, including overlapping labels

Options:

true false

Default:false

### [Axes](https://docs.evidence.dev/components/charts/area-chart\#axes)

[yLog](https://docs.evidence.dev/components/charts/area-chart#props-yLog)

Whether to use a log scale for the y-axis

Options:

true false

Default:false

[yLogBase](https://docs.evidence.dev/components/charts/area-chart#props-yLogBase)

Base to use when log scale is enabled

Options:numberDefault:10

[xAxisTitle](https://docs.evidence.dev/components/charts/area-chart#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:

true string false

Default:false

[yAxisTitle](https://docs.evidence.dev/components/charts/area-chart#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[xGridlines](https://docs.evidence.dev/components/charts/area-chart#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/area-chart#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/area-chart#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/area-chart#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/area-chart#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/area-chart#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/area-chart#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/area-chart#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[yMin](https://docs.evidence.dev/components/charts/area-chart#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/area-chart#props-yMax)

Maximum value for the y-axis

Options:number

[yScale](https://docs.evidence.dev/components/charts/area-chart#props-yScale)

Whether to scale the y-axis to fit your data. \`yMin\` and \`yMax\` take precedence over \`yScale\`

Options:

true false

Default:false

### [Chart](https://docs.evidence.dev/components/charts/area-chart\#chart)

[title](https://docs.evidence.dev/components/charts/area-chart#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/area-chart#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/area-chart#props-legend)

Turns legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true for multiple series

[chartAreaHeight](https://docs.evidence.dev/components/charts/area-chart#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[renderer](https://docs.evidence.dev/components/charts/area-chart#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

[downloadableData](https://docs.evidence.dev/components/charts/area-chart#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/area-chart#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/area-chart\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/area-chart#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/area-chart#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/area-chart#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/area-chart\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/area-chart#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/area-chart\#annotations)

Area charts can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<AreaChart data={sales_data} x=date y=sales>
	<ReferenceLine data={target_data} y=target label=name />
	<ReferenceArea xMin='2020-03-14' xMax='2020-05-01' />
</AreaChart>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/area-chart/index.md)