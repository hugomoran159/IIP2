[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Data](https://docs.evidence.dev/components/data) [Big Value](https://docs.evidence.dev/components/data/big-value)

# Big Value

Use big values to display a large value standalone, and optionally include a comparison and a sparkline.

preview

code

Num Orders

304

▲2.7%vs. Last Month

```text-sm markdown
<BigValue
  data={orders_with_comparisons}
  value=num_orders
  sparkline=month
  comparison=order_growth
  comparisonFmt=pct1
  comparisonTitle="vs. Last Month"
/>
```

## [Examples](https://docs.evidence.dev/components/data/big-value\#examples)

### [Default](https://docs.evidence.dev/components/data/big-value\#default)

preview

code

Num Orders

304

```text-sm markdown
<BigValue
  data={orders_with_comparisons}
  value=num_orders
/>
```

### [Comparisons](https://docs.evidence.dev/components/data/big-value\#comparisons)

preview

code

Num Orders

304

▲2.7%MoM

```text-sm markdown
<BigValue
  data={orders_with_comparisons}
  value=num_orders
  comparison=order_growth
  comparisonFmt=pct1
  comparisonTitle="MoM"
/>
```

### [Multiple cards](https://docs.evidence.dev/components/data/big-value\#multiple-cards)

Multiple cards will align themselves into a row.

preview

code

Sales

$9,905

▼-11.0%MoM

Orders

304

▲2.7%MoM

Average Order Value

$32.58

▼-13.3%MoM

```text-sm markdown
<BigValue
  data={orders_with_comparisons}
  value=sales
  fmt=usd0
  comparison=sales_growth
  comparisonFmt=pct1
  comparisonTitle="MoM"
/>
<BigValue
  data={orders_with_comparisons}
  value=num_orders
  title="Orders"
  comparison=order_growth
  comparisonFmt=pct1
  comparisonTitle="MoM"
/>
<BigValue
  data={orders_with_comparisons}
  value=aov
  title="Average Order Value"
  fmt=usd2
  comparison=aov_growth
  comparisonFmt=pct1
  comparisonTitle="MoM"
/>
```

### [Linking to other pages](https://docs.evidence.dev/components/data/big-value\#linking-to-other-pages)

The link property makes the Value component clickable, allowing navigation to other pages.

preview

code

Num Orders

[304](https://docs.evidence.dev/components/data/big-value)

▲2.7%vs. Last Month

```text-sm html
<BigValue
  data={orders_with_comparisons}
  value=num_orders
  sparkline=month
  comparison=order_growth
  comparisonFmt=pct1
  comparisonTitle="vs. Last Month"
  link='/components/data/big-value'
/>
```

### [Non-Delta Comparisons](https://docs.evidence.dev/components/data/big-value\#non-delta-comparisons)

preview

code

Num Orders

304

296 Last Month

```text-sm html
<BigValue
  data={orders_with_comparisons}
  value=num_orders
  comparison=prev_month_orders
  comparisonTitle="Last Month"
  comparisonDelta=false
/>
```

### [Sparkline](https://docs.evidence.dev/components/data/big-value\#sparkline)

preview

code

Sales

9,905.10

```text-sm html
<BigValue
  data={orders_with_comparisons}
  value=sales
  sparkline=month
/>
```

## [Options](https://docs.evidence.dev/components/data/big-value\#options)

### [Data](https://docs.evidence.dev/components/data/big-value\#data)

[data](https://docs.evidence.dev/components/data/big-value#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[value](https://docs.evidence.dev/components/data/big-value#props-value)

Required

Column to pull the main value from.

Options:column name

[title](https://docs.evidence.dev/components/data/big-value#props-title)

Title of the card.

Options:stringDefault:Title of the value column.

[minWidth](https://docs.evidence.dev/components/data/big-value#props-minWidth)

Overrides min-width of component

Options:% or px valueDefault:18%

[maxWidth](https://docs.evidence.dev/components/data/big-value#props-maxWidth)

Adds a max-width to the component

Options:% or px value

[fmt](https://docs.evidence.dev/components/data/big-value#props-fmt)

Sets format for the value ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[emptySet](https://docs.evidence.dev/components/data/big-value#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in \`build:strict\`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/data/big-value#props-emptyMessage)

Text to display when an empty dataset is received - only applies when \`emptySet\` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

[link](https://docs.evidence.dev/components/data/big-value#props-link)

Used to navigate to other pages. Can be a full external link like `https://google.com` or an internal link like `/sales/performance`

### [Comparison Options](https://docs.evidence.dev/components/data/big-value\#comparison-options)

[comparison](https://docs.evidence.dev/components/data/big-value#props-comparison)

Column to pull the comparison value from.

Options:column name

[comparisonTitle](https://docs.evidence.dev/components/data/big-value#props-comparisonTitle)

Text to the right of the comparison.

Options:stringDefault:Title of the comparison column.

[comparisonDelta](https://docs.evidence.dev/components/data/big-value#props-comparisonDelta)

Whether to display delta symbol and color

Options:

true false

Default:true

[downIsGood](https://docs.evidence.dev/components/data/big-value#props-downIsGood)

If present, negative comparison values appear in green, and positive values appear in red.

Options:

true false

Default:false

[neutralMin](https://docs.evidence.dev/components/data/big-value#props-neutralMin)

Sets the bottom of the range for 'neutral' values - neutral values appear in grey rather than red or green

Options:numberDefault:0

[neutralMax](https://docs.evidence.dev/components/data/big-value#props-neutralMax)

Sets the top of the range for 'neutral' values - neutral values appear in grey rather than red or green

Options:numberDefault:0

[comparisonFmt](https://docs.evidence.dev/components/data/big-value#props-comparisonFmt)

Sets format for the comparison ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

### [Sparkline](https://docs.evidence.dev/components/data/big-value\#sparkline-1)

[sparkline](https://docs.evidence.dev/components/data/big-value#props-sparkline)

Column to pull the date from to create the sparkline.

Options:column name

[sparklineType](https://docs.evidence.dev/components/data/big-value#props-sparklineType)

Chart type for sparkline

Options:

line area bar

Default:line

[sparklineValueFmt](https://docs.evidence.dev/components/data/big-value#props-sparklineValueFmt)

Formatting for tooltip values

Options:format codeDefault:same as fmt if supplied

[sparklineDateFmt](https://docs.evidence.dev/components/data/big-value#props-sparklineDateFmt)

Formatting for tooltip dates

Options:format codeDefault:YYYY-MM-DD

[sparklineColor](https://docs.evidence.dev/components/data/big-value#props-sparklineColor)

Color of visualization

Options:CSS name \| hexademical \| RGB \| HSL

[sparklineYScale](https://docs.evidence.dev/components/data/big-value#props-sparklineYScale)

Whether to truncate the y-axis of the chart to enhance visibility

Options:

true false

Default:false

[connectGroup](https://docs.evidence.dev/components/data/big-value#props-connectGroup)

Group name to connect this sparkline to other charts for synchronized tooltip hovering. Charts with the same \`connectGroup\` name will become connected

Options:string

[description](https://docs.evidence.dev/components/data/big-value#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/data/big-value/index.md)