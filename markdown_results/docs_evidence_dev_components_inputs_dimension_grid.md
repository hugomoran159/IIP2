[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Dimension Grid](https://docs.evidence.dev/components/inputs/dimension-grid)

# Dimension Grid

Dimension grid produces an interactive grid of one dimension tables, one for each string column in the source table. The dimension grid can can also be used as an input.

preview

code

State

Loading...

Category

Loading...

Item

Loading...

Channel

Loading...

```text-sm markdown
<DimensionGrid data={orders} metric='sum(sales)' name=selected_dimensions />

<LineChart data={monthly_sales} handleMissing=zero/>
```

## [Examples](https://docs.evidence.dev/components/inputs/dimension-grid\#examples)

### [Basic Usage](https://docs.evidence.dev/components/inputs/dimension-grid\#basic-usage)

```text-sm html
<DimensionGrid data={my_query} />
```

### [As an Input](https://docs.evidence.dev/components/inputs/dimension-grid\#as-an-input)

Dimension grid produces a condition for all of the selected dimensions which is suitable for referencing directly in a `where` or `filter` clause. For example `airline = 'Air Canada' and plane = '747`. Where no dimensions have been selected, DimensionGrid returns `true`.

````text-sm html
<DimensionGrid
    data={my_query}
    name="selected_dimensions"
/>

```sql filtered_query
select *
from source_name.table
where ${inputs.selected_dimensions}
```
````

### [Multi Select](https://docs.evidence.dev/components/inputs/dimension-grid\#multi-select)

Using the multiple prop, Dimension grid can filter by multiple rows in the same column. Default value is false

preview

code

State

Loading...

Category

Loading...

Item

Loading...

Channel

Loading...

````text-sm html
<DimensionGrid
    data={orders}
    metric='sum(sales)'
    name=multi_dimensions
    multiple
/>

<LineChart data={monthly_sales_multi} y=sales_usd0/>

```monthly_sales_multi
select
order_month,
sum(sales) as sales_usd0
from needful_things.orders
where ${inputs.multi_dimensions}
group by all
```
````

## [Options](https://docs.evidence.dev/components/inputs/dimension-grid\#options)

[data](https://docs.evidence.dev/components/inputs/dimension-grid#props-data)

Required

Query name, wrapped in curly braces

Options:string

[metric](https://docs.evidence.dev/components/inputs/dimension-grid#props-metric)

SQL aggregate which could be applied to `data` e.g. 'sum(sales)'

Options:string

[name](https://docs.evidence.dev/components/inputs/dimension-grid#props-name)

Name of the dimension grid, used to reference the selected value elsewhere as `{inputs.name}`

Options:string

[title](https://docs.evidence.dev/components/inputs/dimension-grid#props-title)

Title for the dimension grid

Options:string

[subtitle](https://docs.evidence.dev/components/inputs/dimension-grid#props-subtitle)

Subtitle - appears under the title

Options:string

[metricLabel](https://docs.evidence.dev/components/inputs/dimension-grid#props-metricLabel)

Label for the metric

Options:string

[fmt](https://docs.evidence.dev/components/inputs/dimension-grid#props-fmt)

Sets format for the value [(see available formats)](https://docs.evidence.dev/core-concepts/formatting)

Options:Excel-style format \| built-in format \| custom format

[limit](https://docs.evidence.dev/components/inputs/dimension-grid#props-limit)

Maximum number of rows to include in each table

Options:number

[multiple](https://docs.evidence.dev/components/inputs/dimension-grid#props-multiple)

Allows for multiple rows in a column to be selected and filtered

Options:boolean

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/dimension-grid/index.md)