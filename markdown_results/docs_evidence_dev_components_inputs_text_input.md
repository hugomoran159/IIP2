[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Text Input](https://docs.evidence.dev/components/inputs/text-input)

# Text Input

Creates a text input that can be used to filter or search

To see how to filter a query using a text input, see [Filters](https://docs.evidence.dev/core-concepts/filters).

preview

code

Search

Selected:

```text-sm markdown
<TextInput
    name=name_of_input
    title="Search"
/>

Selected: {inputs.text_input_name}
```

## [Examples](https://docs.evidence.dev/components/inputs/text-input\#examples)

### [Basic Text Input](https://docs.evidence.dev/components/inputs/text-input\#basic-text-input)

preview

code

Selected:

```text-sm markdown
<TextInput
    name=name_of_input
/>

Selected: {inputs.name_of_input}
```

### [With Title](https://docs.evidence.dev/components/inputs/text-input\#with-title)

preview

code

Search

Selected:

```text-sm markdown
<TextInput
    name=name_of_input
    title="Search"
/>

Selected: {inputs.text_input2}
```

### [With Placeholder](https://docs.evidence.dev/components/inputs/text-input\#with-placeholder)

preview

code

Freetext Search

Selected:

```text-sm markdown
<TextInput
    name=name_of_input
    title="Freetext Search"
    placeholder="Start typing"
/>

Selected: {inputs.text_input3}
```

### [With Default Text Prefilled](https://docs.evidence.dev/components/inputs/text-input\#with-default-text-prefilled)

preview

code

Default Selected

Selected: Sporting

```text-sm markdown
<TextInput
    name=name_of_input
    title="Default Selected"
    defaultValue="Sporting"
/>

Selected: {inputs.text_input4}
```

### [Fuzzy Finding (Searching)](https://docs.evidence.dev/components/inputs/text-input\#fuzzy-finding-searching)

`TextInput` provides an easy-to-use shortcut for [fuzzy finding](https://duckdb.org/docs/sql/functions/char#text-similarity-functions). Note that this is different than `LIKE`, as it does not require a direct substring, and is useful in situtations where spelling may be unknown, like names.

You can reference it by using the syntax `{inputs.your_input_name.search('column_name')}`, and it returns a number between 0 and 1.

## [Usage](https://docs.evidence.dev/components/inputs/text-input\#usage)

Assuming you had some TextInput `first_name_search`:

```text-sm sql
SELECT * FROM users
ORDER BY {inputs.first_name_search.search('first_name')}
LIMIT 10 -- Optionally limit to only show the 10 closest results
```

becomes

```text-sm sql
SELECT * FROM users
ORDER BY damerau_levenshtein(first_name, '{inputs.first_name_search}')
LIMIT 10 -- Optionally limit to only show the 10 closest results
```

## [Options](https://docs.evidence.dev/components/inputs/text-input\#options)

[name](https://docs.evidence.dev/components/inputs/text-input#props-name)

Required

Name of the text input, used to reference the selected value elsewhere as `{inputs.name.value}`

Options:string

[title](https://docs.evidence.dev/components/inputs/text-input#props-title)

Title displayed above the text input

Options:string

[placeholder](https://docs.evidence.dev/components/inputs/text-input#props-placeholder)

Alternative placeholder text displayed in the text input

Options:stringDefault:Type to search

[hideDuringPrint](https://docs.evidence.dev/components/inputs/text-input#props-hideDuringPrint)

Hide the component when the report is printed

Options:

true false

Default:true

[description](https://docs.evidence.dev/components/inputs/text-input#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/text-input/index.md)