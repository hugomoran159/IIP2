[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Dropdown](https://docs.evidence.dev/components/inputs/dropdown)

# Dropdown

Creates a dropdown menu with a list of options that can be selected. The selected option can be used to filter queries or in markdown.

To see how to filter a query using a dropdown, see [Filters](https://docs.evidence.dev/core-concepts/filters).

preview

code

Select a Category

Sinister Toys

Selected: Sinister Toys

```text-sm markdown
<Dropdown
    data={categories}
    name=category1
    value=category_name
    title="Select a Category"
    defaultValue="Sinister Toys"
/>

Selected: {inputs.category1.value}
```

## [Examples](https://docs.evidence.dev/components/inputs/dropdown\#examples)

### [Dropdown using Options from a Query](https://docs.evidence.dev/components/inputs/dropdown\#dropdown-using-options-from-a-query)

preview

code

Sinister Toys


Selected: Sinister Toys

```text-sm markdown
<Dropdown
    data={categories}
    name=category2
    value=category_name
/>
```

Selected: Sinister Toys

### [With a Title](https://docs.evidence.dev/components/inputs/dropdown\#with-a-title)

preview

code

Select a Category

Sinister Toys


Selected: Sinister Toys

```text-sm markdown
<Dropdown
    data={categories}
    name=category3
    value=category_name
    title="Select a Category"
    defaultValue="Sinister Toys"
/>

Selected: {inputs.category3.value}
```

### [With a Default Value](https://docs.evidence.dev/components/inputs/dropdown\#with-a-default-value)

preview

code

Select a Category

Odd Equipment

Selected: Odd Equipment

```text-sm markdown
<Dropdown
    data={categories}
    name=category4
    value=category_name
    title="Select a Category"
    defaultValue="Odd Equipment"
/>

Selected: {inputs.category4.value}
```

### [With Hardcoded Options](https://docs.evidence.dev/components/inputs/dropdown\#with-hardcoded-options)

preview

code

Option One


Selected: 1

```text-sm markdown
<Dropdown name=hardcoded>
    <DropdownOption valueLabel="Option One" value="1" />
    <DropdownOption valueLabel="Option Two" value="2" />
    <DropdownOption valueLabel="Option Three" value="3" />
</Dropdown>

Selected: {inputs.hardcoded.value}
```

### [Alternative Labels](https://docs.evidence.dev/components/inputs/dropdown\#alternative-labels)

This example uses a column called `abbrev`, which contains an alternate label for each category

preview

code

SIN

Selected: Sinister Toys

```text-sm markdown
<Dropdown
    data={categories}
    name=category_abbrev
    value=category_name
    label=abbrev
/>
```

Selected: Sinister Toys

### [Multi-Select](https://docs.evidence.dev/components/inputs/dropdown\#multi-select)

When using multi-select dropdowns, you need to use an alternative SQL expression:

`where column_name IN ${inputs.my_input.value}`

Note:

- The use of the IN operator
- No single quotes used around the `${}`

preview

code

Category Multi


Selected: (SELECT NULL WHERE 0 /\* An Input has not been set \*/)

```text-sm markdown
<Dropdown
    data={categories}
    name=category_multi
    value=category_name
    multiple=true
/>

Selected: {inputs.category_multi.value}
```

### [Filtering a Query](https://docs.evidence.dev/components/inputs/dropdown\#filtering-a-query)

Starting with this table of orders:

preview

code

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| ID | Order Datetime | Category | Item | Sales |
| --- | --- | --- | --- | --- |
| 1 | 2020-06-08 | Sinister Toys | Model Racehorse | 12.3 |
| 2 | 2019-12-11 | Odd Equipment | Microscope | 129.6 |
| 3 | 2020-12-25 | Sinister Toys | Baseball Card | 3.0 |
| 4 | 2021-04-27 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 5 | 2020-03-19 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 6 | 2021-01-04 | Sinister Toys | Model Racehorse | 13.0 |
| 7 | 2019-07-08 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 8 | 2021-09-19 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 9 | 2019-11-29 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 10 | 2019-12-11 | Odd Equipment | Lamp | 34.0 |
| 11 | 2019-02-27 | Cursed Sporting Goods | Boxing Gloves | 21.0 |
| 12 | 2020-05-20 | Sinister Toys | Model Racehorse | 13.0 |
| 13 | 2021-05-20 | Mysterious Apparel | Mystic Pendant | 7.6 |
| 14 | 2021-12-31 | Odd Equipment | Lamp | 34.0 |
| 15 | 2019-10-09 | Mysterious Apparel | Mystic Pendant | 7.6 |
| 16 | 2020-01-05 | Sinister Toys | Model Racehorse | 12.3 |
| 17 | 2019-08-05 | Odd Equipment | Lamp | 34.0 |
| 18 | 2019-08-14 | Odd Equipment | Lamp | 34.0 |
| 19 | 2020-11-08 | Sinister Toys | Baseball Card | 3.0 |
| 20 | 2021-12-11 | Sinister Toys | Model Racehorse | 13.0 |
| 21 | 2021-08-06 | Sinister Toys | Model Racehorse | 13.0 |
| 22 | 2020-06-10 | Odd Equipment | Lamp | 34.0 |
| 23 | 2021-09-26 | Mysterious Apparel | Vintage Jacket | 34.0 |
| 24 | 2020-09-15 | Mysterious Apparel | Necklace | 13.0 |
| 25 | 2020-02-10 | Mysterious Apparel | Vintage Jacket | 34.0 |
| 26 | 2021-10-08 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 27 | 2021-03-06 | Cursed Sporting Goods | Fishing Rod | 80.1 |
| 28 | 2021-02-03 | Odd Equipment | Lamp | 34.0 |
| 29 | 2021-09-14 | Odd Equipment | Microscope | 136.8 |
| 30 | 2021-12-07 | Mysterious Apparel | Vintage Jacket | 34.0 |
| 31 | 2021-08-26 | Cursed Sporting Goods | Running Shoes | 49.5 |
| 32 | 2021-12-04 | Cursed Sporting Goods | Running Shoes | 52.3 |
| 33 | 2019-09-02 | Odd Equipment | Lamp | 32.3 |
| 34 | 2021-11-26 | Mysterious Apparel | Necklace | 13.0 |
| 35 | 2020-12-11 | Sinister Toys | Model Racehorse | 12.3 |
| 36 | 2020-02-21 | Mysterious Apparel | Necklace | 13.0 |
| 37 | 2019-09-22 | Sinister Toys | Model Racehorse | 11.7 |
| 38 | 2019-03-15 | Odd Equipment | Lamp | 34.0 |
| 39 | 2021-02-23 | Odd Equipment | Lamp | 32.3 |
| 40 | 2019-08-19 | Sinister Toys | Baseball Card | 3.0 |
| 41 | 2020-03-12 | Sinister Toys | Baseball Card | 3.0 |
| 42 | 2020-09-24 | Mysterious Apparel | Necklace | 13.0 |
| 43 | 2019-07-20 | Sinister Toys | Model Racehorse | 11.7 |
| 44 | 2021-05-08 | Sinister Toys | Model Racehorse | 13.0 |
| 45 | 2020-11-01 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 46 | 2021-06-22 | Mysterious Apparel | Mystic Pendant | 7.6 |
| 47 | 2021-01-25 | Sinister Toys | Baseball Card | 2.9 |
| 48 | 2021-02-23 | Odd Equipment | Microscope | 144.0 |
| 49 | 2020-03-20 | Odd Equipment | Lamp | 34.0 |
| 50 | 2019-12-04 | Odd Equipment | Lamp | 34.0 |
| 51 | 2019-05-21 | Sinister Toys | Model Racehorse | 12.3 |
| 52 | 2020-04-01 | Cursed Sporting Goods | Boxing Gloves | 21.0 |
| 53 | 2021-10-03 | Mysterious Apparel | Necklace | 13.0 |
| 54 | 2020-11-30 | Odd Equipment | Microscope | 144.0 |
| 55 | 2021-07-29 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 56 | 2019-04-04 | Odd Equipment | Microscope | 144.0 |
| 57 | 2019-04-16 | Sinister Toys | Baseball Card | 3.0 |
| 58 | 2021-09-03 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 59 | 2019-11-23 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 60 | 2020-11-17 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 61 | 2019-03-19 | Sinister Toys | Model Racehorse | 13.0 |
| 62 | 2021-02-04 | Sinister Toys | Baseball Card | 3.0 |
| 63 | 2021-12-16 | Odd Equipment | Lamp | 34.0 |
| 64 | 2021-02-09 | Sinister Toys | Model Racehorse | 10.4 |
| 65 | 2020-12-25 | Odd Equipment | Lamp | 25.5 |
| 66 | 2019-12-19 | Odd Equipment | Microscope | 144.0 |
| 67 | 2019-11-08 | Odd Equipment | Microscope | 144.0 |
| 68 | 2021-02-08 | Sinister Toys | Baseball Card | 3.0 |
| 69 | 2020-07-14 | Sinister Toys | Model Racehorse | 12.3 |
| 70 | 2020-01-05 | Sinister Toys | Baseball Card | 3.0 |
| 71 | 2021-07-31 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 72 | 2021-05-06 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 73 | 2020-05-08 | Mysterious Apparel | Necklace | 11.7 |
| 74 | 2021-07-05 | Mysterious Apparel | Vintage Jacket | 34.0 |
| 75 | 2020-06-18 | Sinister Toys | Toy Doll | 5.0 |
| 76 | 2019-07-13 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 77 | 2019-03-21 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 78 | 2020-07-23 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 79 | 2019-09-13 | Sinister Toys | Baseball Card | 2.7 |
| 80 | 2020-12-30 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 81 | 2019-07-29 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 82 | 2021-09-16 | Sinister Toys | Model Racehorse | 13.0 |
| 83 | 2019-09-01 | Odd Equipment | Microscope | 115.2 |
| 84 | 2021-09-11 | Mysterious Apparel | Vintage Jacket | 34.0 |
| 85 | 2020-07-23 | Odd Equipment | Lamp | 34.0 |
| 86 | 2019-07-11 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 87 | 2020-11-21 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 88 | 2021-09-14 | Odd Equipment | Lamp | 34.0 |
| 89 | 2021-01-11 | Odd Equipment | Lamp | 34.0 |
| 90 | 2019-03-09 | Cursed Sporting Goods | Boxing Gloves | 21.0 |
| 91 | 2019-02-19 | Odd Equipment | Lamp | 34.0 |
| 92 | 2021-11-01 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 93 | 2019-05-27 | Cursed Sporting Goods | Boxing Gloves | 21.0 |
| 94 | 2020-11-18 | Odd Equipment | Microscope | 144.0 |
| 95 | 2020-06-16 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 96 | 2019-05-26 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 97 | 2020-11-14 | Odd Equipment | Lamp | 34.0 |
| 98 | 2021-09-11 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 99 | 2019-01-05 | Sinister Toys | Baseball Card | 3.0 |
| 100 | 2020-07-07 | Sinister Toys | Toy Doll | 5.0 |

No Results

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| ID | Order Datetime | Category | Item | Sales |
| --- | --- | --- | --- | --- |
| 1 | 2020-06-08 | Sinister Toys | Model Racehorse | 12.3 |
| 2 | 2019-12-11 | Odd Equipment | Microscope | 129.6 |
| 3 | 2020-12-25 | Sinister Toys | Baseball Card | 3.0 |
| 4 | 2021-04-27 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 5 | 2020-03-19 | Cursed Sporting Goods | Running Shoes | 55.0 |
| 6 | 2021-01-04 | Sinister Toys | Model Racehorse | 13.0 |
| 7 | 2019-07-08 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 8 | 2021-09-19 | Mysterious Apparel | Mystic Pendant | 8.0 |
| 9 | 2019-11-29 | Cursed Sporting Goods | Fishing Rod | 89.0 |
| 10 | 2019-12-11 | Odd Equipment | Lamp | 34.0 |

No Results

Page

/
1010 of 100 records

````text-sm markdown
```sql order_history
select id, order_datetime, category, item, sales  from needful_things.orders
limit 100
```

<DataTable data={order_history}/>
````

Use this input to filter the results:

preview

code

Category

1
Sinister Toys

Filtered Row Count: 28

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| ID | Order Datetime | Category | Item | Sales |
| --- | --- | --- | --- | --- |
| 1 | 2020-06-08 | Sinister Toys | Model Racehorse | 12.3 |
| 3 | 2020-12-25 | Sinister Toys | Baseball Card | 3.0 |
| 6 | 2021-01-04 | Sinister Toys | Model Racehorse | 13.0 |
| 12 | 2020-05-20 | Sinister Toys | Model Racehorse | 13.0 |
| 16 | 2020-01-05 | Sinister Toys | Model Racehorse | 12.3 |
| 19 | 2020-11-08 | Sinister Toys | Baseball Card | 3.0 |
| 20 | 2021-12-11 | Sinister Toys | Model Racehorse | 13.0 |
| 21 | 2021-08-06 | Sinister Toys | Model Racehorse | 13.0 |
| 35 | 2020-12-11 | Sinister Toys | Model Racehorse | 12.3 |
| 37 | 2019-09-22 | Sinister Toys | Model Racehorse | 11.7 |
| 40 | 2019-08-19 | Sinister Toys | Baseball Card | 3.0 |
| 41 | 2020-03-12 | Sinister Toys | Baseball Card | 3.0 |
| 43 | 2019-07-20 | Sinister Toys | Model Racehorse | 11.7 |
| 44 | 2021-05-08 | Sinister Toys | Model Racehorse | 13.0 |
| 47 | 2021-01-25 | Sinister Toys | Baseball Card | 2.9 |
| 51 | 2019-05-21 | Sinister Toys | Model Racehorse | 12.3 |
| 57 | 2019-04-16 | Sinister Toys | Baseball Card | 3.0 |
| 61 | 2019-03-19 | Sinister Toys | Model Racehorse | 13.0 |
| 62 | 2021-02-04 | Sinister Toys | Baseball Card | 3.0 |
| 64 | 2021-02-09 | Sinister Toys | Model Racehorse | 10.4 |
| 68 | 2021-02-08 | Sinister Toys | Baseball Card | 3.0 |
| 69 | 2020-07-14 | Sinister Toys | Model Racehorse | 12.3 |
| 70 | 2020-01-05 | Sinister Toys | Baseball Card | 3.0 |
| 75 | 2020-06-18 | Sinister Toys | Toy Doll | 5.0 |
| 79 | 2019-09-13 | Sinister Toys | Baseball Card | 2.7 |
| 82 | 2021-09-16 | Sinister Toys | Model Racehorse | 13.0 |
| 99 | 2019-01-05 | Sinister Toys | Baseball Card | 3.0 |
| 100 | 2020-07-07 | Sinister Toys | Toy Doll | 5.0 |

No Results

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| ID | Order Datetime | Category | Item | Sales |
| --- | --- | --- | --- | --- |
| 1 | 2020-06-08 | Sinister Toys | Model Racehorse | 12.3 |
| 3 | 2020-12-25 | Sinister Toys | Baseball Card | 3.0 |
| 6 | 2021-01-04 | Sinister Toys | Model Racehorse | 13.0 |
| 12 | 2020-05-20 | Sinister Toys | Model Racehorse | 13.0 |
| 16 | 2020-01-05 | Sinister Toys | Model Racehorse | 12.3 |
| 19 | 2020-11-08 | Sinister Toys | Baseball Card | 3.0 |
| 20 | 2021-12-11 | Sinister Toys | Model Racehorse | 13.0 |
| 21 | 2021-08-06 | Sinister Toys | Model Racehorse | 13.0 |
| 35 | 2020-12-11 | Sinister Toys | Model Racehorse | 12.3 |
| 37 | 2019-09-22 | Sinister Toys | Model Racehorse | 11.7 |

No Results

Page

/
310 of 28 records

````text-sm markdown
<Dropdown
    data={query_name}
    name=name_of_dropdown
    value=column_name
/>

```sql filtered_query
select *
from source_name.table
where column_name like '${inputs.name_of_dropdown.value}'
```

Filtered Row Count: {orders_filtered.length}

<DataTable data={orders_filtered}/>
````

### [Multiple defaultValues](https://docs.evidence.dev/components/inputs/dropdown\#multiple-defaultvalues)

preview

code

Category Multi Default

2
Mysterious Apparel Sinister Toys

Selected: ('Mysterious Apparel','Sinister Toys')

```text-sm svelte
<Dropdown
    data={query_name}
    name=name_of_dropdown
    value=column_name
    multiple=true
	defaultValue={['Sinister Toys', 'Mysterious Apparel']}
/>

Selected: {inputs.category_multi_default.value}
```

### [Select all by Default Value with Multiple](https://docs.evidence.dev/components/inputs/dropdown\#select-all-by-default-value-with-multiple)

Select and return all values in the dropdown list, requires "multiple" prop.

preview

code

Select a Category

4
4 Selected

Selected: ('Cursed Sporting Goods','Mysterious Apparel','Odd Equipment','Sinister Toys')

```text-sm markdown
<Dropdown
    data={categories}
    name=category_multi_selectAllByDefault
    value=category_name
    title="Select a Category"
    multiple=true
    selectAllByDefault=true
/>

Selected: {inputs.category_multi_selectAllByDefault.value}
```

# [Dropdown](https://docs.evidence.dev/components/inputs/dropdown\#dropdown)

## [Options](https://docs.evidence.dev/components/inputs/dropdown\#options)

[name](https://docs.evidence.dev/components/inputs/dropdown#props-name)

Required

Name of the dropdown, used to reference the selected value elsewhere as {inputs.name.value}

[data](https://docs.evidence.dev/components/inputs/dropdown#props-data)

Query name, wrapped in curly braces

Options:query name

[value](https://docs.evidence.dev/components/inputs/dropdown#props-value)

Column name from the query containing values to pick from

Options:column name

[multiple](https://docs.evidence.dev/components/inputs/dropdown#props-multiple)

Enables multi-select which returns a list

Options:

true false

Default:false

[defaultValue](https://docs.evidence.dev/components/inputs/dropdown#props-defaultValue)

Value to use when the dropdown is first loaded. Must be one of the options in the dropdown. Arrays supported for multi-select.

Options:value from dropdown \| array of values e.g. {\['Value 1', 'Value 2'\]}

[selectAllByDefault](https://docs.evidence.dev/components/inputs/dropdown#props-selectAllByDefault)

Selects and returns all values, multiple property required

Options:

true false

Default:false

[noDefault](https://docs.evidence.dev/components/inputs/dropdown#props-noDefault)

Stops any default from being selected. Overrides any set \`defaultValue\`.

Options:booleanDefault:false

[disableSelectAll](https://docs.evidence.dev/components/inputs/dropdown#props-disableSelectAll)

Removes the \`Select all\` button. Recommended for large datasets.

Options:booleanDefault:false

[label](https://docs.evidence.dev/components/inputs/dropdown#props-label)

Column name from the query containing labels to display instead of the values (e.g., you may want to have the drop-down use \`customer\_id\` as the value, but show \`customer\_name\` to your users)

Options:column nameDefault:Uses the column in value

[title](https://docs.evidence.dev/components/inputs/dropdown#props-title)

Title to display above the dropdown

Options:string

[order](https://docs.evidence.dev/components/inputs/dropdown#props-order)

Column to sort options by, with optional ordering keyword

Options:column name \[ asc \| desc \]Default:Ascending based on dropdown value (or label, if specified)

[where](https://docs.evidence.dev/components/inputs/dropdown#props-where)

SQL where fragment to filter options by (e.g., where sales > 40000)

Options:SQL where clause

[hideDuringPrint](https://docs.evidence.dev/components/inputs/dropdown#props-hideDuringPrint)

Hide the component when the report is printed

Options:

true false

Default:true

[description](https://docs.evidence.dev/components/inputs/dropdown#props-description)

Adds an info icon with description tooltip on hover

Options:string

# [DropdownOption](https://docs.evidence.dev/components/inputs/dropdown\#dropdownoption)

## [Options](https://docs.evidence.dev/components/inputs/dropdown\#options-1)

The DropdownOption component can be used to manually add options to a dropdown. This is useful to add a default option, or to add options that are not in a query.

[value](https://docs.evidence.dev/components/inputs/dropdown#props-value-2)

Required

Value to use when the option is selected

[valueLabel](https://docs.evidence.dev/components/inputs/dropdown#props-valueLabel)

Label to display for the option in the dropdown

Default:Uses the value

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/dropdown/index.md)