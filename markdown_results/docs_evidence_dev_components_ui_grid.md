[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Grid](https://docs.evidence.dev/components/ui/grid)

# Grid

Use the grid component to arrange components in a grid with a specified number of columns. On smaller screen widths, the grid will stack the components vertically to maintain readability.

preview

code

```text-sm svelte
<Grid cols=2>
    <LineChart data={orders_by_category} x=order_month y=orders/>
    <BarChart data={orders_by_category} x=order_month y=orders fillColor=#00b4e0/>
    <ScatterPlot data={orders_by_category} x=order_month y=orders fillColor=#015c08/>
    <AreaChart data={orders_by_category} x=order_month y=orders fillColor=#b8645e lineColor=#b8645e/>
</Grid>
```

## [Group Component](https://docs.evidence.dev/components/ui/grid\#group-component)

To include multiple items inside one grid cell, use the `Group` component to wrap the items you want to include in that cell.

For example:

preview

code

Some text


```text-sm html
<Grid cols=2>
    <LineChart data={orders_by_category} x=order_month y=orders/>
   <Group>
      Some text
    <BarChart data={orders_by_category} x=order_month y=orders fillColor=#00b4e0/>
   </Group>
</Grid>
```

This will stack "some text" above the bar chart, rather than giving it it's own cell.

## [Options](https://docs.evidence.dev/components/ui/grid\#options)

[cols](https://docs.evidence.dev/components/ui/grid#props-cols)

Number of columns in the grid on a full size screen

Options:

1 2 3 4 5 6

Default:2

[gapSize](https://docs.evidence.dev/components/ui/grid#props-gapSize)

Space between grid elements

Options:

none sm md lg

Default:md

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/grid/index.md)