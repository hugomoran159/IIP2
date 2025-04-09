[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Templated Pages](https://docs.evidence.dev/core-concepts/templated-pages)

# Templated Pages

Templated pages allow you to use a single markdown file as a template for many pages with different data. For example:

1. `customers/[customer].md` -\> One page per customer
2. `countries/[country].md` -\> One page per country
3. `weekly-reports/week-[week_num].md` -\> One page per time period
4. `categories/[category]/[product].md` -\> One page per product [nested](https://docs.evidence.dev/core-concepts/templated-pages#nesting-templated-pages) in its category

In example 1 above, [www.example.com/customers/acme](http://www.example.com/customers/acme) would display information for Acme, while [www.example.com/customers/contoso](http://www.example.com/customers/contoso) would display information for Contoso.

A useful reference can be found in the [Needful Things example app](https://github.com/evidence-dev/demo/tree/main/pages/operations/pick_lists).

## [Quickstart: VS Code Extension](https://docs.evidence.dev/core-concepts/templated-pages\#quickstart-vs-code-extension)

1. **Create a [SQL file query](https://docs.evidence.dev/core-concepts/queries#sql-file-queries) in your queries folder**. It should return:
   - **One row per page** you want to generate
   - **A column containing a unique name or id** for each page
   - **Other columns containing data you want** to use in the pages
2. **Run `Evidence: Create Templated Pages from Query`** in the the Command Palette (Ctrl/Cmd+Shift+P).
3. **Enter the column name that contains your unique id** into the box that appears.

Evidence will automatically create a templated page that changes for each unique id, and an index page containing links for each page.

E.g. if your query was called `customers.sql` and contained a unique column called `customer` then the following files would be created:

```text-sm code
pages/
`-- customers/
    |-- [customer].md
    `-- index.md
```

This serves as a helpful starting point, and you will likely want to customize the code in the newly created files.

## [Full Guide of Concepts](https://docs.evidence.dev/core-concepts/templated-pages\#full-guide-of-concepts)

### [Declaring a templated page](https://docs.evidence.dev/core-concepts/templated-pages\#declaring-a-templated-page)

A templated page is created by adding square brackets round a file name `[parameter_name].md` or folder name `[parameter_name]`.
The following are equivalent:

- `pages/customers/[customer].md`
- `pages/customers/[customer]/index.md`

The string inside the square brackets becomes a [parameter](https://docs.evidence.dev/core-concepts/templated-pages#using-page-parameters) you can reference in the page, with the parameter value as text that replaces the parameter name in the URL.

### [Using page parameters](https://docs.evidence.dev/core-concepts/templated-pages\#using-page-parameters)

The parameter passed in the URL can be used in the page. For example, if the URL is `/customers/acme`, the parameter value is `acme`, and you access it in markdown as follows:

```text-sm javascript
{params.customer}
```

Parameters can be used in queries to filter query results (e.g. a for specific customer)

````text-sm sql
```sql customers
select
    sum(sales) as sales_usd
from needful_things.orders
where first_name = '${params.customer}'
group by 1
```
````

Adding this to a `<Value/>` component:

```text-sm javascript
<Value
    data={customers}
    column=sales_usd
/>
```

### [Generating templated pages](https://docs.evidence.dev/core-concepts/templated-pages\#generating-templated-pages)

So far, we've created the template for a set of pages, but haven't specified what specific pages to create, or to put it another way, what values we want the parameter to take.

For a page to be built, there must be links to it somewhere in your app.

Whilst you could add markdown style links for each parameter value, it is easier to programmatically generate them. Two easy options are:

#### [1\. With a `<DataTable/>` and the `link` prop](https://docs.evidence.dev/core-concepts/templated-pages\#1-with-a-ltdatatablegt-and-the-link-prop)

Create a link per row in the SQL query and pass it to the `<DataTable/>`.

````text-sm markdown
```sql customers
select
    customer_name,
    '/customers/' || customer_name as customer_link,
    sum(sales) as sales_usd
from needful_things.orders
group by 1
```

<DataTable
    data={customers}
    link=customer_link
/>
````

#### [2\. With an `{\#each}` loop](https://docs.evidence.dev/core-concepts/templated-pages\#2-with-an-123each125-loop)

````text-sm markdown
```sql customers
select
    customer_name,
    sum(sales) as sales_usd
from needful_things.orders
group by 1
```

{#each customers as customer}

- [{customer.customer_name}](/customers/{customer.customer_name})

{/each}
````

### [Nesting templated pages](https://docs.evidence.dev/core-concepts/templated-pages\#nesting-templated-pages)

Creating folders with parameters can be useful when nesting inside templated pages:

```text-sm bash
pages/
`-- customers/
    `-- [customer]/
        |-- index.md
        `-- [branch].md
```

Now `index.md` would be rendered if you navigate to [www.example.com/customers/acme](http://www.example.com/customers/acme), and `[branch].md` would be rendered if you navigate to [www.example.com/customers/acme/south](http://www.example.com/customers/acme/south).

## [Complete Example Code](https://docs.evidence.dev/core-concepts/templated-pages\#complete-example-code)

See a complete example using a table to generate a templated page for each customer.

`index.md`

````text-sm markdown
# Customers

```sql customers
select
    first_name,
    '/customers/' || first_name as customer_link,
    sum(sales) as sales_usd
from needful_things.orders
group by 1
```

<DataTable
    data={customers}
    link=customer_link
/>
````

`customers/[customer].md`

````text-sm markdown
# {params.customer}

```sql customers
select
    sum(sales) as sales_usd
from needful_things.orders
where first_name = '${params.customer}'
group by 1
```

{params.customer} bought items worth <Value data={customers} column=sales_usd />.
````

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/templated-pages/index.md)