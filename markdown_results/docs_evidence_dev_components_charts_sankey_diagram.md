[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Sankey Diagram](https://docs.evidence.dev/components/charts/sankey-diagram)

# Sankey Diagram

Use Sankey diagrams to display flows of a metric transferring between different categories.

To display a flow with multiple levels, like these examples, see [Mutli-level](https://docs.evidence.dev/components/charts/sankey-diagram#multi-level) below.

preview

code

```text-sm svelte
<SankeyDiagram
    data={query_name}
    sourceCol= sourceCol
    targetCol = targetCol
    valueCol= valueCol
/>
```

## [Vertical](https://docs.evidence.dev/components/charts/sankey-diagram\#vertical)

preview

code

```text-sm svelte
<SankeyDiagram
    data={query_name}
    sourceCol=sourceCol
    targetCol=targetCol
    valueCol=valueCol
    orient=vertical
/>
```

# [Echarts Options String](https://docs.evidence.dev/components/charts/sankey-diagram\#echarts-options-string)

preview

code

```text-sm svelte
<SankeyDiagram
    data={traffic_data}
    title="Sankey"
    subtitle="A simple sankey chart"
    sourceCol=source
    targetCol=target
    valueCol=count
    echartsOptions={{
        title: {
            text: "Custom Echarts Option",
            textStyle: {
              color: '#476fff'
            }
        }
    }}
/>
```

# [Node Depth Override](https://docs.evidence.dev/components/charts/sankey-diagram\#node-depth-override)

preview

code

```text-sm svelte
<SankeyDiagram
    data={apple_income_statement}
    title="Apple Income Statement"
    subtitle="USD Billions"
    sourceCol=source
    targetCol=target
    valueCol=amount_usd
    depthOverride={{'services revenue': 1}}
    nodeAlign=left
/>
```

# [Labels](https://docs.evidence.dev/components/charts/sankey-diagram\#labels)

## [Node Labels](https://docs.evidence.dev/components/charts/sankey-diagram\#node-labels)

### [`nodeLabels=name` (default)](https://docs.evidence.dev/components/charts/sankey-diagram\#nodelabelsname-default)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  nodeLabels=name
/>
```

### [`nodeLabels=value`](https://docs.evidence.dev/components/charts/sankey-diagram\#nodelabelsvalue)

preview

code



The value labels can be formatted using the \`valueFmt\` option.

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  nodeLabels=value
/>
```

### [`nodeLabels=full`](https://docs.evidence.dev/components/charts/sankey-diagram\#nodelabelsfull)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  nodeLabels=full
  valueFmt=usd
/>
```

## [Link Labels](https://docs.evidence.dev/components/charts/sankey-diagram\#link-labels)

### [`linkLabels=full` (default)](https://docs.evidence.dev/components/charts/sankey-diagram\#linklabelsfull-default)

Requires `percentCol` to show percentage beside value

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  valueFmt=usd
  linkLabels=full
/>
```

### [`linkLabels=value`](https://docs.evidence.dev/components/charts/sankey-diagram\#linklabelsvalue)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  valueFmt=usd
  linkLabels=value
/>
```

### [`linkLabels=percent`](https://docs.evidence.dev/components/charts/sankey-diagram\#linklabelspercent)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  valueFmt=usd
  linkLabels=percent
/>
```

## [Custom Color Palette](https://docs.evidence.dev/components/charts/sankey-diagram\#custom-color-palette)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  linkColor=base-content-muted
  colorPalette={['#ad4940', '#3d8cc4', '#1b5218', '#ebb154']}
/>
```

## [Link Colors](https://docs.evidence.dev/components/charts/sankey-diagram\#link-colors)

### [`linkColor=base-content-muted` (default)](https://docs.evidence.dev/components/charts/sankey-diagram\#linkcolorbase-content-muted-default)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  linkColor=base-content-muted
  colorPalette={['#ad4940', '#3d8cc4', '#1b5218', '#ebb154']}
/>
```

### [`linkColor=source`](https://docs.evidence.dev/components/charts/sankey-diagram\#linkcolorsource)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  linkColor=source
  colorPalette={['#ad4940', '#3d8cc4', '#1b5218', '#ebb154']}
/>
```

### [`linkColor=target`](https://docs.evidence.dev/components/charts/sankey-diagram\#linkcolortarget)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  linkColor=target
  colorPalette={['#ad4940', '#3d8cc4', '#1b5218', '#ebb154']}
/>
```

### [`linkColor=gradient`](https://docs.evidence.dev/components/charts/sankey-diagram\#linkcolorgradient)

preview

code

```text-sm svelte
<SankeyDiagram
  data={simple_sankey}
  sourceCol=source
  targetCol=target
  valueCol=amount
  percentCol=percent
  linkColor=gradient
  colorPalette={['#6e0e08', '#3d8cc4', '#1b5218', '#ebb154']}
/>
```

## [Multi-level](https://docs.evidence.dev/components/charts/sankey-diagram\#multi-level)

The syntax for multi-level sankey diagrams is the same, but the
underlying query must represent all the levels using the same
`sourceCol` and `targetCol`, so it is necessary to `union`
each level together. `sourceCol` nodes on the next level will be linked to `targetCol` nodes in the previous level with the same name.

For example, here is the source for the visuals above.

````text-sm svelte
```sql traffic_source
select
    channel as source,
    'all_traffic' as target,
    count(user_id) as count
from events.web_events
group by 1,2

union all

select
    'all_traffic' as source,
    page_route as target,
    count(user_id) as count
from events.web_events
group by 1, 2
‍```

<SankeyDiagram
    data={traffic_data}
    title="Sankey"
    subtitle="A simple sankey chart"
    sourceCol=source
    targetCol=target
    valueCol=count
/>
````

## [Options](https://docs.evidence.dev/components/charts/sankey-diagram\#options)

### [Data](https://docs.evidence.dev/components/charts/sankey-diagram\#data)

[data](https://docs.evidence.dev/components/charts/sankey-diagram#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[sourceCol](https://docs.evidence.dev/components/charts/sankey-diagram#props-sourceCol)

Required

Column to use for the source of the diagram

Options:column name

[targetCol](https://docs.evidence.dev/components/charts/sankey-diagram#props-targetCol)

Required

Column to use for the target of the diagram

Options:column name

[valueCol](https://docs.evidence.dev/components/charts/sankey-diagram#props-valueCol)

Required

Column to use for the value of the diagram

Options:column name

[percentCol](https://docs.evidence.dev/components/charts/sankey-diagram#props-percentCol)

Column to use for the percent labels of the diagram

Options:column name

[depthOverride](https://docs.evidence.dev/components/charts/sankey-diagram#props-depthOverride)

Manual adjustment to location of each node `{{'services revenue': 2}}`

Options:object containing node name and depth level (0 is first level)

[emptySet](https://docs.evidence.dev/components/charts/sankey-diagram#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/charts/sankey-diagram#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

[printEchartsConfig](https://docs.evidence.dev/components/charts/sankey-diagram#props-printEchartsConfig)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

### [Formatting & Styling](https://docs.evidence.dev/components/charts/sankey-diagram\#formatting--styling)

[valueFmt](https://docs.evidence.dev/components/charts/sankey-diagram#props-valueFmt)

Format to use for `valueCol` ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[orient](https://docs.evidence.dev/components/charts/sankey-diagram#props-orient)

Layout direction of the nodes in the diagram.

Options:

horizontal vertical

Default:horizontal

[sort](https://docs.evidence.dev/components/charts/sankey-diagram#props-sort)

Whether the nodes are sorted by size in the diagram

Options:

true false

Default:false

[nodeAlign](https://docs.evidence.dev/components/charts/sankey-diagram#props-nodeAlign)

Controls the horizontal alignment of nodes in the diagram. When orient is vertical, nodeAlign controls vertical alignment.

Options:

justify left right

Default:justify

[nodeGap](https://docs.evidence.dev/components/charts/sankey-diagram#props-nodeGap)

The gap between any two rectangles in each column of the the diagram.

Options:numberDefault:8

[nodeWidth](https://docs.evidence.dev/components/charts/sankey-diagram#props-nodeWidth)

The node width of rectangle in the diagram.

Options:numberDefault:20

[outlineColor](https://docs.evidence.dev/components/charts/sankey-diagram#props-outlineColor)

Border color. Only accepts a single color.

Options:CSS name \| hexademical \| RGB \| HSLDefault:transparent

[outlineWidth](https://docs.evidence.dev/components/charts/sankey-diagram#props-outlineWidth)

Border Width. It should be a natural number.

Options:numberDefault:1

[colorPalette](https://docs.evidence.dev/components/charts/sankey-diagram#props-colorPalette)

Array of custom colours to use for the chart. E.g., `{['#cf0d06','#eb5752','#e88a87']}`

Options:array of color strings (CSS name \| hexademical \| RGB \| HSL)Default:built-in color palette

[linkColor](https://docs.evidence.dev/components/charts/sankey-diagram#props-linkColor)

Color to use for the links between nodes in the diagram

Options:

base-content-muted source target gradient

Default:base-content-muted

### [Chart](https://docs.evidence.dev/components/charts/sankey-diagram\#chart)

[title](https://docs.evidence.dev/components/charts/sankey-diagram#props-title)

Chart title. Appears at top left of chart.

Options:string

[subtitle](https://docs.evidence.dev/components/charts/sankey-diagram#props-subtitle)

Chart subtitle. Appears just under title.

Options:string

[nodeLabels](https://docs.evidence.dev/components/charts/sankey-diagram#props-nodeLabels)

Adds labels to the nodes of the diagram

Options:

name value full

Default:name

[linkLabels](https://docs.evidence.dev/components/charts/sankey-diagram#props-linkLabels)

Adds labels to the links between nodes

Options:

full value percent

Default:full (requires percentCol)

[chartAreaHeight](https://docs.evidence.dev/components/charts/sankey-diagram#props-chartAreaHeight)

Minimum height of the chart area (excl. header and footer) in pixels. Adjusting the height affects all viewport sizes and may impact the mobile UX.

Options:numberDefault:180

### [Custom Echarts Options](https://docs.evidence.dev/components/charts/sankey-diagram\#custom-echarts-options)

[echartsOptions](https://docs.evidence.dev/components/charts/sankey-diagram#props-echartsOptions)

Custom Echarts options to override the default options. See [reference page](https://docs.evidence.dev/components/charts/echarts-options) for available options.

Options:{{exampleOption:'exampleValue'}}

[printEchartsConfig](https://docs.evidence.dev/components/charts/sankey-diagram#props-printEchartsConfig-2)

Helper prop for custom chart development - inserts a code block with the current echarts config onto the page so you can see the options used and debug your custom options

Options:

true false

Default:false

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/sankey-diagram/index.md)