[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Loops](https://docs.evidence.dev/core-concepts/loops)

# Loops

Create repeating elements by looping through data with `{#each}` blocks. Note that curly braces `{...}` execute JavaScript expressions in Evidence.

## [Each Loops](https://docs.evidence.dev/core-concepts/loops\#each-loops)

Loops enable you to iterate over the rows in a query result, and reference the row using an alias of your choosing. They are similar to for loops in Python.

```text-sm markdown
{#each query_name as alias}

{alias.column_name}

{/each}
```

If you have more content than you would like to loop over on a single page, consider using a [templated page](https://docs.evidence.dev/core-concepts/templated-pages).

## [Example](https://docs.evidence.dev/core-concepts/loops\#example)

Imagine you were creating a report on the performance of your organization's cities. You could use a loop to generate a section of your report for each city. When a new city appears in your query results, a new section will appear in your report.

The following table is being returned by the query `location_summary`

|  |  |  |
| --- | --- | --- |
| name | sales\_usd | gross\_margin\_pct |
| --- | --- | --- |
| New York | 9,000 | 0.60 |
| Los Angeles | 5,000 | 0.45 |
| Toronto | 4,000 | 0.70 |

No Results

|  |  |  |
| --- | --- | --- |
| name | sales\_usd | gross\_margin\_pct |
| --- | --- | --- |
| New York | 9,000 | 0.60 |
| Los Angeles | 5,000 | 0.45 |
| Toronto | 4,000 | 0.70 |

No Results

By using an `{#each}` block, we can iterate over each of the rows in `location_summary`, and reference the current row with the alias `city`. Here we'll create a header, and a paragraph for each of the three locations.

```text-sm markdown
Daily sales:

{#each location_summary as city}

## {city.name}

<Value data={city} column=sales_usd/> in sales at a <Value data={city} column=gross_margin_pct/> gross margin.

{/each}
```

Which would result in the following output

> Daily sales:
>
> **New York**
>
> $9,000 in sales at a 60% gross margin.
>
> **Los Angeles**
>
> $5,000 in sales at a 45% gross margin.
>
> **Toronto**
>
> $4,000 in sales at a 70% gross margin.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/loops/index.md)