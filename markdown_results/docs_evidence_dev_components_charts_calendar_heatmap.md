[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Calendar Heatmap](https://docs.evidence.dev/components/charts/calendar-heatmap)

# Calendar Heatmap

Use calendar heatmaps to display how a single metric varies over weeks and months.

preview

code

```text-sm markdown
<CalendarHeatmap
    data={orders_by_day_2021}
    date=day
    value=sales
    title="Calendar Heatmap"
    subtitle="Daily Sales"
/>
```

## [Examples](https://docs.evidence.dev/components/charts/calendar-heatmap\#examples)

### [Multi-Year](https://docs.evidence.dev/components/charts/calendar-heatmap\#multi-year)

preview

code

```text-sm markdown
<CalendarHeatmap
    data={orders_by_day}
    date=day
    value=sales
/>
```

### [Custom Color Scale](https://docs.evidence.dev/components/charts/calendar-heatmap\#custom-color-scale)

preview

code

```text-sm markdown
<CalendarHeatmap
    data={orders_by_day_2021}
    date=day
    value=sales
    colorScale={[\
        ['rgb(254,234,159)', 'rgb(254,234,159)'],\
        ['rgb(218,66,41)', 'rgb(218,66,41)']\
    ]}
/>
```

### [Without Year Label](https://docs.evidence.dev/components/charts/calendar-heatmap\#without-year-label)

preview

code

```text-sm markdown
<CalendarHeatmap
    data={orders_by_day_2021}
    date=day
    value=sales
    yearLabel=false
/>
```

## [Options](https://docs.evidence.dev/components/charts/calendar-heatmap\#options)

### [Data](https://docs.evidence.dev/components/charts/calendar-heatmap\#data)

[data](https://docs.evidence.dev/components/charts/calendar-heatmap#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[date](https://docs.evidence.dev/components/charts/calendar-heatmap#props-date)

Required

Date column to use for the calendar

Options:column name

[value](https://docs.evidence.dev/components/charts/calendar-heatmap#props-value)

Required

Numeric column to use for the y-axis

Options:column name

[min](https://docs.evidence.dev/components/charts/calendar-heatmap#props-min)

Minimum number for the calendar heatmap's color scale

Options:numberDefault:min of value column

[max](https://docs.evidence.dev/components/charts/calendar-heatmap#props-max)

Maximum number for the calendar heatmap's color scale

Options:numberDefault:max of value column

[emptySet](https://docs.evidence.dev/components/charts/calendar-heatmap#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/calendar-heatmap#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

### [Formatting & Styling](https://docs.evidence.dev/components/charts/calendar-heatmap\#formatting--styling)

[colorScale](https://docs.evidence.dev/components/charts/calendar-heatmap#props-colorScale)

Array of colors to form the gradient for the heatmap. Remember to wrap your array in curly braces.

Options:array of color codes - e.g., colorScale={\['navy', 'white', '#c9c9c9'\]}

[valueFmt](https://docs.evidence.dev/components/charts/calendar-heatmap#props-valueFmt)

Format to use for value column ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format name \| custom format name

[yearLabel](https://docs.evidence.dev/components/charts/calendar-heatmap#props-yearLabel)

Turn on or off year label on left of chart

Options:

true false

Default:true

[monthLabel](https://docs.evidence.dev/components/charts/calendar-heatmap#props-monthLabel)

Turn on or off month label on top of chart

Options:

true false

Default:true

[dayLabel](https://docs.evidence.dev/components/charts/calendar-heatmap#props-dayLabel)

Turn on or off day label on left of chart

Options:

true false

Default:true

### [Chart](https://docs.evidence.dev/components/charts/calendar-heatmap\#chart)

[title](https://docs.evidence.dev/components/charts/calendar-heatmap#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/calendar-heatmap#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[chartAreaHeight](https://docs.evidence.dev/components/charts/calendar-heatmap#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:auto set based on y-axis values

[legend](https://docs.evidence.dev/components/charts/calendar-heatmap#props-legend)

Turn on or off the legend

Options:

true false

Default:true

[filter](https://docs.evidence.dev/components/charts/calendar-heatmap#props-filter)

Allow draggable filtering on the legend. Must be used with \`legend=true\`

Options:

true false

Default:false

[renderer](https://docs.evidence.dev/components/charts/calendar-heatmap#props-renderer)

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg/).

Options:

canvas svg

Default:canvas

[downloadableData](https://docs.evidence.dev/components/charts/calendar-heatmap#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/charts/calendar-heatmap#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/calendar-heatmap\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/calendar-heatmap#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/charts/calendar-heatmap#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using \`echartsOptions\` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/calendar-heatmap#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/charts/calendar-heatmap\#interactivity)

[connectGroup](https://docs.evidence.dev/components/charts/calendar-heatmap#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/calendar-heatmap/index.md)