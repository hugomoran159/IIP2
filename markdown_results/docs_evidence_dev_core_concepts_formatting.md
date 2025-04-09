[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Value Formatting](https://docs.evidence.dev/core-concepts/formatting)

# Value Formatting

The easiest way to format numbers and dates in Evidence is through component props. You can pass in any of the following:

- [Excel-style format codes](https://docs.evidence.dev/core-concepts/formatting#excel-format-codes) (e.g., `fmt='$#,##0.0'`)
- Evidence's [built-in formats](https://docs.evidence.dev/core-concepts/formatting#built-in-formats) (e.g., `fmt=usd2k`)
- [Custom defined formats](https://docs.evidence.dev/core-concepts/formatting#custom-formats)

For example, you can use the `fmt` prop to format values inside a Value component:

```text-sm html
<Value data={sales_data} column=sales fmt='$#,##0' />
```

Within charts, you can format individual columns using `xFmt` and `yFmt` (and `sizeFmt` for bubble charts):

```text-sm html
<LineChart
    data={sales_data}
    x=date
    y=sales
    xFmt="m/d"
    yFmt="eur"
/>
```

In the example above, `xFmt` is passing in an Excel-style code to format the dates and `yFmt` is referencing a built-in format ( [see the full list](https://docs.evidence.dev/core-concepts/formatting#built-in-formats) of supported tags below, or [create your own](https://docs.evidence.dev/core-concepts/formatting#custom-formats)).

**Date formatting**

Formatting does not apply to the date axis of a chart. For example, if you set `xFmt` to `m/d/yy`, you will only see that formatting reflected in your chart tooltips and annotations. This is to ensure that the chart axis labels have the correct spacing.

#### [Reusable Formats](https://docs.evidence.dev/core-concepts/formatting\#reusable-formats)

For a more reusable approach, you can use [SQL format tags](https://docs.evidence.dev/core-concepts/formatting#sql-format-tags), which let you define formats within your SQL. This guarantees that your columns will be formatted in the same way wherever they are used in Evidence.

You can also create your own [custom formats](https://docs.evidence.dev/core-concepts/formatting#custom-formats), which are format codes you can reuse across your project.

#### [Formatting Directly in Markdown](https://docs.evidence.dev/core-concepts/formatting\#formatting-directly-in-markdown)

If you need to format values outside of components, [the format function](https://docs.evidence.dev/core-concepts/formatting#format-function) can be used directly. For example, when using [expressions](https://docs.evidence.dev/core-concepts/syntax#expressions) it is not possible to use component props or format tags.

## [Excel Format Codes](https://docs.evidence.dev/core-concepts/formatting\#excel-format-codes)

Evidence supports [Excel-style custom format codes](https://support.microsoft.com/en-us/office/number-format-codes-5026bbd6-04bc-48cd-bf33-80f18b4eae68), which can be passed directly to a component prop, the [format function](https://docs.evidence.dev/core-concepts/formatting#format-function), or saved as a [custom format code](https://docs.evidence.dev/core-concepts/formatting#custom-formats) that you want to reuse.

**Strings inside formats codes**

Some Excel format codes include strings: use double-quotes for the string, and single-quotes to surround the whole format code.

E.g., `fmt = '#,##0.00 "mpg"'`

## [Built-in Formats](https://docs.evidence.dev/core-concepts/formatting\#built-in-formats)

Evidence supports a variety of date/time, number, percentage, and currency formats. You can find the full list of formats below.

### [Auto-Formatting](https://docs.evidence.dev/core-concepts/formatting\#auto-formatting)

Wherever you see `auto` listed beside a format, that means Evidence will automatically format your value based on the context it is in.

For example, Evidence automatically formats large numbers into shortened versions based on the size of the median number in a column (e.g., 4,000,000 → 4M).

You can choose to handle these numbers differently by choosing a specific format code. For example, if Evidence is formatting a column as millions, but you want to see all numbers in thousands, you could use the `num0k` format, which will show all numbers in the column in thousands with 0 decimal places.

### [Dates](https://docs.evidence.dev/core-concepts/formatting\#dates)

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| ddd | ddd | 2022-01-09 12:45 | Sun |
| dddd | dddd | 2022-01-09 12:45 | Sunday |
| mmm | mmm | 2022-01-09 12:45 | Jan |
| mmmm | mmmm | 2022-01-09 12:45 | January |
| yyyy | yyyy | 2022-01-09 12:45 | 2022 |
| shortdate | mmm d/yy | 2022-01-09 12:45 | Jan 9/22 |
| longdate | mmmm d, yyyy | 2022-01-09 12:45 | January 9, 2022 |
| fulldate | dddd mmmm d, yyyy | 2022-01-09 12:45 | Sunday January 9, 2022 |
| mdy | m/d/y | 2022-01-09 12:45 | 1/9/22 |
| dmy | d/m/y | 2022-01-09 12:45 | 9/1/22 |
| hms | H:MM:SS AM/PM | 2022-01-09 12:45 | 11:45:03 AM |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| ddd | ddd | 2022-01-09 12:45 | Sun |
| dddd | dddd | 2022-01-09 12:45 | Sunday |
| mmm | mmm | 2022-01-09 12:45 | Jan |
| mmmm | mmmm | 2022-01-09 12:45 | January |
| yyyy | yyyy | 2022-01-09 12:45 | 2022 |
| shortdate | mmm d/yy | 2022-01-09 12:45 | Jan 9/22 |
| longdate | mmmm d, yyyy | 2022-01-09 12:45 | January 9, 2022 |
| fulldate | dddd mmmm d, yyyy | 2022-01-09 12:45 | Sunday January 9, 2022 |
| mdy | m/d/y | 2022-01-09 12:45 | 1/9/22 |
| dmy | d/m/y | 2022-01-09 12:45 | 9/1/22 |
| hms | H:MM:SS AM/PM | 2022-01-09 12:45 | 11:45:03 AM |

No Results

### [Currencies](https://docs.evidence.dev/core-concepts/formatting\#currencies)

Supported currencies:

|  |  |
| --- | --- |
| Code | Currency |
| --- | --- |
| usd | United States Dollar |
| aud | Australian Dollar |
| brl | Brazilian Real |
| cad | Canadian Dollar |
| cny | Renminbi |
| eur | Euro |
| gbp | Pound Sterling |
| jpy | Japanese Yen |
| inr | Indian Rupee |
| krw | South Korean Won |
| ngn | Nigerian Naira |
| rub | Russian Ruble |
| sek | Swedish Krona |

No Results

|  |  |
| --- | --- |
| Code | Currency |
| --- | --- |
| usd | United States Dollar |
| aud | Australian Dollar |
| brl | Brazilian Real |
| cad | Canadian Dollar |
| cny | Renminbi |
| eur | Euro |
| gbp | Pound Sterling |
| jpy | Japanese Yen |
| inr | Indian Rupee |
| krw | South Korean Won |
| ngn | Nigerian Naira |
| rub | Russian Ruble |
| sek | Swedish Krona |

No Results

In order to use currency tags, use the currency code, optionally appended with:

- a number indicating the number of decimal places to show (0-2)
- a letter indication the order of magnitude to show ("","k", "m", "b")

For example, the available tags for USD are:

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| usd | auto | 412.17 | $412 |
| usd0 | $#,##0 | 7043.123 | $7,043 |
| usd1 | $#,##0.0 | 7043.123 | $7,043.1 |
| usd2 | $#,##0.00 | 7043.123 | $7,043.12 |
| usd0k | $#,##0,"k" | 64301.12 | $64k |
| usd1k | $#,##0.0,"k" | 64301.12 | $64.3k |
| usd2k | $#,##0.00,"k" | 64301.12 | $64.30k |
| usd0m | $#,##0,,"M" | 4564301.12 | $5M |
| usd1m | $#,##0.0,,"M" | 4564301.12 | $4.6M |
| usd2m | $#,##0.00,,"M" | 4564301.12 | $4.56M |
| usd0b | $#,##0,,,"B" | 9784564301.12 | $10B |
| usd1b | $#,##0.0,,,"B" | 9784564301.12 | $9.8B |
| usd2b | $#,##0.00,,,"B" | 9784564301.12 | $9.78B |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| usd | auto | 412.17 | $412 |
| usd0 | $#,##0 | 7043.123 | $7,043 |
| usd1 | $#,##0.0 | 7043.123 | $7,043.1 |
| usd2 | $#,##0.00 | 7043.123 | $7,043.12 |
| usd0k | $#,##0,"k" | 64301.12 | $64k |
| usd1k | $#,##0.0,"k" | 64301.12 | $64.3k |
| usd2k | $#,##0.00,"k" | 64301.12 | $64.30k |
| usd0m | $#,##0,,"M" | 4564301.12 | $5M |
| usd1m | $#,##0.0,,"M" | 4564301.12 | $4.6M |
| usd2m | $#,##0.00,,"M" | 4564301.12 | $4.56M |
| usd0b | $#,##0,,,"B" | 9784564301.12 | $10B |
| usd1b | $#,##0.0,,,"B" | 9784564301.12 | $9.8B |
| usd2b | $#,##0.00,,,"B" | 9784564301.12 | $9.78B |

No Results

### [Numbers](https://docs.evidence.dev/core-concepts/formatting\#numbers)

The default number format (when no `fmt` is specified) automatically handles decimal places and summary units (in the same way that `usd` does for currency).

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| num0 | #,##0 | 11.23168 | 11 |
| num1 | #,##0.0 | 11.23168 | 11.2 |
| num2 | #,##0.00 | 11.23168 | 11.23 |
| num3 | #,##0.000 | 11.23168 | 11.232 |
| num4 | #,##0.0000 | 11.23168 | 11.2317 |
| num0k | #,##0,"k" | 64201 | 64k |
| num1k | #,##0.0,"k" | 64201 | 64.2k |
| num2k | #,##0.00,"k" | 64201 | 64.20k |
| num0m | #,##0,,"M" | 42539483 | 43M |
| num1m | #,##0.0,,"M" | 42539483 | 42.5M |
| num2m | #,##0.00,,"M" | 42539483 | 42.54M |
| num0b | #,##0,,,"B" | 1384937584 | 1B |
| num1b | #,##0.0,,,"B" | 1384937584 | 1.4B |
| num2b | #,##0.00,,,"B" | 1384937584 | 1.38B |
| id | 0 | 921594675 | 921594675 |
| fract | \# ?/? | 0.25 | 1/4 |
| mult | #,##0.0"x" | 5.32 | 5.3x |
| mult0 | #,##0"x" | 5.32 | 5x |
| mult1 | #,##0.0"x" | 5.32 | 5.3x |
| mult2 | #,##0.00"x" | 5.32 | 5.32x |
| sci | 0.00E+0 | 16546.1561 | 1.65E+4 |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| num0 | #,##0 | 11.23168 | 11 |
| num1 | #,##0.0 | 11.23168 | 11.2 |
| num2 | #,##0.00 | 11.23168 | 11.23 |
| num3 | #,##0.000 | 11.23168 | 11.232 |
| num4 | #,##0.0000 | 11.23168 | 11.2317 |
| num0k | #,##0,"k" | 64201 | 64k |
| num1k | #,##0.0,"k" | 64201 | 64.2k |
| num2k | #,##0.00,"k" | 64201 | 64.20k |
| num0m | #,##0,,"M" | 42539483 | 43M |
| num1m | #,##0.0,,"M" | 42539483 | 42.5M |
| num2m | #,##0.00,,"M" | 42539483 | 42.54M |
| num0b | #,##0,,,"B" | 1384937584 | 1B |
| num1b | #,##0.0,,,"B" | 1384937584 | 1.4B |
| num2b | #,##0.00,,,"B" | 1384937584 | 1.38B |
| id | 0 | 921594675 | 921594675 |
| fract | \# ?/? | 0.25 | 1/4 |
| mult | #,##0.0"x" | 5.32 | 5.3x |
| mult0 | #,##0"x" | 5.32 | 5x |
| mult1 | #,##0.0"x" | 5.32 | 5.3x |
| mult2 | #,##0.00"x" | 5.32 | 5.32x |
| sci | 0.00E+0 | 16546.1561 | 1.65E+4 |

No Results

### [Percentages](https://docs.evidence.dev/core-concepts/formatting\#percentages)

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| pct | auto | 0.731 | 73.1% |
| pct0 | #,##0% | 0.731 | 73% |
| pct1 | #,##0.0% | 0.731 | 73.1% |
| pct2 | #,##0.00% | 0.731 | 73.10% |
| pct3 | #,##0.000% | 0.731 | 73.100% |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| Format Name | Format Code | Example Input | Example Output |
| --- | --- | --- | --- |
| pct | auto | 0.731 | 73.1% |
| pct0 | #,##0% | 0.731 | 73% |
| pct1 | #,##0.0% | 0.731 | 73.1% |
| pct2 | #,##0.00% | 0.731 | 73.10% |
| pct3 | #,##0.000% | 0.731 | 73.100% |

No Results

## [Custom Formats](https://docs.evidence.dev/core-concepts/formatting\#custom-formats)

Custom formats can be added in the Value Formatting Section of the Evidence Settings.

With custom formats, you define the format you want to use (using [Excel style custom format codes](https://support.microsoft.com/en-us/office/number-format-codes-5026bbd6-04bc-48cd-bf33-80f18b4eae68)), and give the format a name (e.g., `mydate`). That format name will now be accessible in any place you can format your data in Evidence. For example:

```text-sm html
<Value data={sales_data} column=date fmt=mydate />
```

## [SQL Format Tags](https://docs.evidence.dev/core-concepts/formatting\#sql-format-tags)

SQL format tags let you define formats for your columns within your SQL query. This ensures that columns are formatted in the same way wherever they are used.

A **format tag** is appended to your column name with an underscore: for example, to append the percentage format to a column named `growth`, it would be `growth_pct`.

Formatting can be configured in the Value Formatting Section of the Evidence Settings.

Format tags are case-insensitive, so `growth_pct` and `GROWTH_PCT` are equivalent.

### [Title Formatting](https://docs.evidence.dev/core-concepts/formatting\#title-formatting)

When creating a table, Evidence formats column titles based on the name of the column and its format tag. Format tags that do not add to the meaning of the column name are not printed as part of the title. All columns are printed with proper casing.

#### [Examples](https://docs.evidence.dev/core-concepts/formatting\#examples)

|  |  |
| --- | --- |
| Column Name | Formatted Title |
| --- | --- |
| sales\_usd | Sales ($) |
| customer\_id | Customer ID |
| growth\_pct | Growth |
| customer\_number\_num2k | Customer Number |

No Results

|  |  |
| --- | --- |
| Column Name | Formatted Title |
| --- | --- |
| sales\_usd | Sales ($) |
| customer\_id | Customer ID |
| growth\_pct | Growth |
| customer\_number\_num2k | Customer Number |

No Results

## [Format Function](https://docs.evidence.dev/core-concepts/formatting\#format-function)

The format function is used to format expressions within markdown. This is useful when you cannot use a component.

The syntax is:

```text-sm javascript
{fmt(expression, formatCode)}
```

`formatCode` can be any one of the following:

- An Excel-style format code (e.g., `$#,##0.0`)
- A built-in Evidence format (e.g., `eur`)
- A custom-defined format code (see section above on custom formats)

### [Example](https://docs.evidence.dev/core-concepts/formatting\#example)

In the below example, we return a value from a calculation. In this situtation we cannot use the `Value` component, which only accepts a single row. Instead we use the `Format` function to format the result.

````text-sm markdown
```sql sales_per_year
select
    date_part('year', order_datetime) AS year,
    sum(sales) AS total_sales
from needful_things.orders
group by year
order by year desc
```

Sales are {fmt(sales_per_year[0].total_sales - sales_per_year[1].total_sales, '+#,##0;-#,##0')} vs last year.
````

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/formatting/index.md)