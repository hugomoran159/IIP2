[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Bar Chart](https://docs.evidence.dev/components/charts/bar-chart)

# Bar Chart

Use bar or column charts to compare a metric across categories. Bar charts are best with a small number of categories and series, and should generally start at 0.

preview

code

```text-sm markdown
<BarChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
    title="Sales by Category"
/>
```

## [Examples](https://docs.evidence.dev/components/charts/bar-chart\#examples)

### [Default](https://docs.evidence.dev/components/charts/bar-chart\#default)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_month}
    x=month
    y=sales
/>
```

### [Stacked](https://docs.evidence.dev/components/charts/bar-chart\#stacked)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
/>
```

### [100% Stacked](https://docs.evidence.dev/components/charts/bar-chart\#100-stacked)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_category_2021}
    x=month
    y=sales
    yFmt=pct0
    series=category
    type=stacked100
/>
```

### [Grouped](https://docs.evidence.dev/components/charts/bar-chart\#grouped)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
    type=grouped
/>
```

### [Horizontal](https://docs.evidence.dev/components/charts/bar-chart\#horizontal)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_item_all_time}
    x=item
    y=sales
    swapXY=true
    yFmt=usd0k
/>
```

### [Horizontal Stacked](https://docs.evidence.dev/components/charts/bar-chart\#horizontal-stacked)

preview

code

```text-sm markdown
<BarChart
    data={categories_by_channel}
    x=category
    y=sales
    series=channel
    swapXY=true
/>
```

### [Horizontal 100% Stacked](https://docs.evidence.dev/components/charts/bar-chart\#horizontal-100-stacked)

preview

code

```text-sm markdown
<BarChart
    data={categories_by_channel}
    x=category
    y=sales
    series=channel
    type=stacked100
    swapXY=true
/>
```

### [Horizontal Grouped](https://docs.evidence.dev/components/charts/bar-chart\#horizontal-grouped)

preview

code

```text-sm markdown
<BarChart
    data={categories_by_channel}
    x=category
    y=sales
    series=channel
    type=grouped
    swapXY=true
/>
```

### [Value Labels](https://docs.evidence.dev/components/charts/bar-chart\#value-labels)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_category_2021}
    x=month
    y=sales
    yFmt=usd1k
    series=category
    labels=true
/>
```

### [Custom Color Palette](https://docs.evidence.dev/components/charts/bar-chart\#custom-color-palette)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_category_2021}
    x=month
    y=sales
    series=category
    colorPalette={[\
        '#cf0d06',\
        '#eb5752',\
        '#e88a87',\
        '#fcdad9',\
        ]}
/>
```

### [Secondary / Dual y Axis](https://docs.evidence.dev/components/charts/bar-chart\#secondary--dual-y-axis)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_month}
    x=month
    y=sales_usd0k
    y2=num_orders_num0
/>
```

### [Secondary / Dual Axis with Line](https://docs.evidence.dev/components/charts/bar-chart\#secondary--dual-axis-with-line)

preview

code

```text-sm markdown
<BarChart
    data={orders_by_month}
    x=month
    y=sales
    yFmt=usd0k
    y2=num_orders
    y2SeriesType=line
/>
```

## [Options](https://docs.evidence.dev/components/charts/bar-chart\#options)

### [Data](https://docs.evidence.dev/components/charts/bar-chart\#data)

[data](https://docs.evidence.dev/components/charts/bar-chart#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/bar-chart#props-x)

Column to use for the x-axis of the chart

Options:column nameDefault:First column

[y](https://docs.evidence.dev/components/charts/bar-chart#props-y)

Column(s) to use for the y-axis of the chart

Options:column name \| array of column namesDefault:Any non-assigned numeric columns

[y2](https://docs.evidence.dev/components/charts/bar-chart#props-y2)

Column(s) to include on a secondary y-axis

Options:column name \| array of column names

[y2SeriesType](https://docs.evidence.dev/components/charts/bar-chart#props-y2SeriesType)

Chart type to apply to the series on the y2 axis

Options:

bar line scatter

Default:bar

[series](https://docs.evidence.dev/components/charts/bar-chart#props-series)

Column to use as the series (groups) in a multi-series chart

Options:column name

[sort](https://docs.evidence.dev/components/charts/bar-chart#props-sort)

Whether to apply default sort to your data. Default sort is x ascending for number and date x-axes, and y descending for category x-axes

Options:

true false

Default:true

[type](https://docs.evidence.dev/components/charts/bar-chart#props-type)

Grouping method to use for multi-series charts

Options:

stacked grouped stacked100

Default:stacked

[stackName](https://docs.evidence.dev/components/charts/bar-chart#props-stackName)

Name for an individual stack. If separate Bar components are used with different stackNames, the chart will show multiple stacks

Options:string

[emptySet](https://docs.evidence.dev/components/charts/bar-chart#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/bar-chart#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/bar-chart\#formatting--styling)

[xFmt](https://docs.evidence.dev/components/charts/bar-chart#props-xFmt)

Format to use for x column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[yFmt](https://docs.evidence.dev/components/charts/bar-chart#props-yFmt)

Format to use for y column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[y2Fmt](https://docs.evidence.dev/components/charts/bar-chart#props-y2Fmt)

Format to use for y2 column(s) ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[seriesLabelFmt](https://docs.evidence.dev/components/charts/bar-chart#props-seriesLabelFmt)

Format to use for series label ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[fillColor](https://docs.evidence.dev/components/charts/bar-chart#props-fillColor)

Color to override default series color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSL

[fillOpacity](https://docs.evidence.dev/components/charts/bar-chart#props-fillOpacity)

% of the full color that should be rendered, with remainder being transparent

Options:number (0 to 1)Default:1

[outlineWidth](https://docs.evidence.dev/components/charts/bar-chart#props-outlineWidth)

Width of line surrounding each bar

Options:numberDefault:0

[outlineColor](https://docs.evidence.dev/components/charts/bar-chart#props-outlineColor)

Color to use for outline if outlineWidth > 0

Options:CSS name \| hexademical \| RGB \| HSL

[colorPalette](https://docs.evidence.dev/components/charts/bar-chart#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

[seriesColors](https://docs.evidence.dev/components/charts/bar-chart#props-seriesColors)

Apply a specific color to each series in your chart. Unspecified series will receive colors from the built-in palette as normal. Note the double curly braces required in the syntax

Options:object with series names and assigned colorsDefault:colors applied by order of series in data

[seriesOrder](https://docs.evidence.dev/components/charts/bar-chart#props-seriesOrder)

Apply a specific order to the series in a multi-series chart.

Options:Array of series names in the order they should be used in the chart seriesOrder={\['series one', 'series two'\]}Default:default order implied by the data

[leftPadding](https://docs.evidence.dev/components/charts/bar-chart#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[rightPadding](https://docs.evidence.dev/components/charts/bar-chart#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[xLabelWrap](https://docs.evidence.dev/components/charts/bar-chart#props-xLabelWrap)

Whether to wrap x-axis labels when there is not enough space. Default behaviour is to truncate the labels.

Options:

true false

Default:false

### [Value Labels](https://docs.evidence.dev/components/charts/bar-chart\#value-labels-1)

[labels](https://docs.evidence.dev/components/charts/bar-chart#props-labels)

Show value labels

Options:

true false

Default:false

[stackTotalLabel](https://docs.evidence.dev/components/charts/bar-chart#props-stackTotalLabel)

If using labels, whether to show a total at the top of stacked bar chart

Options:

true false

Default:true

[seriesLabels](https://docs.evidence.dev/components/charts/bar-chart#props-seriesLabels)

If using labels, whether to show series labels

Options:

true false

Default:true

[labelSize](https://docs.evidence.dev/components/charts/bar-chart#props-labelSize)

Font size of value labels

Options:numberDefault:11

[labelPosition](https://docs.evidence.dev/components/charts/bar-chart#props-labelPosition)

Where label will appear on your series

Options:

outside inside

Default:Single Series: outside, Stacked: inside, Grouped: outside

[labelColor](https://docs.evidence.dev/components/charts/bar-chart#props-labelColor)

Font color of value labels

Options:CSS name \| hexademical \| RGB \| HSLDefault:Automatic based on color contrast of background

[labelFmt](https://docs.evidence.dev/components/charts/bar-chart#props-labelFmt)

Format to use for value labels ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format nameDefault:same as y column

[yLabelFmt](https://docs.evidence.dev/components/charts/bar-chart#props-yLabelFmt)

Format to use for value labels for series on the y axis. Overrides any other formats ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[y2LabelFmt](https://docs.evidence.dev/components/charts/bar-chart#props-y2LabelFmt)

Format to use for value labels for series on the y2 axis. Overrides any other formats ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[showAllLabels](https://docs.evidence.dev/components/charts/bar-chart#props-showAllLabels)

Allow all labels to appear on chart, including overlapping labels

Options:

true false

Default:false

### [Axes](https://docs.evidence.dev/components/charts/bar-chart\#axes)

[swapXY](https://docs.evidence.dev/components/charts/bar-chart#props-swapXY)

Swap the x and y axes to create a horizontal chart

Options:

true false

Default:false

[yLog](https://docs.evidence.dev/components/charts/bar-chart#props-yLog)

Whether to use a log scale for the y-axis

Options:

true false

Default:false

[yLogBase](https://docs.evidence.dev/components/charts/bar-chart#props-yLogBase)

Base to use when log scale is enabled

Options:numberDefault:10

[xAxisTitle](https://docs.evidence.dev/components/charts/bar-chart#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:

true string false

Default:false

[yAxisTitle](https://docs.evidence.dev/components/charts/bar-chart#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[y2AxisTitle](https://docs.evidence.dev/components/charts/bar-chart#props-y2AxisTitle)

Name to show beside y2 axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[xGridlines](https://docs.evidence.dev/components/charts/bar-chart#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/bar-chart#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[y2Gridlines](https://docs.evidence.dev/components/charts/bar-chart#props-y2Gridlines)

Turns on/off gridlines extending from y2-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/bar-chart#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/bar-chart#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[y2AxisLabels](https://docs.evidence.dev/components/charts/bar-chart#props-y2AxisLabels)

Turns on/off value labels on the y2-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/bar-chart#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/bar-chart#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[y2Baseline](https://docs.evidence.dev/components/charts/bar-chart#props-y2Baseline)

Turns on/off thick axis line (line appears directly alongside the y2-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/bar-chart#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/bar-chart#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[y2TickMarks](https://docs.evidence.dev/components/charts/bar-chart#props-y2TickMarks)

Turns on/off tick marks for each of the y2-axis labels

Options:

true false

Default:false

[yMin](https://docs.evidence.dev/components/charts/bar-chart#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/bar-chart#props-yMax)

Maximum value for the y-axis

Options:number

[yScale](https://docs.evidence.dev/components/charts/bar-chart#props-yScale)

Whether to scale the y-axis to fit your data. \`yMin\` and \`yMax\` take precedence over \`yScale\`

Options:

true false

Default:false

[y2Min](https://docs.evidence.dev/components/charts/bar-chart#props-y2Min)

Starting value for the y2-axis

Options:number

[y2Max](https://docs.evidence.dev/components/charts/bar-chart#props-y2Max)

Maximum value for the y2-axis

Options:number

[y2Scale](https://docs.evidence.dev/components/charts/bar-chart#props-y2Scale)

Whether to scale the y-axis to fit your data. \`y2Min\` and \`y2Max\` take precedence over \`y2Scale\`

Options:

true false

Default:false

[yAxisColor](https://docs.evidence.dev/components/charts/bar-chart#props-yAxisColor)

Turns on/off color on the y-axis (turned on by default when secondary y-axis is used). Can also be used to set a specific color

Options:

true false color string (CSS name \| hexademical \| RGB \| HSL)

Default:true when y2 used; false otherwise

### [Chart](https://docs.evidence.dev/components/charts/bar-chart\#chart)

[title](https://docs.evidence.dev/components/charts/bar-chart#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/bar-chart#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[legend](https://docs.evidence.dev/components/charts/bar-chart#props-legend)

Turns legend on or off. Legend appears at top center of chart.

Options:

true false

Default:true for multiple series

[chartAreaHeight](https://docs.evidence.dev/components/charts/bar-chart#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[renderer](https://docs.evidence.dev/components/charts/bar-chart#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

[downloadableData](https://docs.evidence.dev/components/charts/bar-chart#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/bar-chart#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/bar-chart\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/bar-chart#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/bar-chart#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/bar-chart#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/bar-chart\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/bar-chart#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/bar-chart\#annotations)

Bar charts can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<BarChart data={orders_by_month} x=month y=sales>
  <ReferenceArea xMin='2020-03-14' xMax='2021-05-01' label='COVID-19 Lockdown'/>
  <ReferenceLine data={target_data} y=target label=name/>
</BarChart>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/bar-chart/index.md)