[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Date Range](https://docs.evidence.dev/components/inputs/date-range)

# Date Range

Creates a date picker that can be used to filter a query.
Includes a set of preset ranges for quick selection of common date ranges. These are relative to the supplied end date.

To see how to filter a query using an input component, see [Filters](https://docs.evidence.dev/core-concepts/filters).

preview

code

Jan 2, 2019 - Dec 19, 20211/2/19 - 12/19/21Select a RangeRange

From 2019-01-02 to 2021-12-19

```text-sm markdown
<DateRange
    name=date_range_name
    data={orders_by_day}
    dates=day
/>

From {inputs.date_range_name.start} to {inputs.date_range_name.end}
```

## [Examples](https://docs.evidence.dev/components/inputs/date-range\#examples)

### [Using Date Range from a Query](https://docs.evidence.dev/components/inputs/date-range\#using-date-range-from-a-query)

preview

code

Jan 2, 2019 - Dec 19, 20211/2/19 - 12/19/21Select a RangeRange

From 2019-01-02 to 2021-12-19

```text-sm markdown
<DateRange
    name=date_range_from_query
    data={orders_by_day}
    dates=day
/>

From {inputs.date_range_from_query.start} to {inputs.date_range_from_query.end}
```

### [Manually Specifying a Range](https://docs.evidence.dev/components/inputs/date-range\#manually-specifying-a-range)

preview

code

Jan 1, 2019 - Dec 31, 20191/1/19 - 12/31/19Select a RangeRange

```text-sm markdown
<DateRange
    name=manual_date_range
    start=2019-01-01
    end=2019-12-31
/>
```

### [With a Title](https://docs.evidence.dev/components/inputs/date-range\#with-a-title)

preview

code

Select a Date Range

Jan 2, 2019 - Dec 19, 20211/2/19 - 12/19/21Select a RangeRange

```text-sm markdown
<DateRange
    name=date_range_with_title
    data={orders_by_day}
    dates=day
    title="Select a Date Range"
/>
```

### [Visible During Print / Export](https://docs.evidence.dev/components/inputs/date-range\#visible-during-print--export)

preview

code

Jan 2, 2019 - Dec 19, 20211/2/19 - 12/19/21Select a RangeRange

```text-sm markdown
<DateRange
    name=date_range_visible_during_print
    data={orders_by_day}
    dates=day
    hideDuringPrint={false}
/>
```

### [Filtering a Query](https://docs.evidence.dev/components/inputs/date-range\#filtering-a-query)

preview

code

Jan 2, 2019 - Dec 19, 20211/2/19 - 12/19/21Select a RangeRange

````text-sm markdown
<DateRange
    name=range_filtering_a_query
    data={orders_by_day}
    dates=day
/>

```sql filtered_query
select
    *
from ${orders_by_day}
where day between '${inputs.range_filtering_a_query.start}' and '${inputs.range_filtering_a_query.end}'
```

<LineChart
    data={filtered_query}
    x=day
    y=sales
/>
````

### [Customizing Single Preset Ranges](https://docs.evidence.dev/components/inputs/date-range\#customizing-single-preset-ranges)

preview

code

Jan 1, 1970 - Apr 9, 20251/1/70 - 4/9/25Select a RangeRange

```text-sm svelte
<DateRange
    name="date_range_preset"
    presetRanges={'Last 7 Days'}
/>
```

### [Customizing Multiple Preset Ranges](https://docs.evidence.dev/components/inputs/date-range\#customizing-multiple-preset-ranges)

preview

code

Jan 1, 1970 - Apr 9, 20251/1/70 - 4/9/25Select a RangeRange

```text-sm svelte
<DateRange
    name="date_range_preset_2"
    presetRanges={['Last 7 Days', 'Last 3 Months', 'Year to Date', 'All Time']}
/>
```

### [Default Value for Preset Ranges](https://docs.evidence.dev/components/inputs/date-range\#default-value-for-preset-ranges)

preview

code

Apr 3, 2025 - Apr 9, 20254/3/25 - 4/9/25Last 7 Days

```text-sm svelte
<DateRange
    name="date_range_preset_3"
    defaultValue={'Last 7 Days'}
/>
```

## [Options](https://docs.evidence.dev/components/inputs/date-range\#options)

[name](https://docs.evidence.dev/components/inputs/date-range#props-name)

Required

Name of the DateRange, used to reference the selected values elsewhere as {inputs.name.start or inputs.name.end

Options:string

[data](https://docs.evidence.dev/components/inputs/date-range#props-data)

Query name, wrapped in curly braces

Options:query name

[dates](https://docs.evidence.dev/components/inputs/date-range#props-dates)

Column name from the query containing date range to span

Options:column name

[start](https://docs.evidence.dev/components/inputs/date-range#props-start)

A manually specified start date to use for the range

Options:string formatted YYYY-MM-DD

[end](https://docs.evidence.dev/components/inputs/date-range#props-end)

A manually specified end date to use for the range

Options:string formatted YYYY-MM-DD

[title](https://docs.evidence.dev/components/inputs/date-range#props-title)

Title to display in the Date Range component

Options:string

[presetRanges](https://docs.evidence.dev/components/inputs/date-range#props-presetRanges)

Customize "Select a Range" drop down, by including present range options. **Range options**: `'Last 7 Days'` `'Last 30 Days'` `'Last 90 Days'` `'Last 365 Days'` `'Last 3 Months'` `'Last 6 Months'` `'Last 12 Months'` `'Last Month'` `'Last Year'` `'Month to Date'` `'Month to Today'` `'Year to Date'` `'Year to Today'` `'All Time'`

Options:string \| array of values e.g. {\['Last 7 Days', 'Last 30 Days'\]}

[defaultValue](https://docs.evidence.dev/components/inputs/date-range#props-defaultValue)

Accepts preset in string format to apply default value in Date Range picker. **Range options**: `'Last 7 Days'` `'Last 30 Days'` `'Last 90 Days'` `'Last 365 Days'` `'Last 3 Months'` `'Last 6 Months'` `'Last 12 Months'` `'Last Month'` `'Last Year'` `'Month to Date'` `'Month to Today'` `'Year to Date'` `'Year to Today'` `'All Time'`

Options:string e.g. Last 7 Days or Last 6 Months

[hideDuringPrint](https://docs.evidence.dev/components/inputs/date-range#props-hideDuringPrint)

Hide the component when the report is printed

Options:

true false

[description](https://docs.evidence.dev/components/inputs/date-range#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/date-range/index.md)