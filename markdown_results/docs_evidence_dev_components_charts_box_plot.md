[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Box Plot](https://docs.evidence.dev/components/charts/box-plot)

# Box Plot

Use box plots to summarize the distribution and range of a metric around the median value.

preview

code

```text-sm markdown
<BoxPlot
    data={sales_distribution_by_channel}
    name=channel
    intervalBottom=first_quartile
    midpoint=median
    intervalTop=third_quartile
    yFmt=usd0
/>
```

## [Data Structure](https://docs.evidence.dev/components/charts/box-plot\#data-structure)

The BoxPlot component requires pre-aggregated data, with one row per box you would like to display. There are 2 ways to pass in the values needed to construct the box:

**1\. Explicitly define each value (e.g., `min`, `intervalBottom`, `midpoint`, `intervalTop`, `max`)**

|  |  |  |  |
| --- | --- | --- | --- |
| name | intervalBottom | midpoint | intervalTop |
| --- | --- | --- | --- |
| Google Paid | 57.69 | 102.06 | 179.22 |
| Google Organic | 34.00 | 83.84 | 144.00 |
| Facebook Ads | 34.00 | 70.24 | 130.47 |
| Referral | 15.07 | 39.66 | 89.00 |
| Coupon | 9.91 | 34.00 | 67.92 |
| Tiktok Ads | 13.00 | 34.00 | 83.44 |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| name | intervalBottom | midpoint | intervalTop |
| --- | --- | --- | --- |
| Google Paid | 57.69 | 102.06 | 179.22 |
| Google Organic | 34.00 | 83.84 | 144.00 |
| Facebook Ads | 34.00 | 70.24 | 130.47 |
| Referral | 15.07 | 39.66 | 89.00 |
| Coupon | 9.91 | 34.00 | 67.92 |
| Tiktok Ads | 13.00 | 34.00 | 83.44 |

No Results

This example table excludes whiskers which would be defined with `min` and `max` columns

**2\. Define a `midpoint` and a `confidenceInterval` \- this will add the interval to the midpoint to get the max, and subtract to get the min**

|  |  |  |
| --- | --- | --- |
| name | midpoint | confidence\_interval |
| --- | --- | --- |
| Google Paid | 102.06 | 20.00 |
| Google Organic | 83.84 | 20.00 |
| Facebook Ads | 70.24 | 20.00 |
| Referral | 39.66 | 20.00 |
| Coupon | 34.00 | 20.00 |
| Tiktok Ads | 34.00 | 20.00 |

No Results

|  |  |  |
| --- | --- | --- |
| name | midpoint | confidence\_interval |
| --- | --- | --- |
| Google Paid | 102.06 | 20.00 |
| Google Organic | 83.84 | 20.00 |
| Facebook Ads | 70.24 | 20.00 |
| Referral | 39.66 | 20.00 |
| Coupon | 34.00 | 20.00 |
| Tiktok Ads | 34.00 | 20.00 |

No Results

## [Examples](https://docs.evidence.dev/components/charts/box-plot\#examples)

### [Basic Box Plot](https://docs.evidence.dev/components/charts/box-plot\#basic-box-plot)

preview

code

```text-sm markdown
<BoxPlot
    data={sales_distribution_by_channel}
    name=channel
    intervalBottom=first_quartile
    midpoint=median
    intervalTop=third_quartile
    yFmt=usd0
/>
```

### [Horizontal Box Plot](https://docs.evidence.dev/components/charts/box-plot\#horizontal-box-plot)

preview

code

```text-sm markdown
<BoxPlot
    data={sales_distribution_by_channel}
    name=channel
    intervalBottom=first_quartile
    midpoint=median
    intervalTop=third_quartile
    yFmt=usd0
    swapXY=true
/>
```

### [Box Plot with Whiskers](https://docs.evidence.dev/components/charts/box-plot\#box-plot-with-whiskers)

preview

code

```text-sm markdown
<BoxPlot
    data={sales_distribution_by_channel}
    name=channel
    min=min
    intervalBottom=first_quartile
    midpoint=median
    intervalTop=third_quartile
    max=max
    yFmt=usd0
/>
```

### [Box Plot with Custom Colors](https://docs.evidence.dev/components/charts/box-plot\#box-plot-with-custom-colors)

preview

code

```text-sm markdown
<BoxPlot
    data={sales_distribution_by_channel}
    name=channel
    intervalBottom=first_quartile
    midpoint=median
    intervalTop=third_quartile
    yFmt=usd0
    color=color
/>
```

## [Options](https://docs.evidence.dev/components/charts/box-plot\#options)

### [Data](https://docs.evidence.dev/components/charts/box-plot\#data)

[data](https://docs.evidence.dev/components/charts/box-plot#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[name](https://docs.evidence.dev/components/charts/box-plot#props-name)

Required

Column to use for the names of each box in your plot

Options:column name

[min](https://docs.evidence.dev/components/charts/box-plot#props-min)

Column containing minimum values, appearing as whisker

Options:column name

[intervalBottom](https://docs.evidence.dev/components/charts/box-plot#props-intervalBottom)

Column containing values for bottom of box

Options:column name

[midpoint](https://docs.evidence.dev/components/charts/box-plot#props-midpoint)

Required

Column containing values for midpoint of box

Options:column name

[intervalTop](https://docs.evidence.dev/components/charts/box-plot#props-intervalTop)

Column containing values for top of box

Options:column name

[max](https://docs.evidence.dev/components/charts/box-plot#props-max)

Column containing maximum values, appearing as whisker

Options:column name

[confidenceInterval](https://docs.evidence.dev/components/charts/box-plot#props-confidenceInterval)

Column containing value to use in place of intervalBottom and intervalTop. Is subtracted from midpoint to get the bottom and added to midpoint to get the top

Options:column name

[emptySet](https://docs.evidence.dev/components/charts/box-plot#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/box-plot#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/box-plot\#formatting--styling)

[color](https://docs.evidence.dev/components/charts/box-plot#props-color)

Column containing color strings

Options:column name

[yFmt](https://docs.evidence.dev/components/charts/box-plot#props-yFmt)

Format to use for y column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[seriesColors](https://docs.evidence.dev/components/charts/box-plot#props-seriesColors)

Apply a specific color to each series in your chart. Unspecified series will receive colors from the built-in palette as normal.

Options:object with series names and assigned colorsDefault:colors applied by order of series in data

[leftPadding](https://docs.evidence.dev/components/charts/box-plot#props-leftPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[rightPadding](https://docs.evidence.dev/components/charts/box-plot#props-rightPadding)

Number representing the padding (whitespace) on the left side of the chart. Useful to avoid labels getting cut off

Options:number

[xLabelWrap](https://docs.evidence.dev/components/charts/box-plot#props-xLabelWrap)

Whether to wrap x-axis labels when there is not enough space. Default behaviour is to truncate the labels.

Options:

true false

Default:false

### [Axes](https://docs.evidence.dev/components/charts/box-plot\#axes)

[swapXY](https://docs.evidence.dev/components/charts/box-plot#props-swapXY)

Swap the x and y axes to create a horizontal chart

Options:

true false

Default:false

[xAxisTitle](https://docs.evidence.dev/components/charts/box-plot#props-xAxisTitle)

Name to show under x-axis. If 'true', formatted column name is used. Only works with swapXY=false

Options:

true string false

Default:false

[yAxisTitle](https://docs.evidence.dev/components/charts/box-plot#props-yAxisTitle)

Name to show beside y-axis. If 'true', formatted column name is used.

Options:

true string false

Default:false

[xGridlines](https://docs.evidence.dev/components/charts/box-plot#props-xGridlines)

Turns on/off gridlines extending from x-axis tick marks (vertical lines when swapXY=false)

Options:

true false

Default:false

[yGridlines](https://docs.evidence.dev/components/charts/box-plot#props-yGridlines)

Turns on/off gridlines extending from y-axis tick marks (horizontal lines when swapXY=false)

Options:

true false

Default:true

[xAxisLabels](https://docs.evidence.dev/components/charts/box-plot#props-xAxisLabels)

Turns on/off value labels on the x-axis

Options:

true false

Default:true

[yAxisLabels](https://docs.evidence.dev/components/charts/box-plot#props-yAxisLabels)

Turns on/off value labels on the y-axis

Options:

true false

Default:true

[xBaseline](https://docs.evidence.dev/components/charts/box-plot#props-xBaseline)

Turns on/off thick axis line (line appears at y=0)

Options:

true false

Default:true

[yBaseline](https://docs.evidence.dev/components/charts/box-plot#props-yBaseline)

Turns on/off thick axis line (line appears directly alongside the y-axis labels)

Options:

true false

Default:false

[xTickMarks](https://docs.evidence.dev/components/charts/box-plot#props-xTickMarks)

Turns on/off tick marks for each of the x-axis labels

Options:

true false

Default:false

[yTickMarks](https://docs.evidence.dev/components/charts/box-plot#props-yTickMarks)

Turns on/off tick marks for each of the y-axis labels

Options:

true false

Default:false

[yMin](https://docs.evidence.dev/components/charts/box-plot#props-yMin)

Starting value for the y-axis

Options:number

[yMax](https://docs.evidence.dev/components/charts/box-plot#props-yMax)

Maximum value for the y-axis

Options:number

### [Chart](https://docs.evidence.dev/components/charts/box-plot\#chart)

[title](https://docs.evidence.dev/components/charts/box-plot#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/box-plot#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[chartAreaHeight](https://docs.evidence.dev/components/charts/box-plot#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

[renderer](https://docs.evidence.dev/components/charts/box-plot#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

[downloadableData](https://docs.evidence.dev/components/charts/box-plot#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/box-plot#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/box-plot\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/box-plot#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/box-plot#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/box-plot#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/box-plot\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/box-plot#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

## [Annotations](https://docs.evidence.dev/components/charts/box-plot\#annotations)

Box plots can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<BoxPlot
    data={box}
    name=experiment
    midpoint=value
    confidenceInterval=confidence
>
    <ReferenceLine y=0.04 label='Target'/>
</BoxPlot>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/box-plot/index.md)