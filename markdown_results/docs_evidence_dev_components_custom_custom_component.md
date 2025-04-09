[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Custom](https://docs.evidence.dev/components/custom) [Custom Components](https://docs.evidence.dev/components/custom/custom-component)

# Custom Components

Custom components allow you to extend the functionality of Evidence, as well as to make your code more reusable.

In Evidence, you can build your own components and use them anywhere in your app. This is made possible through Svelte, the JavaScript framework Evidence is built on. These components can include the charts used for visualization, custom components created completely from scratch, or adaptations of existing UI components such as the header, sidebar, menu, etc.

Below is a **short guide** on building a simple component in Evidence.

For a fuller guide, Svelte offers a great interactive tutorial that you can complete in your browser in about an hour: [Svelte Tutorial](https://svelte.dev/tutorial/basics)

**Built a great component?**

Let us know in our [Slack community](https://slack.evidence.dev/)!

We'd love to see what you've built, and may add generally applicable components to the Evidence core component library!

## [Example custom component](https://docs.evidence.dev/components/custom/custom-component\#example-custom-component)

If you were creating a component called `<Hello />`, which included some text and a BarChart, to use in `index.md`, you could do so like this:

Add a folder called `components/` in the root of your project. This is where Evidence looks for your Svelte components:

### [Folder structure](https://docs.evidence.dev/components/custom/custom-component\#folder-structure)

```text-sm bash
.
|-- pages/
|   `-- index.md
`-- components/
    `-- Hello.svelte
```

`Hello.svelte` is your component. Add the following code to these two files:

### [File contents](https://docs.evidence.dev/components/custom/custom-component\#file-contents)

````text-sm html

```sql sales_by_country
select 'Canada' as country, 100 as sales_usd
union all
select 'USA' as country, 200 as sales_usd
union all
select 'UK' as country, 300 as sales_usd
```

<!-- To use data in the component, pass it to the component as a prop
     You can use multiple queries, and name the props anything you like -->
<Hello myData={sales_by_country} />
````

```text-sm html
<!-- To allow the component to accept data, you need to use the 'export let' syntax
     If you need any Evidence components inside your custom component, you must import them explicitly -->
<script>
	export let myData;
	import { BarChart } from '@evidence-dev/core-components';
</script>

<p>
	Here is a BarChart in a Component, with some accompanying text. Components stored in the
	/components/ folder will be included in your app.
</p>

<BarChart data={myData} />
```

## [Building your own component: Checklist](https://docs.evidence.dev/components/custom/custom-component\#building-your-own-component-checklist)

If you're building a component, here are some things to keep in mind.

In your markdown file:

1. **Pass any data as props** if you need to access query results in the component

In the custom component:

1. **Use Svelte (HTML + extra features) syntax** in this component - it will not support Markdown
2. **Use the `/components/` folder** for your .svelte files
3. **`export` any props you want to use** in the component
4. **Import any [Evidence components](https://github.com/evidence-dev/evidence/tree/main/sites/example-project/src/components)** you want to use in the custom component

## [Optional: Publishing Your Components as a Plugin](https://docs.evidence.dev/components/custom/custom-component\#optional-publishing-your-components-as-a-plugin)

If you have built custom components that you would like other Evidence users to be able to use in their apps, you can publish them as an Evidence plugin. See the [Plugin section](https://docs.evidence.dev/plugins/create-component-plugin) for more details.

## [Utility Functions](https://docs.evidence.dev/components/custom/custom-component\#utility-functions)

Evidence provides a collection of helpful utility functions to use within custom components, for things like error handling, data manipulation, and value formatting.

To use these utilities, you must import them explicitly in the script tag portion of your component. The import line for each utlity function is included for reference below:

### [Error Handling](https://docs.evidence.dev/components/custom/custom-component\#error-handling)

#### [checkInputs `checkInputs(data, reqCols, optCols)`](https://docs.evidence.dev/components/custom/custom-component\#checkinputs-checkinputsdata-reqcols-optcols)

Accepts a dataset and list of columns, and returns an error if the dataset is empty, required columns are missing, or referenced columns do not exist in the data

```text-sm javascript
import checkInputs from '@evidence-dev/component-utilities/checkInputs';
```

- `data`: the query result you need to check
- `reqCols`: a list of columns that are required for your component (e.g., x or y for a chart)
- `optCols`: a list of optional columns

#### [ErrorChart `<ErrorChart error={error} chartType="My Chart"/>`](https://docs.evidence.dev/components/custom/custom-component\#errorchart-lterrorchart-error123error125-charttypemy-chartgt)

A component used to display an error state on the page

```text-sm javascript
import { ErrorChart } from '@evidence-dev/core-components';
```

- `error`: the error message to display
- `chartType`: the title that appears at the top of the error component

### [Data Manipulation](https://docs.evidence.dev/components/custom/custom-component\#data-manipulation)

#### [getDistinctValues `getDistinctValues(data, column)`](https://docs.evidence.dev/components/custom/custom-component\#getdistinctvalues-getdistinctvaluesdata-column)

Returns an array of distinct values from a specified column in a dataset

```text-sm javascript
import getDistinctValues from '@evidence-dev/component-utilities/getDistinctValues';
```

- `data`: query result to pull the values from
- `column`: name of column to use

#### [getDistinctCount `getDistinctCount(data, column)`](https://docs.evidence.dev/components/custom/custom-component\#getdistinctcount-getdistinctcountdata-column)

Returns the count of distinct values in a column

```text-sm javascript
import getDistinctCount from '@evidence-dev/component-utilities/getDistinctCount';
```

- `data`: query result to pull the values from
- `column`: name of column to use

#### [getSortedData `getSortedData(data, col, isAsc)`](https://docs.evidence.dev/components/custom/custom-component\#getsorteddata-getsorteddatadata-col-isasc)

Returns the original dataset, sorted by the specific column and direction

```text-sm javascript
import getSortedData from '@evidence-dev/component-utilities/getSortedData';
```

- `data`: query result to pull the values from
- `col`: name of column to sort
- `isAsc`: if true, will sort ascending; otherwise, descending

#### [getColumnSummary `getColumnSummary(data, returnType = "object")`](https://docs.evidence.dev/components/custom/custom-component\#getcolumnsummary-getcolumnsummarydata-returntype--object)

Returns an object with information about each column (title, min, max, format, etc.)

```text-sm javascript
import getColumnSummary from '@evidence-dev/component-utilities/getColumnSummary';
```

- `data`: query result to summarize
- `returnType`: "object" or "array"

#### [getCompletedData `getCompletedData(data, x, y, series, nullsZero = false, fillX = false)`](https://docs.evidence.dev/components/custom/custom-component\#getcompleteddata-getcompleteddatadata-x-y-series-nullszero--false-fillx--false)

Returns the original dataset with rows filled in as needed to complete a continuous number series

```text-sm javascript
import getCompletedData from '@evidence-dev/component-utilities/getCompletedData';
```

- `data`: query result which requires completed data
- `x`: name of column for x-axis
- `y`: name of column for y-axis
- `series`: name of column for series
- `nullsZero`: if true, will treat nulls as zeroes; otherwise, will leave as nulls
- `fillX`: if true, will find the smallest increment in the x-axis values and create rows as needed to create a continous series

### [Value & Label Formatting](https://docs.evidence.dev/components/custom/custom-component\#value--label-formatting)

#### [formatValue `formatValue(value, columnFormat = undefined, columnUnitSummary = undefined)`](https://docs.evidence.dev/components/custom/custom-component\#formatvalue-formatvaluevalue-columnformat--undefined-columnunitsummary--undefined)

Returns a formatted value

```text-sm javascript
import { formatValue } from '@evidence-dev/component-utilities/formatting';
```

- `value`: value to format
- `columnFormat`: a format object for column being formatted (can be obtained from the `getColumnSummary` function)
- `columnUnitSummary`: an object containing the extents of the column, used for unit summary formatting like "M" or "B" (can be obtained from the `getColumnSummary` function)

#### [fmt `fmt(value, format)`](https://docs.evidence.dev/components/custom/custom-component\#fmt-fmtvalue-format)

Simpler version of the `formatValue` function which does not require a format object

```text-sm javascript
import { fmt } from '@evidence-dev/component-utilities/formatting';
```

- `value`: value to be formatted
- `format`: a string representing a format tag name or an Excel-style format code

#### [formatTitle `formatTitle(column, columnFormat)`](https://docs.evidence.dev/components/custom/custom-component\#formattitle-formattitlecolumn-columnformat)

Returns a formatted column title (with proper letter casing)

```text-sm javascript
import formatTitle from '@evidence-dev/component-utilities/formatTitle';
```

- `column`: name of column to be formatted
- `columnFormat`: a format object for column being formatted (can be obtained from the `getColumnSummary` function)

## [Adding Queries](https://docs.evidence.dev/components/custom/custom-component\#adding-queries)

Custom components can execute queries rather than requiring data to be passed to them. See [component queries](https://docs.evidence.dev/components/custom/component-queries) for details

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/custom/custom-component/index.md)