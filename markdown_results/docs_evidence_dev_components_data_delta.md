[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Data](https://docs.evidence.dev/components/data) [Delta](https://docs.evidence.dev/components/data/delta)

# Delta

Use a Delta component to display an inline indicator that shows how a value has changed.

preview

code

This value is +36.6%▲ since last month.

```text-sm markdown
This value is <Delta data={growth} column=positive fmt="+0.0%;-0.0%;0.0%" /> since last month.
```

## [Examples](https://docs.evidence.dev/components/data/delta\#examples)

### [Value Types](https://docs.evidence.dev/components/data/delta\#value-types)

#### [Positive](https://docs.evidence.dev/components/data/delta\#positive)

preview

code

36.6%▲

```text-sm markdown
<Delta data={growth} column=positive fmt=pct1 />
```

#### [Negative](https://docs.evidence.dev/components/data/delta\#negative)

preview

code

-36.6%▼

```text-sm markdown
<Delta data={growth} column=negative fmt=pct1 />
```

#### [Neutral\*](https://docs.evidence.dev/components/data/delta\#neutral)

\*Values are not defined as neutral until you define a range using the `neutralMin` and `neutralMax` props

preview

code

1.0%–

```text-sm markdown
<Delta data={growth} column=neutral fmt=pct1 neutralMin=-0.02 neutralMax=0.02 />
```

### [Chips](https://docs.evidence.dev/components/data/delta\#chips)

#### [Positive](https://docs.evidence.dev/components/data/delta\#positive-1)

preview

code

36.6%▲

```text-sm markdown
<Delta data={growth} column=growth fmt=pct1 chip=true />
```

#### [Negative](https://docs.evidence.dev/components/data/delta\#negative-1)

preview

code

-36.6%▼

```text-sm markdown
<Delta data={growth} column=negative fmt=pct1 chip=true/>
```

#### [Neutral\*](https://docs.evidence.dev/components/data/delta\#neutral-1)

\*Values are not defined as neutral until you define a range using the `neutralMin` and `neutralMax` props

preview

code

1.0%–

```text-sm markdown
<Delta data={growth} column=neutral fmt=pct1 chip=true neutralMin=-0.02 neutralMax=0.02 />
```

### [Symbol Position](https://docs.evidence.dev/components/data/delta\#symbol-position)

#### [Symbol on Left](https://docs.evidence.dev/components/data/delta\#symbol-on-left)

preview

code

▲36.6%

```text-sm html
<Delta data={growth} column=positive fmt=pct1 symbolPosition=left/>
```

#### [Symbol on Left in Chip](https://docs.evidence.dev/components/data/delta\#symbol-on-left-in-chip)

preview

code

▲36.6%

```text-sm html
<Delta data={growth} column=positive fmt=pct1 chip=true symbolPosition=left/>
```

## [Options](https://docs.evidence.dev/components/data/delta\#options)

[data](https://docs.evidence.dev/components/data/delta#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[column](https://docs.evidence.dev/components/data/delta#props-column)

Column to pull values from

Options:column nameDefault:First column

[row](https://docs.evidence.dev/components/data/delta#props-row)

Row number to display. 0 is the first row.

Options:numberDefault:0

[value](https://docs.evidence.dev/components/data/delta#props-value)

Pass a specific value to the component (e.g., value=100). Overridden by the data/column props.

Options:number

[fmt](https://docs.evidence.dev/components/data/delta#props-fmt)

Format to use for the value ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[downIsGood](https://docs.evidence.dev/components/data/delta#props-downIsGood)

If true, negative comparison values appear in green, and positive values appear in red.

Options:

true false

Default:false

[showSymbol](https://docs.evidence.dev/components/data/delta#props-showSymbol)

Whether to show the up/down delta arrow symbol

Options:

true false

Default:true

[showValue](https://docs.evidence.dev/components/data/delta#props-showValue)

Whether to show the value. Set this to false to show only the delta arrow indicator.

Options:

true false

Default:true

[text](https://docs.evidence.dev/components/data/delta#props-text)

Text to display after the delta symbol and value

Options:string

[neutralMin](https://docs.evidence.dev/components/data/delta#props-neutralMin)

Start of the range for 'neutral' values, which appear in grey font with a dash instead of an up/down arrow. By default, neutral is not applied to any values.

Options:numberDefault:0

[neutralMax](https://docs.evidence.dev/components/data/delta#props-neutralMax)

End of the range for 'neutral' values, which appear in grey font with a dash instead of an up/down arrow. By default, neutral is not applied to any values.

Options:numberDefault:0

[chip](https://docs.evidence.dev/components/data/delta#props-chip)

Whether to display the delta as a 'chip', with a background color and border.

Options:

true false

Default:false

[symbolPosition](https://docs.evidence.dev/components/data/delta#props-symbolPosition)

Whether to display the delta symbol to the left or right of the value

Options:

left right

Default:right

[emptySet](https://docs.evidence.dev/components/data/delta#props-emptySet)

Sets behaviour for empty datasets. Can throw an error, a warning, or allow empty. When set to 'error', empty datasets will block builds in `build:strict`. Note this only applies to initial page load - empty datasets caused by input component changes (dropdowns, etc.) are allowed.

Options:

error warn pass

Default:error

[emptyMessage](https://docs.evidence.dev/components/data/delta#props-emptyMessage)

Text to display when an empty dataset is received - only applies when `emptySet` is 'warn' or 'pass', or when the empty dataset is a result of an input component change (dropdowns, etc.).

Options:stringDefault:No records

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/data/delta/index.md)