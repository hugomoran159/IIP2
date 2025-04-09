[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Button Group](https://docs.evidence.dev/components/inputs/button-group)

# Button Group

Creates a group of single-select buttons for quick filtering

To see how to filter a query using a Button Group, see [Filters](https://docs.evidence.dev/core-concepts/filters).

## [Examples](https://docs.evidence.dev/components/inputs/button-group\#examples)

### [Button Group using Options from a Query](https://docs.evidence.dev/components/inputs/button-group\#button-group-using-options-from-a-query)

preview

code

Sinister ToysOdd EquipmentMysterious ApparelCursed Sporting Goods

Selected:

```text-sm markdown
<ButtonGroup
    data={categories}
    name=category_picker
    value=category
/>

Selected: {inputs.category_picker}
```

### [With a Title](https://docs.evidence.dev/components/inputs/button-group\#with-a-title)

preview

code

Select a Category

Sinister ToysOdd EquipmentMysterious ApparelCursed Sporting Goods

Selected:

```text-sm markdown
<ButtonGroup
    data={categories}
    name=category_selector
    value=category
    title="Select a Category"
/>

Selected: {inputs.category_selector}
```

### [With a Default Value](https://docs.evidence.dev/components/inputs/button-group\#with-a-default-value)

preview

code

Sinister ToysOdd EquipmentMysterious ApparelCursed Sporting Goods

Selected: Cursed Sporting Goods

```text-sm markdown
<ButtonGroup
    data={categories}
    name=selected_button1
    value=category
    defaultValue="Cursed Sporting Goods"
/>

Selected: {inputs.selected_button1}
```

### [With Hardcoded Options](https://docs.evidence.dev/components/inputs/button-group\#with-hardcoded-options)

preview

code

Option OneOption TwoOption Three

Selected:

```text-sm markdown
<ButtonGroup name=hardcoded_options>
    <ButtonGroupItem valueLabel="Option One" value="1" />
    <ButtonGroupItem valueLabel="Option Two" value="2" />
    <ButtonGroupItem valueLabel="Option Three" value="3" />
</ButtonGroup>

Selected: {inputs.hardcoded_options}
```

### [With Hardcoded Options and Default Value](https://docs.evidence.dev/components/inputs/button-group\#with-hardcoded-options-and-default-value)

preview

code

Option OneOption TwoOption Three

Selected: 2

```text-sm markdown
<ButtonGroup name=hardcoded_options_default>
    <ButtonGroupItem valueLabel="Option One" value="1" />
    <ButtonGroupItem valueLabel="Option Two" value="2" default />
    <ButtonGroupItem valueLabel="Option Three" value="3" />
</ButtonGroup>

Selected: {inputs.hardcoded_options_default}
```

### [Alternative Labels](https://docs.evidence.dev/components/inputs/button-group\#alternative-labels)

preview

code

SINODDMYSCUR

Selected:

```text-sm markdown
<ButtonGroup
    data={categories}
    name=alternative_labels_selector
    value=category
    label=short_category
/>

Selected: {inputs.alternative_labels_selector}
```

### [Filtering a Query](https://docs.evidence.dev/components/inputs/button-group\#filtering-a-query)

preview

code

Sinister ToysOdd EquipmentMysterious ApparelCursed Sporting Goods

Loading...

```text-sm markdown
<ButtonGroup
    data={categories}
    name=category_button_group
    value=category
/>

<DataTable data={filtered_query} emptySet=pass emptyMessage="No category selected"/>
```

### [Style Buttons as Tabs](https://docs.evidence.dev/components/inputs/button-group\#style-buttons-as-tabs)

preview

code

Sinister Toys Odd Equipment Mysterious Apparel Cursed Sporting Goods

Selected:

```text-sm markdown
<ButtonGroup
    data={categories}
    name=buttons_as_tabs
    value=category
    display=tabs
/>

Selected: {inputs.buttons_as_tabs}
```

### [Style Buttons as Tabs: With Hardcoded Options](https://docs.evidence.dev/components/inputs/button-group\#style-buttons-as-tabs-with-hardcoded-options)

preview

code

Option One Option Two Option Three

Selected:

```text-sm markdown
<ButtonGroup name=button_tabs_hardcoded_options display=tabs>
    <ButtonGroupItem valueLabel="Option One" value="1" />
    <ButtonGroupItem valueLabel="Option Two" value="2" />
    <ButtonGroupItem valueLabel="Option Three" value="3" />
</ButtonGroup>

Selected: {inputs.button_tabs_hardcoded_options}
```

# [ButtonGroup](https://docs.evidence.dev/components/inputs/button-group\#buttongroup)

## [Options](https://docs.evidence.dev/components/inputs/button-group\#options)

[name](https://docs.evidence.dev/components/inputs/button-group#props-name)

Required

Name of the button group, used to reference the selected value elsewhere as {inputs.name}

[preset](https://docs.evidence.dev/components/inputs/button-group#props-preset)

Preset values to use

Options:dates

[data](https://docs.evidence.dev/components/inputs/button-group#props-data)

Query name, wrapped in curly braces

Options:query name

[value](https://docs.evidence.dev/components/inputs/button-group#props-value)

Column name from the query containing values to pick from

Options:column name

[label](https://docs.evidence.dev/components/inputs/button-group#props-label)

Column name from the query containing labels to display instead of the values (e.g., you may want to have the drop-down use \`customer\_id\` as the value, but show \`customer\_name\` to your users)

Options:column nameDefault:Uses the column in value

[title](https://docs.evidence.dev/components/inputs/button-group#props-title)

Title to display above the button group

Options:string

[defaultValue](https://docs.evidence.dev/components/inputs/button-group#props-defaultValue)

Sets initial active button and current value

Options:value from button group, e.g. 'Cursed Sporting Goods'

[order](https://docs.evidence.dev/components/inputs/button-group#props-order)

Column to sort options by

Options:column nameDefault:Uses the same order as the query in \`data\`

[where](https://docs.evidence.dev/components/inputs/button-group#props-where)

SQL where fragment to filter options by (e.g., where sales > 40000)

Options:SQL where clause

[display](https://docs.evidence.dev/components/inputs/button-group#props-display)

Displays tabs with button functionality

Options:

tabs buttons

Default:buttons

[description](https://docs.evidence.dev/components/inputs/button-group#props-description)

Adds an info icon with description tooltip on hover. Appears next to title.

Options:string

# [ButtonGroupItem](https://docs.evidence.dev/components/inputs/button-group\#buttongroupitem)

The ButtonGroupItem component can be used to manually add options to a button group. This is useful if you want to add a default option, or if you want to add options that are not in a query.

## [Options](https://docs.evidence.dev/components/inputs/button-group\#options-1)

[value](https://docs.evidence.dev/components/inputs/button-group#props-value-2)

Required

Value to use when the option is selected

[valueLabel](https://docs.evidence.dev/components/inputs/button-group#props-valueLabel)

Label to display for the option in the dropdown

Options:stringDefault:Uses value

[default](https://docs.evidence.dev/components/inputs/button-group#props-default)

Sets the option as the default

Options:

true false

Default:false

[hideDuringPrint](https://docs.evidence.dev/components/inputs/button-group#props-hideDuringPrint)

Hide the component when the report is printed

Options:

true false

Default:true

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/button-group/index.md)