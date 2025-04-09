[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Components](https://docs.evidence.dev/core-concepts/components)

# Components

## [What are Components?](https://docs.evidence.dev/core-concepts/components\#what-are-components)

Evidence has a built in [component library](https://docs.evidence.dev/components/all-components) to create charts and other visual elements.

Components use angle brackets ( `<.../>`) to wrap the component name, like HTML syntax. Data from a query, and configuration options are passed in as properties, or "props":

```text-sm html
<BarChart
	data="{orders_by_month}"
	x="order_month"
	y="sales_usd0k"
	series="category"
	title="Sales by Category"
/>
```

![Category Bar Chart](https://docs.evidence.dev/img/category-chart.png)

## [Showing Values in Text](https://docs.evidence.dev/core-concepts/components\#showing-values-in-text)

The simplest component is the `<Value/>` component. It displays a single value from a query. It can be used to put automatically updated values in text.

````text-sm markdown
```sql orders
SELECT
    '2021-01-01' AS date,
    100 AS num_orders
```

The number of orders yesterday was <Value data = {orders} column = num_orders />.
````

Above, we've passed in the query data `orders` in curly braces `{ }`, and specified the column we want to display `num_orders` in the `column` prop.

For more information on the `Value` component, see the [Value docs](https://docs.evidence.dev/components/data/value).

## [Charts](https://docs.evidence.dev/core-concepts/components\#charts)

Our chart library has a flexible, declarative API that lets you add default chart types, or create your own.

While our library offers a lot of customizable features, we include sensible defaults that look good out of the box.

### [Props and defaults](https://docs.evidence.dev/core-concepts/components\#props-and-defaults)

At a minimum, all charts require a data prop, but for other props Evidence has default assumptions to reduce the amount of configuration required.

**Data**

- All charts require a data prop, which should contain a query result wrapped in `{...}` (e.g., `data={query_name}`)

**x and y**

- All x-y coordinate (AKA Cartesian) charts require `x` and `y` columns to create the axes and scales for the chart
- `y` can accept multiple columns, but can only plot on a single axis at this time.
- We have built-in assumptions to make writing the chart code easier:
  - If you don't supply `x`, the first column in the dataset is assumed to be `x`
  - If you don't supply `y`, any numerical columns that you have not already assigned to the chart are assumed to be `y`

**Multiple Series**

- To plot multiple series (or groups) on your chart, you can do one of the following (or both):
  - Include a `series` column, which contains category or group names (e.g, `series=country`)
  - Include multiple `y` columns - each column will be treated as an individual series (e.g., `y={["y1", "y2"]}`)

### [Annotations](https://docs.evidence.dev/core-concepts/components\#annotations)

Charts can include [annotations](https://docs.evidence.dev/components/charts/annotations) using the `ReferenceLine` and `ReferenceArea` components. These components are used within a chart component like so:

```text-sm html
<LineChart data={sales_data} x=date y=sales>
  <ReferenceLine data={target_data} y=target label=name/>
</LineChart>
```

## [Custom Components](https://docs.evidence.dev/core-concepts/components\#custom-components)

You can also build your own reusable data viz or UI components in Evidence. See [the Custom Component Guide](https://docs.evidence.dev/components/custom/custom-component) for more details.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/components/index.md)