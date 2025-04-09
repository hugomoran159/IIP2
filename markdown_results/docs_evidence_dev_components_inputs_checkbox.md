[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Checkbox](https://docs.evidence.dev/components/inputs/checkbox)

# Checkbox

Creates a checkbox with toggleable input. The Title and Name attributes can be defined, enabling the passing of true and false values.

preview

code

Hide Months 0

```text-sm markdown
<Checkbox
    title="Hide Months 0"
    name=hide_months_0
/>
```

### [Checkbox using Default Value](https://docs.evidence.dev/components/inputs/checkbox\#checkbox-using-default-value)

Defining the checked property will set the initial checkbox value with true and false.

preview

code

Title of checkbox

Selected Value: true

```text-sm markdown
<Checkbox
    title="Title of checkbox"
    name=name_of_checkbox
    checked=true
/>

Selected Value: {inputs.name_of_checkbox}
```

preview

code

Exclude low values

Records Count

10,000

````text-sm markdown
```sql orders
select
    COUNT(*) as records_count
from needful_things.orders
WHERE  not ${inputs.exclude_low_value} -- When True, Do not evaluate the next condition
    OR (
            ${inputs.exclude_low_value} -- Input is set to false
        AND sales < 10  -- Apply this condition
    )
```

<Checkbox
    title="Exclude low values"
    name=exclude_low_value
/>

<BigValue fmt=num0 value=records_count data={orders}/>
````

# [Checkbox](https://docs.evidence.dev/components/inputs/checkbox\#checkbox)

## [Options](https://docs.evidence.dev/components/inputs/checkbox\#options)

[name](https://docs.evidence.dev/components/inputs/checkbox#props-name)

Required

Name of the checkbox, used to reference the selected value elsewhere as `{inputs.name.value}`

[title](https://docs.evidence.dev/components/inputs/checkbox#props-title)

Label for the checkbox. If undefined, will default to small checkbox

Options:string

[checked](https://docs.evidence.dev/components/inputs/checkbox#props-checked)

Initial value for checkbox. True value for checked, false for unchecked

Options:boolean

[description](https://docs.evidence.dev/components/inputs/checkbox#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/checkbox/index.md)