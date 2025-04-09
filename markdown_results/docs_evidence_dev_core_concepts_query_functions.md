[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Query Functions](https://docs.evidence.dev/core-concepts/query-functions)

# Query Functions

Query functions allow you to operate on query results with SQL-like syntax.

**Warning**

Query functions are experimental and may change in the future

The supported query functions are:

- [`.where()`](https://docs.evidence.dev/core-concepts/query-functions#where)
- [`.groupBy()`](https://docs.evidence.dev/core-concepts/query-functions#groupby)
- [`.limit()`](https://docs.evidence.dev/core-concepts/query-functions#limit)
- [`.offset()`](https://docs.evidence.dev/core-concepts/query-functions#offset)
- [`.agg()`](https://docs.evidence.dev/core-concepts/query-functions#agg)

## [Where](https://docs.evidence.dev/core-concepts/query-functions\#where)

``.where(`sqlStatement`)``

Filters rows in the query based on the provided condition.

```text-sm markdown
<DataTable data={orders.where(`sales > 100`)} />
```

#### [Parameters](https://docs.evidence.dev/core-concepts/query-functions\#parameters)

[sqlStatement](https://docs.evidence.dev/core-concepts/query-functions#props-sqlStatement)

Required

A SQL-like condition to filter rows, must be wrapped in backticks.

### [Iterating through a query](https://docs.evidence.dev/core-concepts/query-functions\#iterating-through-a-query)

````text-sm markdown
```sql categories
SELECT DISTINCT category FROM orders
```

```sql orders_by_category
SELECT
    category,
    item,
    sum(sales) as total_sales
FROM orders
group by all
```

{#each categories as category}

    <BarChart data={orders_by_category.where(`category = '${category}'`)} />

{/each}
````

Example Output

## [GroupBy](https://docs.evidence.dev/core-concepts/query-functions\#groupby)

`.groupBy([columns], withRowCount = true)`

Groups rows by the specified columns and optionally includes a row count.

```text-sm markdown
<DataTable data={orders.groupBy(["category", "item"])} />
```

#### [Parameters](https://docs.evidence.dev/core-concepts/query-functions\#parameters-1)

[columns](https://docs.evidence.dev/core-concepts/query-functions#props-columns)

Required

The columns to group by.

[withRowCount](https://docs.evidence.dev/core-concepts/query-functions#props-withRowCount)

Whether to include a \`rows\` column indicating the count of rows in each group.

## [Limit](https://docs.evidence.dev/core-concepts/query-functions\#limit)

`.limit(limit)`

Limits the number of rows returned by the query.

```text-sm markdown
<DataTable data={orders.limit(5)} />
```

#### [Parameters](https://docs.evidence.dev/core-concepts/query-functions\#parameters-2)

[limit](https://docs.evidence.dev/core-concepts/query-functions#props-limit)

Required

Maximum number of rows.

## [Offset](https://docs.evidence.dev/core-concepts/query-functions\#offset)

`.offset(offset)`

Skips a specified number of rows in the query result.

```text-sm markdown
<DataTable data={orders.offset(20)} />
```

#### [Parameters](https://docs.evidence.dev/core-concepts/query-functions\#parameters-3)

[offset](https://docs.evidence.dev/core-concepts/query-functions#props-offset)

Required

Number of rows to skip.

## [Agg](https://docs.evidence.dev/core-concepts/query-functions\#agg)

`.agg({aggObj})`

Adds aggregation operations to the query (e.g., `sum`, `avg`, `min`, `max`, `median`). Used in conjunction with [`groupBy`](https://docs.evidence.dev/core-concepts/query-functions#groupby).

```text-sm markdown
<DataTable
    data={orders.groupBy(["category", "item"]).agg({sum: "sales"})}
/>
```

#### [Parameters](https://docs.evidence.dev/core-concepts/query-functions\#parameters-4)

[aggObj](https://docs.evidence.dev/core-concepts/query-functions#props-aggObj)

Required

Configuration object where keys are aggregation functions ( `sum`, `avg`, `min`, `max`, `median`) and values are column specifications.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/query-functions/index.md)