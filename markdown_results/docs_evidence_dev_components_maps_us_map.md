[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Maps](https://docs.evidence.dev/components/maps) [US Map](https://docs.evidence.dev/components/maps/us-map)

# US Map

Compare a metric across US states using a flat choropleth map. For other regions see the more general [Area Map](https://docs.evidence.dev/components/maps/area-map) component.

preview

code

```text-sm html
<USMap
    data={state_population}
    state=state_name
    value=population
/>
```

## [Examples](https://docs.evidence.dev/components/maps/us-map\#examples)

### [Color Scales](https://docs.evidence.dev/components/maps/us-map\#color-scales)

`colorScale=info`

preview

code

```text-sm html
<USMap
    data={state_population}
    state=state_name
    value=population
    colorScale=info
/>
```

`colorScale=positive`

preview

code

```text-sm html
<USMap
    data={state_population}
    state=state_name
    value=population
    colorScale=positive
/>
```

`colorScale=negative`

preview

code

```text-sm html
<USMap
    data={state_population}
    state=state_name
    value=population
    colorScale=negative
/>
```

### [Custom Color Scale](https://docs.evidence.dev/components/maps/us-map\#custom-color-scale)

preview

code

```text-sm svelte
<USMap
    data={state_population}
    state=state_name
    value=population
    colorScale={['maroon','white','#1c0d80']}
    legend=true
/>
```

### [Legend](https://docs.evidence.dev/components/maps/us-map\#legend)

#### [Default](https://docs.evidence.dev/components/maps/us-map\#default)

preview

code

```text-sm html
<USMap
    data={state_population}
    state=state_name
    value=population
    legend=true
/>
```

#### [With Filter](https://docs.evidence.dev/components/maps/us-map\#with-filter)

preview

code

```text-sm svelte
<USMap
    data={state_population}
    state=state_name
    value=population
    colorScale={['maroon','white','#1c0d80']}
    legend=true
    filter=true
/>
```

### [Links](https://docs.evidence.dev/components/maps/us-map\#links)

preview

code

![](https://docs.evidence.dev/img/map-links.gif)

```text-sm html
<USMap
	data={state_current}
	state=state
	value=value
	abbreviations=true
	link=state_link
	title="Sales by State"
	subtitle="{most_recent_month[0].month}"
/>
```

### [State Abbreviations](https://docs.evidence.dev/components/maps/us-map\#state-abbreviations)

preview

code

```text-sm html
<USMap data={map_data} state=state_abbrev value=sales_usd abbreviations=true />
```

## [Options](https://docs.evidence.dev/components/maps/us-map\#options)

### [Data](https://docs.evidence.dev/components/maps/us-map\#data)

[data](https://docs.evidence.dev/components/maps/us-map#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[state](https://docs.evidence.dev/components/maps/us-map#props-state)

Required

Column to be used as the name for each state

Options:column name

[abbreviations](https://docs.evidence.dev/components/maps/us-map#props-abbreviations)

If true, map will look for two letter abbreviations rather than full names

Options:

false true

Default:false

[value](https://docs.evidence.dev/components/maps/us-map#props-value)

Required

Column to be used as the value determining the colour of each state

Options:column name

[colorScale](https://docs.evidence.dev/components/maps/us-map#props-colorScale)

Colour scale to be used. To use a custom color palette, see the `colorPalette` prop

Default:info

[colorPalette](https://docs.evidence.dev/components/maps/us-map#props-colorPalette)

Custom color palette to use for setting state colors. Overrides `colorScale`. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color codes (can be CSS, hex, RGB, HSL)

[min](https://docs.evidence.dev/components/maps/us-map#props-min)

Minimum value for the colour scale. Anything below the minimum will be shown in the same colour as the min value

Options:number

[max](https://docs.evidence.dev/components/maps/us-map#props-max)

Maximum value for the colour scale. Anything above the maximum will be shown in the same colour as the max value

Options:number

[title](https://docs.evidence.dev/components/maps/us-map#props-title)

Title appearing above the map. Is included when you click to save the map image

Options:string

[subtitle](https://docs.evidence.dev/components/maps/us-map#props-subtitle)

Subtitle appearing just above the map. Is included when you click to save the map image

Options:string

[link](https://docs.evidence.dev/components/maps/us-map#props-link)

Column containing links. When supplied, allows you to click each state on the map and navigate to the link

Options:column name

[fmt](https://docs.evidence.dev/components/maps/us-map#props-fmt)

Format to use for values ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[legend](https://docs.evidence.dev/components/maps/us-map#props-legend)

Whether to show a legend at the top of the map

Options:

true false

Default:false

[filter](https://docs.evidence.dev/components/maps/us-map#props-filter)

Whether to include filter controls on the legend. Can only be used when legend = true

Options:

true false

Default:false

[emptySet](https://docs.evidence.dev/components/maps/us-map#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to `error`, empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/maps/us-map#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is `warn` or `pass`, or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

[renderer](https://docs.evidence.dev/components/maps/us-map#props-renderer)

[downloadableData](https://docs.evidence.dev/components/maps/us-map#props-downloadableData)

Whether to show the download button to allow users to download the data

Options:

true false

Default:true

[downloadableImage](https://docs.evidence.dev/components/maps/us-map#props-downloadableImage)

Whether to show the button to allow users to save the chart as an image

Options:

true false

Default:true

Which chart renderer type (canvas or SVG) to use. See ECharts' [documentation on renderers](https://echarts.apache.org/handbook/en/best-practices/canvas-vs-svg).

Options:

canvas svg

Default:canvas

### [Custom Echarts Options](https://docs.evidence.dev/components/maps/us-map\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/maps/us-map#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[seriesOptions](https://docs.evidence.dev/components/maps/us-map#props-seriesOptions)

Custom Echarts options to override the default options for all series in the chart. This loops through the series to apply the settings rather than having to specify every series manually using `echartsOptions` See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleSeriesOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/maps/us-map#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Interactivity](https://docs.evidence.dev/components/maps/us-map\#interactivity)

[connectGroup](https://docs.evidence.dev/components/maps/us-map#props-connectGroup)

Group name to connect this chart to other charts for synchronized tooltip hovering. Charts with the same `connectGroup` name will become connected

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/maps/us-map/index.md)