[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Filters](https://docs.evidence.dev/core-concepts/filters)

# Filters

Filters dynamically change what data is returned by a query. Filters take the input that a user provides via a component, and use it to change the query.

The below example uses the Evidence [`<Dropdown/>`](https://docs.evidence.dev/components/inputs/dropdown) component.

## [Examples](https://docs.evidence.dev/core-concepts/filters\#examples)

### [Filtering a query with a dropdown](https://docs.evidence.dev/core-concepts/filters\#filtering-a-query-with-a-dropdown)

![Filtering a Query](https://docs.evidence.dev/img/filters-queries.png)

````text-sm markdown
```sql unique_items
select
    item
from needful_things.orders
group by 1
```

<Dropdown
    name=selected_item
    data={unique_items}
    value=item
/>

```sql orders_by_month
select
    date_trunc('month', order_date) as month,
    sum(sales) as sales_usd
from needful_things.orders
where item = '${inputs.selected_item.value}'
group by 1
```

<BarChart
    data={orders_by_month}
    x=month
    y=sales_usd
/>
````

## [Filtering a query with a default value](https://docs.evidence.dev/core-concepts/filters\#filtering-a-query-with-a-default-value)

![Filtering a Query](https://docs.evidence.dev/img/filters-default.png)

The `%` character can be used as a wildcard in SQL. It will return all items when the user selects "All Items" from this dropdown.

Note also the use of the `like` operator in the `where` clause.

````text-sm markdown
```sql items
select
    item
from needful_things.orders
group by 1
```

<Dropdown
    name=selected_item
    data={unique_items}
    value=item
>
    <DropdownOption value="%" valueLabel="All Items"/>
</Dropdown>

```sql orders_by_month
select
    date_trunc('month', order_date) as month,
    sum(sales) as sales_usd
from needful_things.orders
where item like '${inputs.selected_item.value}'
group by 1
```

<BarChart
    data={orders_by_month}
    x=month
    y=sales_usd
/>
````

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/filters/index.md)