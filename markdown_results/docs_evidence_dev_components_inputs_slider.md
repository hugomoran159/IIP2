[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Inputs](https://docs.evidence.dev/components/inputs) [Slider](https://docs.evidence.dev/components/inputs/slider)

# Slider

Creates a Slider input with default min, max and step values

preview

code

sales:$50

$0$100

```text-sm markdown
<Slider
    title="sales"
    name=sales
    defaultValue=50
    fmt="usd0"
/>
```

Min and Max values can be defined, the step property and define the incremental value of the slider

preview

code

Months:0

036

```text-sm markdown
<Slider
    title="Months"
    name=monthsWithSteps
    min=0
    max=36
    step=12
/>
```

showMaxMin property can hide the Max and Min values with false, by default showMaxMin is true

preview

code

Months:0

```text-sm markdown
<Slider
    title="Months"
    name=monthsWithoutMinMax
    min=0
    max=36
    showMaxMin=false
/>
```

The default size of the slider can be altered with the size property using; medium, large or full

preview

code

Months Medium:4

036

```text-sm markdown
<Slider
    title="Months Medium"
    name=monthsMedium
    defaultValue=4
    min=0
    max=36
    size=medium
/>
```

preview

code

Months Large:18

036

```text-sm markdown
<Slider
    title="Months Large"
    name=monthsLarge
    defaultValue=18
    min=0
    max=36
    size=large
/>
```

preview

code

Months Full:26

036

```text-sm markdown
<Slider
    title="Months Full"
    name=monthsFull
    min=0
    max=36
    size=full
/>
```

## [Specifying Dynamic Columns](https://docs.evidence.dev/components/inputs/slider\#specifying-dynamic-columns)

Supply data with a specified column name to define the slider's min and max values. The slider's range will be calculated based on the column's minimum and maximum values.

preview

code

data slider:91

919,728

```text-sm markdown
<Slider
    title='data slider'
    name='RangeSlider'
    size=large
    step=100
    data={flight_data}
    range=fare
/>
```

Supply data with specified column names for minColumn, maxColumn, and/or defaultValue. The first row’s value in each of these columns will determine the minimum, maximum, or default value, respectively.

preview

code

data slider:10,000

010,000

```text-sm markdown
<Slider
    title='data slider'
    name='MaxColSlider'
    size=large
    step=100
    data={flight_data}
    maxColumn=max_fare
    min=0
    defaultValue=max_fare
/>
```

# [Slider](https://docs.evidence.dev/components/inputs/slider\#slider)

## [Options](https://docs.evidence.dev/components/inputs/slider\#options)

[name](https://docs.evidence.dev/components/inputs/slider#props-name)

Required

name of the slider, used to reference the selected value elsewhere as `{inputs.name}`

[defaultValue](https://docs.evidence.dev/components/inputs/slider#props-defaultValue)

Sets the initial value of the silder

[min](https://docs.evidence.dev/components/inputs/slider#props-min)

Sets the minimum value on the slider. Negative Values accepted.

Options:numberDefault:0

[max](https://docs.evidence.dev/components/inputs/slider#props-max)

Sets the maximum value on the slider. This value must be larger than the min.

Options:numberDefault:100

[data](https://docs.evidence.dev/components/inputs/slider#props-data)

Query name, wrapped in curly braces

Options:query name

[range](https://docs.evidence.dev/components/inputs/slider#props-range)

Required for data - Take and sets the max and min values of a column

Options:string - column name

[maxColumn](https://docs.evidence.dev/components/inputs/slider#props-maxColumn)

Takes the first value of a column and assigns it to the max value

Options:string - column name

[minColumn](https://docs.evidence.dev/components/inputs/slider#props-minColumn)

Takes the first value of a column and assigns it to the min value

Options:string - column name

[step](https://docs.evidence.dev/components/inputs/slider#props-step)

Defines the incremental value of the slider

Options:numberDefault:1

[showMinMax](https://docs.evidence.dev/components/inputs/slider#props-showMinMax)

Hides or shows min and max value markers on slider.

Options:booleanDefault:true

[size](https://docs.evidence.dev/components/inputs/slider#props-size)

Sets the length of the slider

Options:

small medium large full

Default:small

[fmt](https://docs.evidence.dev/components/inputs/slider#props-fmt)

Sets format for the value ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[description](https://docs.evidence.dev/components/inputs/slider#props-description)

Adds an info icon with description tooltip on hover

Options:string

[hideDuringPrint](https://docs.evidence.dev/components/inputs/slider#props-hideDuringPrint)

Hide the component when the report is printed

Options:

true false

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/inputs/slider/index.md)