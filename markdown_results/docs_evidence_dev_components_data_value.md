[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Data](https://docs.evidence.dev/components/data) [Value](https://docs.evidence.dev/components/data/value)

# Value

Use a Value component to display a formatted value from a query inline in text.

By default, `Value` will display the value from the first row of the first column of the referenced data.

```text-sm markdown
<Value data={query_name} /> <!-- First row from the first column -->
```

## [Specifying Rows and Columns](https://docs.evidence.dev/components/data/value\#specifying-rows-and-columns)

Optionally supply a `column` and/or a `row` argument to display other values from `data`.

**Row Index**

`row` is zero-indexed, so `row=0` displays the first row.

```text-sm markdown
<!-- Show the **7th row** from column_name -->

<Value
    data={query_name}
    column=column_name
    row=6
/>
```

## [Example](https://docs.evidence.dev/components/data/value\#example)

**Markdown:**

```text-sm markdown
The most recent month of data began <Value data={monthly_orders} />,
when there were <Value data={monthly_orders} column=orders/> orders.
```

**Results:**![summary-sentence](https://docs.evidence.dev/img/tutorial-img/needful-things-value-in-text-nowindow.png)

## [Adding a Placeholder](https://docs.evidence.dev/components/data/value\#adding-a-placeholder)

Override errors with the optional `placeholder` argument. This is useful for drafting reports _before_ writing your queries.

```text-sm markdown
<Value placeholder="sales last year"/>
```

Sales in the last fiscal year were \[sales last year\]Placeholder: no data currently referenced., a change of \[X%\]Placeholder: no data currently referenced. vs. the prior year.

## [Formatting Values](https://docs.evidence.dev/components/data/value\#formatting-values)

Evidence supports a variety of formats - see [value formatting](https://docs.evidence.dev/core-concepts/formatting) and the `fmt` prop below for more info.

## [Aggregated Values](https://docs.evidence.dev/components/data/value\#aggregated-values)

Values support basic aggregations such as, `min`, `max`, `median`, `sum`, `avg`

preview

code

Loading...

```text-sm markdown
<Value data={orders} column="sales" agg="avg" fmt="usd0" />
```

## [Customize Color Values](https://docs.evidence.dev/components/data/value\#customize-color-values)

preview

code

Loading...

```text-sm markdown
<Value data={orders} column="sales" agg="avg" fmt="usd0" color="#85BB65" />
```

## [Red Negative Values](https://docs.evidence.dev/components/data/value\#red-negative-values)

If the value is negative, the font color will automatically change to red, overriding any color specified by the color prop.

preview

code

Loading...

```text-sm markdown
<Value data={NegativeSales} column="max_sales" agg="avg" fmt="usd0" redNegatives="true" />
```

## [Options](https://docs.evidence.dev/components/data/value\#options)

[data](https://docs.evidence.dev/components/data/value#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[column](https://docs.evidence.dev/components/data/value#props-column)

Column to pull values from

Options:column nameDefault:First column

[row](https://docs.evidence.dev/components/data/value#props-row)

Row number to display. 0 is the first row.

Options:numberDefault:0

[placeholder](https://docs.evidence.dev/components/data/value#props-placeholder)

Text to display in place of an error

Options:string

[fmt](https://docs.evidence.dev/components/data/value#props-fmt)

Format to use for the value ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[emptySet](https://docs.evidence.dev/components/data/value#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/data/value#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

[agg](https://docs.evidence.dev/components/data/value#props-agg)

Adds aggregation to query, column name required.

Options:

sum avg min median max

Default:null

[color](https://docs.evidence.dev/components/data/value#props-color)

Specifies the font color of the Value.

Options:CSS name \| hexademical \| RGB \| HSL

[redNegatives](https://docs.evidence.dev/components/data/value#props-redNegatives)

Conditionally sets the font color to red based on whether the selected value is less than 0

Options:

true false

Default:false

[description](https://docs.evidence.dev/components/data/value#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/data/value/index.md)