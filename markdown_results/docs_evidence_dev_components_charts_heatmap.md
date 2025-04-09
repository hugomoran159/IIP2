[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Heatmap](https://docs.evidence.dev/components/charts/heatmap)

# Heatmap

Use heatmaps to show patterns in a single metric across two categorical dimensions, using colour to indicate size.

preview

code

```text-sm markdown
<Heatmap
    data={orders}
    x=day
    y=category
    value=order_count
    valueFmt=usd
/>
```

## [Data Structure](https://docs.evidence.dev/components/charts/heatmap\#data-structure)

Heatmap requires your data to contain 2 categorical columns (1 for the x-axis and 1 for the y-axis) and 1 numeric column.

#### [Example](https://docs.evidence.dev/components/charts/heatmap\#example)

|  |  |  |
| --- | --- | --- |
| Region | Product | Sales |
| --- | --- | --- |
| West | A | 120 |
| West | B | 200 |
| West | C | 150 |
| East | A | 110 |
| East | B | 315 |
| East | C | 450 |

No Results

|  |  |  |
| --- | --- | --- |
| Region | Product | Sales |
| --- | --- | --- |
| West | A | 120 |
| West | B | 200 |
| West | C | 150 |
| East | A | 110 |
| East | B | 315 |
| East | C | 450 |

No Results

### [Unpivoting your Data](https://docs.evidence.dev/components/charts/heatmap\#unpivoting-your-data)

If you have data spread across columns, you can use the `UNPIVOT` feature in your SQL query to prepare the data for the heatmap.

#### [Example](https://docs.evidence.dev/components/charts/heatmap\#example-1)

If you have a query result called `region_sales`:

|  |  |  |  |
| --- | --- | --- | --- |
| region | A | B | C |
| --- | --- | --- | --- |
| West | 120 | 200 | 150 |
| East | 110 | 315 | 450 |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| region | A | B | C |
| --- | --- | --- | --- |
| West | 120 | 200 | 150 |
| East | 110 | 315 | 450 |

No Results

You can use `UNPIVOT` like so:

```text-sm sql
UNPIVOT ${region_sales}
on COLUMNS(* EXCLUDE(region))
INTO
    NAME product
    VALUE sales
```

Which will return this table, which can be passed into the Heatmap:

|  |  |  |
| --- | --- | --- |
| region | product | sales |
| --- | --- | --- |
| West | A | 120 |
| West | B | 200 |
| West | C | 150 |
| East | A | 110 |
| East | B | 315 |
| East | C | 450 |

No Results

|  |  |  |
| --- | --- | --- |
| region | product | sales |
| --- | --- | --- |
| West | A | 120 |
| West | B | 200 |
| West | C | 150 |
| East | A | 110 |
| East | B | 315 |
| East | C | 450 |

No Results

**Note on Date Columns**

Heatmap currently only works with string columns. If you would like to use a date column, cast it to a string in your SQL query before passing it into the Heatmap

## [Examples](https://docs.evidence.dev/components/charts/heatmap\#examples)

### [Basic Heatmap](https://docs.evidence.dev/components/charts/heatmap\#basic-heatmap)

preview

code

```text-sm markdown
<Heatmap
    data={orders}
    x=day
    y=category
    value=order_count
    valueFmt=usd
/>
```

### [Custom Color Scale](https://docs.evidence.dev/components/charts/heatmap\#custom-color-scale)

preview

code

```text-sm svelte
<Heatmap
    data={orders}
    x=day
    y=category
    value=order_count
    valueFmt=usd
    colorScale={[\
        ['rgb(254,234,159)', 'rgb(254,234,159)'],\
        ['rgb(218,66,41)', 'rgb(218,66,41)']\
    ]}
/>
```

### [Rotated Labels](https://docs.evidence.dev/components/charts/heatmap\#rotated-labels)

preview

code

```text-sm svelte
<Heatmap
    data={item_state}
    x=item
    y=state
    value=orders
    xLabelRotation=-45
    colorScale={['white', 'maroon']}
    title="Item Sales"
    subtitle="By State"
    rightPadding=40
    cellHeight=25
    nullsZero=false
/>
```

## [Options](https://docs.evidence.dev/components/charts/heatmap\#options)

### [Data](https://docs.evidence.dev/components/charts/heatmap\#data)

[data](https://docs.evidence.dev/components/charts/heatmap#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/heatmap#props-x)

Required

Categorical column to use for the x-axis. If you want to use dates, cast them to strings in your query first

Options:column name

[y](https://docs.evidence.dev/components/charts/heatmap#props-y)

Required

Categorical column to use for the y-axis. If you want to use dates, cast them to strings in your query first

Options:column name

[value](https://docs.evidence.dev/components/charts/heatmap#props-value)

Required

Numeric column to use for the y-axis

Options:column name

[min](https://docs.evidence.dev/components/charts/heatmap#props-min)

Minimum number for the heatmap's color scale

Options:numberDefault:min of value column

[max](https://docs.evidence.dev/components/charts/heatmap#props-max)

Maximum number for the heatmap's color scale

Options:numberDefault:max of value column

[emptySet](https://docs.evidence.dev/components/charts/heatmap#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/heatmap#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/heatmap\#formatting--styling)

[nullsZero](https://docs.evidence.dev/components/charts/heatmap#props-nullsZero)

Whether to treats nulls or missing values as zero

Options:

true false

Default:true

[zeroDisplay](https://docs.evidence.dev/components/charts/heatmap#props-zeroDisplay)

String to display in place of zeros

Options:string

[colorScale](https://docs.evidence.dev/components/charts/heatmap#props-colorScale)

Array of colors to form the gradient for the heatmap.

Options:array of color codes - e.g., {\['navy', 'white', '#c9c9c9'\]}

[valueFmt](https://docs.evidence.dev/components/charts/heatmap#props-valueFmt)

Format to use for value column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[cellHeight](https://docs.evidence.dev/components/charts/heatmap#props-cellHeight)

Number representing the height of cells in the heatmap

Options:numberDefault:30

[leftPadding](https://docs.evidence.dev/components/charts/heatmap#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:numberDefault:0

[rightPadding](https://docs.evidence.dev/components/charts/heatmap#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:numberDefault:2

[valueLabels](https://docs.evidence.dev/components/charts/heatmap#props-valueLabels)

Turn on or off value labels in the heatmap cells

Options:

true false

Default:true

[mobileValueLabels](https://docs.evidence.dev/components/charts/heatmap#props-mobileValueLabels)

Turn on or off value labels in the heatmap cells when app is viewed on a mobile device screen size

Options:

true false

Default:false

[borders](https://docs.evidence.dev/components/charts/heatmap#props-borders)

Turn on or off borders around cells. Default is to show light grey border around each cell. To customize border appearance, use \`echartsOptions\`

Options:

true false

Default:true

### [Axes](https://docs.evidence.dev/components/charts/heatmap\#axes)

[xTickMarks](https://docs.evidence.dev/components/charts/heatmap#props-xTickMarks)

Turns on/off tick marks for the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/heatmap#props-yTickMarks)

Turns on/off tick marks for the y-axis labels

Options:

true false

Default:false

[xLabelRotation](https://docs.evidence.dev/components/charts/heatmap#props-xLabelRotation)

Degrees to rotate the labels on the x-axis. Can be negative number to reverse direction. \`45\` and \`-45\` are common options

Options:numberDefault:0

[xAxisPosition](https://docs.evidence.dev/components/charts/heatmap#props-xAxisPosition)

Position of x-axis and labels. Can be top or bottom. top recommended for longer charts

Options:

top bottom

Default:top

[xSort](https://docs.evidence.dev/components/charts/heatmap#props-xSort)

Column to sort x values by

Options:column name

[xSortOrder](https://docs.evidence.dev/components/charts/heatmap#props-xSortOrder)

Sets direction of sort

Options:

asc desc

Default:asc

[ySort](https://docs.evidence.dev/components/charts/heatmap#props-ySort)

Column to sort y values by

Options:column name

[ySortOrder](https://docs.evidence.dev/components/charts/heatmap#props-ySortOrder)

Sets direction of sort

Options:

asc desc

Default:asc

### [Chart](https://docs.evidence.dev/components/charts/heatmap\#chart)

[title](https://docs.evidence.dev/components/charts/heatmap#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/heatmap#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[chartAreaHeight](https://docs.evidence.dev/components/charts/heatmap#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:auto set based on y-axis values

[legend](https://docs.evidence.dev/components/charts/heatmap#props-legend)

Turn on or off the legend

Options:

true false

Default:true

[filter](https://docs.evidence.dev/components/charts/heatmap#props-filter)

Allow draggable filtering on the legend. Must be used with \`legend=true\`

Options:

true false

Default:false

[renderer](https://docs.evidence.dev/components/charts/heatmap#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

[downloadableData](https://docs.evidence.dev/components/charts/heatmap#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/heatmap#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/heatmap\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/heatmap#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/heatmap#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/heatmap#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/heatmap\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/heatmap#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/heatmap/index.md)