[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Date Input](https://docs.evidence.dev/components/inputs/date-input)

# Date Input

A date input component allows the user to select a date or a range of dates. The selected dates can be used as inputs to queries or components.

To see how to filter a query using an input component, see [Filters](https://docs.evidence.dev/core-concepts/filters).

preview

code

Sales After

Sales After

Jan 2, 2019 1/2/19

````text-sm markdown

```sql filtered_query
select
    *
from ${orders_by_day}
where day > '${inputs.range_filtering_a_query.value}'
```

<DateInput
    name=date_filtering_a_query
    data={orders_by_day}
    dates=day
/>

<BarChart
    data={filtered_query}
    x=day
    y=sales
/>
````

## [Examples](https://docs.evidence.dev/components/inputs/date-input\#examples)

### [Using Date Input from a Query](https://docs.evidence.dev/components/inputs/date-input\#using-date-input-from-a-query)

The Date selected can be accessed through the `inputs.[name].value`

preview

code

Jan 2, 2019 1/2/19

Date Selected: 2019-01-02

```text-sm markdown
<DateInput
    name=date_range_from_query
    data={orders_by_day}
    dates=day
/>

Date Selected: {inputs.date_input_from_query.value}
```

### [With a Title](https://docs.evidence.dev/components/inputs/date-input\#with-a-title)

preview

code

Select a Date Input

Select a Date Input

Jan 2, 2019 1/2/19

```text-sm markdown
<DateInput
    name=date_range_with_title
    data={orders_by_day}
    dates=day
    title="Select a Date Input"/>
```

## [Date Range](https://docs.evidence.dev/components/inputs/date-input\#date-range)

Creates a date picker for selecting a date range to filter queries, with selectable preset date options.

### [Filtering a Query with Range Calendar](https://docs.evidence.dev/components/inputs/date-input\#filtering-a-query-with-range-calendar)

The Date selected can be accessed through the `inputs.[name].start` & `inputs.[name].end`

preview

code

Date Range

Jan 2, 2019 - Dec 19, 20211/2/19 - 12/19/21Select a RangeRange

````text-sm markdown

```sql filtered_query_ranged
select
    *
from ${orders_by_day}
where day between '${inputs.range_filtering_a_query.start}' - '${inputs.range_filtering_a_query.end}'
```

<DateInput
    name=range_filtering_a_query
    data={orders_by_day}
    dates=day
    title='Date Range'
    range
/>

<LineChart
    data={filtered_query_ranged}
    x=day
    y=sales
/>
````

### [Default Value for Preset Ranges](https://docs.evidence.dev/components/inputs/date-input\#default-value-for-preset-ranges)

preview

code

Apr 3, 2025 - Apr 9, 20254/3/25 - 4/9/25Last 7 Days

```text-sm svelte
<DateInput
    name=name_of_date_range
    defaultValue={'Last 7 Days'}
    range
/>
```

### [Customizing Single Preset Ranges](https://docs.evidence.dev/components/inputs/date-input\#customizing-single-preset-ranges)

preview

code

Jan 1, 1970 - Apr 9, 20251/1/70 - 4/9/25Select a RangeRange

```text-sm svelte
<DateInput
    name="date_range_2"
    presetRanges={'Last 7 Days'}
    range
/>
```

### [Customizing Multiple Preset Ranges](https://docs.evidence.dev/components/inputs/date-input\#customizing-multiple-preset-ranges)

preview

code

Jan 1, 1970 - Apr 9, 20251/1/70 - 4/9/25Select a RangeRange

```text-sm svelte
<DateInput
    name="date_range_3"
    range
    presetRanges={['Last 7 Days', 'Last 3 Months', 'Year to Date', 'All Time']}
/>
```

### [Manually Specifying a Range](https://docs.evidence.dev/components/inputs/date-input\#manually-specifying-a-range)

preview

code

Jan 1, 2019 - Dec 31, 20191/1/19 - 12/31/19Select a RangeRange

```text-sm markdown
<DateInput
    name=manual_date_range
    start=2019-01-01
    end=2019-12-31
    range
/>
```

## [Options](https://docs.evidence.dev/components/inputs/date-input\#options)

[name](https://docs.evidence.dev/components/inputs/date-input#props-name)

Required

Name of the DateInput, used to reference the selected values elsewhere as {inputs.name.start or inputs.name.end

Options:string

[data](https://docs.evidence.dev/components/inputs/date-input#props-data)

Query name, wrapped in curly braces

Options:query name

[range](https://docs.evidence.dev/components/inputs/date-input#props-range)

toggles between a ranged and single input calendar

Options:

true false

[dates](https://docs.evidence.dev/components/inputs/date-input#props-dates)

Column name from the query containing Date Input to span

Options:column name

[start](https://docs.evidence.dev/components/inputs/date-input#props-start)

A manually specified start date to use for the range

Options:string formatted YYYY-MM-DD

[end](https://docs.evidence.dev/components/inputs/date-input#props-end)

A manually specified end date to use for the range

Options:string formatted YYYY-MM-DD

[title](https://docs.evidence.dev/components/inputs/date-input#props-title)

Title to display in the Date Input component

Options:string

[presetRanges](https://docs.evidence.dev/components/inputs/date-input#props-presetRanges)

Customize "Select a Range" drop down, by including present range options. **Range options**: `'Last 7 Days'` `'Last 30 Days'` `'Last 90 Days'` `'Last 3 Months'` `'Last 6 Months'` `'Last 12 Months'` `'Last Month'` `'Last Year'` `'Month to Date'` `'Year to Date'` `'All Time'`

Options:string \| array of values e.g. {\['Last 7 Days', 'Last 30 Days'\]}

[defaultValue](https://docs.evidence.dev/components/inputs/date-input#props-defaultValue)

Accepts preset in string format to apply default value in Date Input picker. **Range options**: `'Last 7 Days'` `'Last 30 Days'` `'Last 90 Days'` `'Last 3 Months'` `'Last 6 Months'` `'Last 12 Months'` `'Last Month'` `'Last Year'` `'Month to Date'` `'Year to Date'` `'All Time'`

Options:string e.g. Last 7 Days or Last 6 Months

[hideDuringPrint](https://docs.evidence.dev/components/inputs/date-input#props-hideDuringPrint)

Hide the component when the report is printed

Options:

true false

[description](https://docs.evidence.dev/components/inputs/date-input#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/date-input/index.md)