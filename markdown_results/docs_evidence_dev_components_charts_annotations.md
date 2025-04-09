[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Charts](https://docs.evidence.dev/components/charts) [Annotations](https://docs.evidence.dev/components/charts/annotations)

# Annotations

Use annotations to add important context directly to a chart - highlight areas, or specific points to make it easier for your reader to draw insights.

## [At a glance](https://docs.evidence.dev/components/charts/annotations\#at-a-glance)

Evidence currently offers 4 types of annotations, which can be defined inline or with a dataset:

- [`ReferenceLine`](https://docs.evidence.dev/components/charts/annotations#reference-line): draw a line on a chart (e.g. sales target, launch dates, linear regression)
- [`ReferenceArea`](https://docs.evidence.dev/components/charts/annotations#reference-area): highlight an area on a chart (e.g. holiday shopping periods, metric control ranges)
- [`ReferencePoint`](https://docs.evidence.dev/components/charts/annotations#reference-point): highlight specific points on a chart (e.g. anomalies, points of interest)
- [`Callout`](https://docs.evidence.dev/components/charts/annotations#callout): draw attention to data (e.g. data trend explanation)

preview

code

Callout
Data trending up here

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferenceLine y=7500 label="Reference Line" hideValue labelPosition="aboveStart" color=positive/>
    <ReferenceArea xMin='2020-03-14' xMax='2020-08-15' label="Reference Area" color=warning/>
    <ReferencePoint x="2019-07-01" y=6590 label="Reference Point" labelPosition=bottom color=negative/>
    <Callout x="2021-05-01" y=11012 labelPosition=bottom labelWidth=fit>
        Callout
        Data trending up here
    </Callout>
</LineChart>
```

# [Reference Line](https://docs.evidence.dev/components/charts/annotations\#reference-line)

Reference lines allow you to add lines to a chart to provide additional context within the visualization. These lines can be produced by providing a specific value ( `y=50` or `x='2020-03-14'`) or by providing a dataset (e.g., `date`, `event_name`).

If you provide coordinates for `[x, y]` and `[x2, y2]`, you can create sloped lines between points.

When a dataset is provided, `ReferenceLine` can generate multiple lines - one for each row in the dataset. This can be helpful for plotting things like important milestones, launch dates, or experiment start dates.

## [Examples](https://docs.evidence.dev/components/charts/annotations\#examples)

### [Y-axis Defined Inline](https://docs.evidence.dev/components/charts/annotations\#y-axis-defined-inline)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yAxisTitle="Sales per Month" yFmt=usd0>
    <ReferenceLine y=9000 label="Target"/>
</LineChart>
```

### [X-axis Defined Inline](https://docs.evidence.dev/components/charts/annotations\#x-axis-defined-inline)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yAxisTitle="Sales per Month" yFmt=usd0>
    <ReferenceLine x='2019-09-18' label="Launch" hideValue=true/>
</LineChart>
```

### [Y-axis Multiple Lines](https://docs.evidence.dev/components/charts/annotations\#y-axis-multiple-lines)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0 yAxisTitle="Sales per Month">
    <ReferenceLine y=9000 label="Target" labelPosition=belowEnd/>
    <ReferenceLine y=10500 label="Forecast"/>
</LineChart>
```

### [X-axis from Data](https://docs.evidence.dev/components/charts/annotations\#x-axis-from-data)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0 yAxisTitle="Sales per Month">
    <ReferenceLine data={multiple_dates} x=start_date label=campaign_name hideValue/>
</LineChart>
```

### [Sloped Line Inline](https://docs.evidence.dev/components/charts/annotations\#sloped-line-inline)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0 yAxisTitle="Sales per Month">
    <ReferenceLine x='2019-01-01' y=6500 x2='2021-12-01' y2=12000 label="Growth Trend" labelPosition=belowEnd/>
</LineChart>
```

### [Linear Regression from Data](https://docs.evidence.dev/components/charts/annotations\#linear-regression-from-data)

preview

code

```text-sm html
<ScatterPlot data={orders_by_state} x=sales y=num_orders xMin=0 yMin=0>
    <ReferenceLine data={regression} x=x y=y x2=x2 y2=y2 label=label color=base-content-muted lineType=solid/>
</ScatterPlot>
```

### [Custom Styling](https://docs.evidence.dev/components/charts/annotations\#custom-styling)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales_usd0k yAxisTitle="Sales per Month">
    <ReferenceLine y=110000 color=negative hideValue=true lineWidth=3 lineType=solid/>
</LineChart>
```

### [Label Positions](https://docs.evidence.dev/components/charts/annotations\#label-positions)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0k yAxisTitle="Sales per Month">
    <ReferenceLine y=4000 label=aboveStart labelPosition=aboveStart hideValue/>
    <ReferenceLine y=4000 label=aboveCenter labelPosition=aboveCenter hideValue/>
    <ReferenceLine y=4000 label=aboveEnd labelPosition=aboveEnd hideValue/>
    <ReferenceLine y=4000 label=belowStart labelPosition=belowStart hideValue/>
    <ReferenceLine y=4000 label=belowCenter labelPosition=belowCenter hideValue/>
    <ReferenceLine y=4000 label=belowEnd labelPosition=belowEnd hideValue/>
</LineChart>
```

### [Colours](https://docs.evidence.dev/components/charts/annotations\#colours)

preview

code

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0k yAxisTitle="Sales per Month">
    <ReferenceLine y=1500 color=negative label=negative/>
    <ReferenceLine y=3500 color=warning label=warning/>
    <ReferenceLine y=5500 color=positive label=positive/>
    <ReferenceLine y=7500 color=info label=info/>
    <ReferenceLine y=9500 color=base-content-muted label=base-content-muted/>
    <ReferenceLine y=11500 color=#63178f label=custom/>
</LineChart>
```

## [Options](https://docs.evidence.dev/components/charts/annotations\#options)

A reference line can be produced by defining values inline or by supplying a dataset, and the required props are different for each of those cases.

### [Defining Values Inline](https://docs.evidence.dev/components/charts/annotations\#defining-values-inline)

[x](https://docs.evidence.dev/components/charts/annotations#props-x)

x-axis value where line will be plotted, or coordinate where line will start if x2 is provided

Options:number \| string \| date

[y](https://docs.evidence.dev/components/charts/annotations#props-y)

y-axis value where line will be plotted, or coordinate where line will start if y2 is provided

Options:number

[x2](https://docs.evidence.dev/components/charts/annotations#props-x2)

x-axis value for line endpoint

Options:number \| string \| date

[y2](https://docs.evidence.dev/components/charts/annotations#props-y2)

y-axis value for line endpoint

Options:number

[label](https://docs.evidence.dev/components/charts/annotations#props-label)

Text to show as label for the line. If no label is provided, the value will be used.

Options:string

This table shows how you combine `x`, `y`, `x2`, and `y2` to create different types of lines:

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| x | y | x2 | y2 | Result |
| --- | --- | --- | --- | --- |
| 5 | - | - | - | Vertical line at x=5 |
| - | 100 | - | - | Horizontal line at y=100 |
| 5 | 100 | - | - | Vertical line at x=5 (ignores y) |
| 5 | 100 | - | 200 | Vertical line from \[5, 100\] to \[5, 200\] |
| 5 | 100 | 10 | - | Horizontal line from \[5, 100\] to \[10, 100\] |
| 5 | 100 | 10 | 200 | Sloped line from \[5, 100\] to \[10, 200\] |

No Results

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| x | y | x2 | y2 | Result |
| --- | --- | --- | --- | --- |
| 5 | - | - | - | Vertical line at x=5 |
| - | 100 | - | - | Horizontal line at y=100 |
| 5 | 100 | - | - | Vertical line at x=5 (ignores y) |
| 5 | 100 | - | 200 | Vertical line from \[5, 100\] to \[5, 200\] |
| 5 | 100 | 10 | - | Horizontal line from \[5, 100\] to \[10, 100\] |
| 5 | 100 | 10 | 200 | Sloped line from \[5, 100\] to \[10, 200\] |

No Results

If you provide `[x, y]` and `[x2, y2]`, coordinates must fall within the chart's boundaries in order for the line to be drawn.

### [Supplying a Dataset](https://docs.evidence.dev/components/charts/annotations\#supplying-a-dataset)

[data](https://docs.evidence.dev/components/charts/annotations#props-data)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/annotations#props-x-2)

Column containing x-axis values for lines (or starting points if x2 is provided)

Options:column name

[y](https://docs.evidence.dev/components/charts/annotations#props-y-2)

Column containing y-axis values for lines (or starting points if y2 is provided)

Options:column name

[x2](https://docs.evidence.dev/components/charts/annotations#props-x2-2)

Column containing x-axis values for line endpoints.

Options:column name

[y2](https://docs.evidence.dev/components/charts/annotations#props-y2-2)

Column containing y-axis values for line endpoints.

Options:column name

[label](https://docs.evidence.dev/components/charts/annotations#props-label-2)

Column containing a label to use for each line

Options:column name

[hideValue](https://docs.evidence.dev/components/charts/annotations#props-hideValue)

Option to remove the value from the label

Options:

true false

Default:false

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| x | y | x2 | y2 | Result |
| --- | --- | --- | --- | --- |
| x\_col | - | - | - | Vertical lines at values in x\_col |
| - | y\_col | - | - | Horizontal lines at values in y\_col |
| x\_col | y\_col | - | - | Vertical lines at x\_col (ignores y\_col) |
| x\_col | y\_col | x2\_col | y2\_col | Sloped Lines from \[x\_col, y\_col\] to \[x2\_col, y2\_col\] |

No Results

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| x | y | x2 | y2 | Result |
| --- | --- | --- | --- | --- |
| x\_col | - | - | - | Vertical lines at values in x\_col |
| - | y\_col | - | - | Horizontal lines at values in y\_col |
| x\_col | y\_col | - | - | Vertical lines at x\_col (ignores y\_col) |
| x\_col | y\_col | x2\_col | y2\_col | Sloped Lines from \[x\_col, y\_col\] to \[x2\_col, y2\_col\] |

No Results

If you provide `[x, y]` and `[x2, y2]`, coordinates must fall within the chart's boundaries in order for lines to be drawn.

### [Styling](https://docs.evidence.dev/components/charts/annotations\#styling)

[color](https://docs.evidence.dev/components/charts/annotations#props-color)

Color to override default line and label colors

Options:CSS name \| hexademical \| RGB \| HSL

[lineColor](https://docs.evidence.dev/components/charts/annotations#props-lineColor)

Color to override default line color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[lineType](https://docs.evidence.dev/components/charts/annotations#props-lineType)

Options to show breaks in a line (dashed or dotted)

Options:

solid dashed dotted

Default:dashed

[lineWidth](https://docs.evidence.dev/components/charts/annotations#props-lineWidth)

Thickness of line (in pixels)

Options:numberDefault:1.3

[symbolStart](https://docs.evidence.dev/components/charts/annotations#props-symbolStart)

The type of symbol used to mark the start of the line

Options:

circle rect roundRect triangle diamond pin arrow none

Default:circle

[symbolStartSize](https://docs.evidence.dev/components/charts/annotations#props-symbolStartSize)

The size of the symbol at the start of the line

Options:numberDefault:8

[symbolEnd](https://docs.evidence.dev/components/charts/annotations#props-symbolEnd)

The type of symbol used to mark the end of the line

Options:

circle rect roundRect triangle diamond pin arrow none

Default:circle

[symbolEndSize](https://docs.evidence.dev/components/charts/annotations#props-symbolEndSize)

The size of the symbol at the end of the line

Options:numberDefault:8

[labelPosition](https://docs.evidence.dev/components/charts/annotations#props-labelPosition)

Where label will appear on the line

Options:

aboveStart aboveCenter aboveEnd belowStart belowCenter belowEnd

Default:aboveEnd

[labelColor](https://docs.evidence.dev/components/charts/annotations#props-labelColor)

Color to override default label color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[labelBackground](https://docs.evidence.dev/components/charts/annotations#props-labelBackground)

Option to show a white semi-transparent background behind the label. Helps when label is shown in front of darker colours.

Options:

true false

Default:true

[labelPadding](https://docs.evidence.dev/components/charts/annotations#props-labelPadding)

Padding between the text and the border of the label background

Options:number

[labelBorderWidth](https://docs.evidence.dev/components/charts/annotations#props-labelBorderWidth)

The thickness of the border around the label (in pixels)

Options:number

[labelBorderRadius](https://docs.evidence.dev/components/charts/annotations#props-labelBorderRadius)

The radius of rounded corners on the label background (in pixels)

Options:number

[labelBorderColor](https://docs.evidence.dev/components/charts/annotations#props-labelBorderColor)

The color of the border around the label background

Options:CSS name \| hexademical \| RGB \| HSL

[labelBorderType](https://docs.evidence.dev/components/charts/annotations#props-labelBorderType)

The type of border around the label background (dashed or dotted)

Options:

solid dotted dashed

[fontSize](https://docs.evidence.dev/components/charts/annotations#props-fontSize)

The size of the font in the label

Options:number

[align](https://docs.evidence.dev/components/charts/annotations#props-align)

How to align the label to the symbol, and the text within the label

Options:

left center right

[bold](https://docs.evidence.dev/components/charts/annotations#props-bold)

Make the label text bold

Options:

true false

Default:false

[italic](https://docs.evidence.dev/components/charts/annotations#props-italic)

Make the label text italic

Options:

true false

Default:false

# [Reference Area](https://docs.evidence.dev/components/charts/annotations\#reference-area)

Reference areas allow you to add highlighted ranges to a chart. These ranges can be:

- Along the x-axis (e.g., recession date ranges)
- Along the y-axis (e.g., control threshold for a metric)
- Both (e.g, highlighting a specific series of points in the middle of the chart)

Reference areas can be produced by defining the x and y-axis values inline (e.g., `xMin='2020-03-14' xMax='2020-06-30'`) or by supplying a dataset (e.g., `start_date`, `end_date`, `name`).

When a dataset is provided, `ReferenceArea` can generate multiple areas - one for each row in the dataset.

## [Examples](https://docs.evidence.dev/components/charts/annotations\#examples-1)

### [X-axis Defined Inline](https://docs.evidence.dev/components/charts/annotations\#x-axis-defined-inline-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0 yAxisTitle="Sales per Month">
    <ReferenceArea xMin='2020-03-14' xMax='2020-08-15' label=First color=warning/>
    <ReferenceArea xMin='2021-03-14' xMax='2021-08-15' label=Second/>
</LineChart>
```

### [Y-axis Defined Inline](https://docs.evidence.dev/components/charts/annotations\#y-axis-defined-inline-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=num_orders yAxisTitle="Orders per Month">
    <ReferenceArea yMin=250 color=positive label="Good"/>
    <ReferenceArea yMin=100 yMax=250 color=warning label="Okay"/>
    <ReferenceArea yMin=0 yMax=100 color=negative label="Bad"/>
</LineChart>
```

### [X-axis from Data](https://docs.evidence.dev/components/charts/annotations\#x-axis-from-data-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0 yAxisTitle="Sales per Month">
    <ReferenceArea data={multiple_dates} xMin=start_date xMax=end_date label=campaign_name/>
</LineChart>
```

### [Bar Chart](https://docs.evidence.dev/components/charts/annotations\#bar-chart)

```text-sm html
<BarChart data={orders_by_category_2021} x=month y=sales yFmt=usd0 series=category>
    <ReferenceArea xMin='2021-01-01' xMax='2021-04-01'/>
</BarChart>
```

#### [Continuous Axis Bar Charts](https://docs.evidence.dev/components/charts/annotations\#continuous-axis-bar-charts)

On a continous x-axis (dates or numbers), the reference area will start and stop at the exact point on the x-axis. This means it will appear in the middle of whichever bar is at that point. If you would prefer to see the area cover the full bar, there are 2 ways to achieve this:

1. Add a buffer on either side of the range you want to highlight (e.g., instead of ending the area at `2020-07-01`, end it at `2020-07-15`)
2. Change your x-axis to categorical data (using `xType=category`). If using a date axis, you may also want to retain the axis label formatting for dates - to achieve this, you can use the `xFmt` prop (e.g., `xFmt=mmm`)

### [Reference Area Box](https://docs.evidence.dev/components/charts/annotations\#reference-area-box)

![](https://docs.evidence.dev/img/refarea-box.png)

```text-sm html
<ScatterPlot data={countries} x=gdp_usd y=gdp_growth_pct1 tooltipTitle=country series=continent>
    <ReferenceArea xMin=16000 xMax=24000 yMin=-0.03 yMax=0.055 label="Large and stagnant" color=base-content-muted border=true/>
</ScatterPlot>
```

### [Labels](https://docs.evidence.dev/components/charts/annotations\#labels)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=topLeft labelPosition=topLeft areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=top labelPosition=top areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=topRight labelPosition=topRight areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=left labelPosition=left areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=center labelPosition=center areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=right labelPosition=right areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=bottomLeft labelPosition=bottomLeft areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=bottom labelPosition=bottom areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
    <ReferenceArea xMin='2019-07-01' xMax='2021-07-31' label=bottomRight labelPosition=bottomRight areaColor="hsla(206.25, 80%, 80%, 0.01)"/>
</LineChart>
```

#### [Label Overlaps](https://docs.evidence.dev/components/charts/annotations\#label-overlaps)

Reference areas appear behind chart gridlines, including reference area labels. If you are seeing an overlap between the gridlines and the reference area label, you can avoi this by turning gridlines off ( `yGridlines=false`).

### [Colours](https://docs.evidence.dev/components/charts/annotations\#colours-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0 >
    <ReferenceArea xMax='2019-04-01' label=info color=info/>
    <ReferenceArea xMin='2019-04-01' xMax='2019-11-01' label=negative color=negative/>
    <ReferenceArea xMin='2019-11-01' xMax='2020-07-01' label=warning color=warning/>
    <ReferenceArea xMin='2020-07-01' xMax='2021-02-01' label=positive color=positive/>
    <ReferenceArea xMin='2021-02-01' xMax='2021-09-01' label=base-content-muted color=base-content-muted/>
    <ReferenceArea xMin='2021-09-01' label=custom color=#f2dbff labelColor=#4d1070/>
</LineChart>
```

## [Options](https://docs.evidence.dev/components/charts/annotations\#options-1)

A reference area can be produced by defining values inline or by supplying a dataset, and the required props are different for each of those cases.

### [Defining Values Inline](https://docs.evidence.dev/components/charts/annotations\#defining-values-inline-1)

[xMin](https://docs.evidence.dev/components/charts/annotations#props-xMin)

x-axis value where area should start. If left out, range will extend to the start of the x-axis.

Options:number \| string \| date

[xMax](https://docs.evidence.dev/components/charts/annotations#props-xMax)

x-axis value where area should end. If left out, range will extend to the end of the x-axis.

Options:number \| string \| date

[yMin](https://docs.evidence.dev/components/charts/annotations#props-yMin)

y-axis value where area should start. If left out, range will extend to the start of the y-axis.

Options:number

[yMax](https://docs.evidence.dev/components/charts/annotations#props-yMax)

y-axis value where area should end. If left out, range will extend to the end of the y-axis.

Options:number

[label](https://docs.evidence.dev/components/charts/annotations#props-label-3)

Text to show as label for the area

Options:string

- At least 1 of `xMin`, `xMax`, `yMin`, or `yMax` is required to plot an area.

### [Supplying a Dataset](https://docs.evidence.dev/components/charts/annotations\#supplying-a-dataset-1)

[data](https://docs.evidence.dev/components/charts/annotations#props-data-2)

Required

Query name, wrapped in curly braces

Options:query name

[xMin](https://docs.evidence.dev/components/charts/annotations#props-xMin-2)

Column containing x-axis values for area start. If left out, range will extend to the start of the x-axis.

Options:column name

[xMax](https://docs.evidence.dev/components/charts/annotations#props-xMax-2)

Column containing x-axis values for area end. If left out, range will extend to the end of the x-axis.

Options:column name

[yMin](https://docs.evidence.dev/components/charts/annotations#props-yMin-2)

Column containing y-axis values for area start. If left out, range will extend to the start of the y-axis.

Options:column name

[yMax](https://docs.evidence.dev/components/charts/annotations#props-yMax-2)

Column containing y-axis values for area end. If left out, range will extend to the end of the y-axis.

Options:column name

[label](https://docs.evidence.dev/components/charts/annotations#props-label-4)

Column containing a label to use for each area

Options:column name

- At least 1 of `xMin`, `xMax`, `yMin`, or `yMax` is required to plot an area.

### [Styling](https://docs.evidence.dev/components/charts/annotations\#styling-1)

[color](https://docs.evidence.dev/components/charts/annotations#props-color-2)

Color to override default area and label colors

Options:CSS name \| hexademical \| RGB \| HSL

[areaColor](https://docs.evidence.dev/components/charts/annotations#props-areaColor)

Color to override default area color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[opacity](https://docs.evidence.dev/components/charts/annotations#props-opacity)

Opacity of the highlighted area

Options:number

[border](https://docs.evidence.dev/components/charts/annotations#props-border)

Renders a border around the highlighted area

Default:false

[borderColor](https://docs.evidence.dev/components/charts/annotations#props-borderColor)

Color to override default border color

Options:CSS name \| hexademical \| RGB \| HSL

[borderType](https://docs.evidence.dev/components/charts/annotations#props-borderType)

Options to show breaks in a line (dashed or dotted)

Options:

solid dashed dotted

Default:dashed

[borderWidth](https://docs.evidence.dev/components/charts/annotations#props-borderWidth)

Thickness of border (in pixels)

Options:number

[labelPosition](https://docs.evidence.dev/components/charts/annotations#props-labelPosition-2)

Where label will appear within the area

Options:

topLeft top topRight left center right bottomLeft bottom bottomRight

Default:topLeft

[labelColor](https://docs.evidence.dev/components/charts/annotations#props-labelColor-2)

Color to override default label color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[labelColor](https://docs.evidence.dev/components/charts/annotations#props-labelColor-3)

Color to override default label color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[labelBackgroundColor](https://docs.evidence.dev/components/charts/annotations#props-labelBackgroundColor)

The color of the background behind the label

Options:CSS name \| hexademical \| RGB \| HSL

[labelPadding](https://docs.evidence.dev/components/charts/annotations#props-labelPadding-2)

Padding between the text and the border of the label background

Options:number

[labelBorderWidth](https://docs.evidence.dev/components/charts/annotations#props-labelBorderWidth-2)

The thickness of the border around the label (in pixels)

Options:number

[labelBorderRadius](https://docs.evidence.dev/components/charts/annotations#props-labelBorderRadius-2)

The radius of rounded corners on the label background (in pixels)

Options:number

[labelBorderColor](https://docs.evidence.dev/components/charts/annotations#props-labelBorderColor-2)

The color of the border around the label background

Options:CSS name \| hexademical \| RGB \| HSL

[labelBorderType](https://docs.evidence.dev/components/charts/annotations#props-labelBorderType-2)

The type of border around the label background (dashed or dotted)

Options:

solid dotted dashed

[fontSize](https://docs.evidence.dev/components/charts/annotations#props-fontSize-2)

The size of the font in the label

Options:number

[align](https://docs.evidence.dev/components/charts/annotations#props-align-2)

How to align the label to the symbol, and the text within the label

Options:

left center right

[bold](https://docs.evidence.dev/components/charts/annotations#props-bold-2)

Make the label text bold

Options:

true false

Default:false

[italic](https://docs.evidence.dev/components/charts/annotations#props-italic-2)

Make the label text italic

Options:

true false

Default:false

# [Reference Point](https://docs.evidence.dev/components/charts/annotations\#reference-point)

Reference points allow you to add labels on certain points to emphasize them in the chart. They can be produced by providing a specific x/y coordinate (e.g. `x="2021-05-01"` `y=11012`) or by providing a dataset (e.g. `anomalies`, `points`).

When a dataset is provided, `ReferencePoint` will generate multiple points - one for each row in the dataset. This can be helpful for plotting a large number of points with a succinct syntax.

## [Examples](https://docs.evidence.dev/components/charts/annotations\#examples-2)

### [Defined Point](https://docs.evidence.dev/components/charts/annotations\#defined-point)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferencePoint x="2019-07-01" y=6590 label="2019-07-01 : Big drop" labelPosition=bottom/>
</LineChart>
```

### [Points from Data](https://docs.evidence.dev/components/charts/annotations\#points-from-data)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferencePoint data={sales_drops} x=month y=sales label=label labelPosition=bottom align=right />
</LineChart>
```

### [Custom Styling](https://docs.evidence.dev/components/charts/annotations\#custom-styling-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferencePoint
        x="2019-07-01"
        y=6590
        label="2019-07-01 : Big drop"
        labelPosition=right
        color=negative
        symbolSize=16
        symbolBorderWidth=1
        symbolBorderColor=negative
        symbolOpacity=0.25
    />
</LineChart>
```

### [Label Positions](https://docs.evidence.dev/components/charts/annotations\#label-positions-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferencePoint x="2019-07-01" y=6590 label=top labelPosition=top/>
    <ReferencePoint x="2019-07-01" y=6590 label=right labelPosition=right/>
    <ReferencePoint x="2019-07-01" y=6590 label=bottom labelPosition=bottom/>
    <ReferencePoint x="2019-07-01" y=6590 label=left labelPosition=left/>
</LineChart>
```

#### [Multiline label](https://docs.evidence.dev/components/charts/annotations\#multiline-label)

A label with
line breaks in it
to allow longer text

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferencePoint x="2019-07-01" y=6590 labelPosition=bottom align=left>
        A label with
        line breaks in it
        to allow longer text
    </ReferencePoint>
</LineChart>
```

### [Colours](https://docs.evidence.dev/components/charts/annotations\#colours-2)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <ReferencePoint x="2019-03-01" y=3000 color=info label=info />
    <ReferencePoint x="2019-09-01" y=3000 color=negative label=negative />
    <ReferencePoint x="2020-03-01" y=3000 color=warning label=warning />
    <ReferencePoint x="2020-09-01" y=3000 color=positive label=positive />
    <ReferencePoint x="2021-03-01" y=3000 color=base-content-muted label=base-content-muted />
    <ReferencePoint x="2021-09-01" y=3000 color=#63178f label=custom />
</LineChart>
```

## [Options](https://docs.evidence.dev/components/charts/annotations\#options-2)

### [Defining Values Inline](https://docs.evidence.dev/components/charts/annotations\#defining-values-inline-2)

[x](https://docs.evidence.dev/components/charts/annotations#props-x-3)

x coordinate value where the point will be plotted

Options:number \| string \| date

[y](https://docs.evidence.dev/components/charts/annotations#props-y-3)

y coordinate value where the point will be plotted

Options:number \| string \| date

[label](https://docs.evidence.dev/components/charts/annotations#props-label-5)

Required

Text to show as label for the point

Options:string

### [Supplying a Dataset](https://docs.evidence.dev/components/charts/annotations\#supplying-a-dataset-2)

[data](https://docs.evidence.dev/components/charts/annotations#props-data-3)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/annotations#props-x-4)

Column containing x-axis values for points

Options:column name

[y](https://docs.evidence.dev/components/charts/annotations#props-y-4)

Column containing y-axis values for points

Options:column name

[label](https://docs.evidence.dev/components/charts/annotations#props-label-6)

Required

Column containing a label to use for each line

Options:column name

### [Styling](https://docs.evidence.dev/components/charts/annotations\#styling-2)

[color](https://docs.evidence.dev/components/charts/annotations#props-color-3)

Color to override default line and label colors

Options:CSS name \| hexademical \| RGB \| HSLDefault:base-content-muted

[labelColor](https://docs.evidence.dev/components/charts/annotations#props-labelColor-4)

Color to override default label color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[labelWidth](https://docs.evidence.dev/components/charts/annotations#props-labelWidth)

The width available for the label. If text is longer than this width, it will wrap to new lines.

Options:fit \| string \| numberDefault:fit

[labelPadding](https://docs.evidence.dev/components/charts/annotations#props-labelPadding-3)

Padding between the text and the border of the label background

Options:number

[labelPosition](https://docs.evidence.dev/components/charts/annotations#props-labelPosition-3)

Where the label will appear relative to the point

Options:

top right bottom left

Default:top

[labelBackgroundColor](https://docs.evidence.dev/components/charts/annotations#props-labelBackgroundColor-2)

The color of the background behind the label

Options:CSS name \| hexademical \| RGB \| HSLDefault:hsla(360, 100%, 100%, 0.7)

[labelBorderWidth](https://docs.evidence.dev/components/charts/annotations#props-labelBorderWidth-3)

The thickness of the border around the label (in pixels)

Options:number

[labelBorderRadius](https://docs.evidence.dev/components/charts/annotations#props-labelBorderRadius-3)

The radius of rounded corners on the label background (in pixels)

Options:number

[labelBorderColor](https://docs.evidence.dev/components/charts/annotations#props-labelBorderColor-3)

The color of the border around the label background

Options:CSS name \| hexademical \| RGB \| HSL

[labelBorderType](https://docs.evidence.dev/components/charts/annotations#props-labelBorderType-3)

The type of border around the label background (dashed or dotted)

Options:

solid dotted dashed

[fontSize](https://docs.evidence.dev/components/charts/annotations#props-fontSize-3)

The size of the font in the label

Options:number

[align](https://docs.evidence.dev/components/charts/annotations#props-align-3)

How to align the label to the symbol, and the text within the label

Options:

left center right

[bold](https://docs.evidence.dev/components/charts/annotations#props-bold-3)

Make the label text bold

Options:

true false

Default:false

[italic](https://docs.evidence.dev/components/charts/annotations#props-italic-3)

Make the label text italic

Options:

true false

Default:false

[symbol](https://docs.evidence.dev/components/charts/annotations#props-symbol)

The type of symbol used to mark the x/y coordinate(s)

Options:

circle rect roundRect triangle diamond pin arrow none

Default:circle

[symbolColor](https://docs.evidence.dev/components/charts/annotations#props-symbolColor)

Color to override default symbol color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[symbolSize](https://docs.evidence.dev/components/charts/annotations#props-symbolSize)

The size of the symbol

Options:numberDefault:8

[symbolOpacity](https://docs.evidence.dev/components/charts/annotations#props-symbolOpacity)

The opacity of the symbol

Options:number

[symbolBorderWidth](https://docs.evidence.dev/components/charts/annotations#props-symbolBorderWidth)

The width of the border around the symbol

Options:number

[symbolBorderColor](https://docs.evidence.dev/components/charts/annotations#props-symbolBorderColor)

The color of the border around the symbol

Options:CSS name \| hexademical \| RGB \| HSL

[preserveWhitespace](https://docs.evidence.dev/components/charts/annotations#props-preserveWhitespace)

When true, stops multiline labels from having whitespace at the start/end of lines trimmed

Options:

true false

Default:false

# [Callout](https://docs.evidence.dev/components/charts/annotations\#callout)

Callouts are very similar to reference points, just with different default styling to optimize them for slightly different use cases. Callouts allow you to add a long label somewhere on a chart to describe a trend or provide insight on the data. They can be produced by providing a specific x/y coordinate (e.g. `x="2021-05-01"` `y=11012`) or by providing a dataset (e.g. `anomalies`, `points`).

When a dataset is provided, `Callout` will generate multiple points - one for each row in the dataset. This can be helpful for plotting a large number of points with a succinct syntax.

## [Examples](https://docs.evidence.dev/components/charts/annotations\#examples-3)

### [Defined Point](https://docs.evidence.dev/components/charts/annotations\#defined-point-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <Callout x="2019-07-01" y=6590 label="Sales really dropped here" labelPosition=bottom/>
</LineChart>
```

### [Points from Data](https://docs.evidence.dev/components/charts/annotations\#points-from-data-1)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <Callout data={sales_drops} x=month y=sales label=label labelPosition=bottom align=right />
</LineChart>
```

### [Custom Styling](https://docs.evidence.dev/components/charts/annotations\#custom-styling-2)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <Callout
        x="2019-07-01"
        y=6590
        label="Sales really dropped here"
        labelPosition=right
        color=negative
        symbolSize=16
        symbolBorderWidth=1
        symbolBorderColor=negative
        symbolOpacity=0.25
    />
</LineChart>
```

### [Label Positions](https://docs.evidence.dev/components/charts/annotations\#label-positions-2)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <Callout x="2019-07-01" y=6590 label=top labelPosition=top/>
    <Callout x="2019-07-01" y=6590 label=right labelPosition=right/>
    <Callout x="2019-07-01" y=6590 label=bottom labelPosition=bottom/>
    <Callout x="2019-07-01" y=6590 label=left labelPosition=left/>
</LineChart>
```

#### [Multiline label](https://docs.evidence.dev/components/charts/annotations\#multiline-label-1)

Callout
with
line
breaks

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <Callout x="2019-07-01" y=6590 labelPosition=bottom align=left>
        Callout
        with
        line
        breaks
    </Callout>
</LineChart>
```

### [Colours](https://docs.evidence.dev/components/charts/annotations\#colours-3)

```text-sm html
<LineChart data={orders_by_month} x=month y=sales yFmt=usd0>
    <Callout x="2019-03-01" y=3000 color=info label=info />
    <Callout x="2019-09-01" y=3000 color=negative label=negative />
    <Callout x="2020-03-01" y=3000 color=warning label=warning />
    <Callout x="2020-09-01" y=3000 color=positive label=positive />
    <Callout x="2021-03-01" y=3000 color=base-content-muted label=base-content-muted />
    <Callout x="2021-09-01" y=3000 color=#63178f label=custom />
</LineChart>
```

## [Options](https://docs.evidence.dev/components/charts/annotations\#options-3)

### [Defining Values Inline](https://docs.evidence.dev/components/charts/annotations\#defining-values-inline-3)

[x](https://docs.evidence.dev/components/charts/annotations#props-x-5)

x coordinate value where the point will be plotted

Options:number \| string \| date

[y](https://docs.evidence.dev/components/charts/annotations#props-y-5)

y coordinate value where the point will be plotted

Options:number \| string \| date

[label](https://docs.evidence.dev/components/charts/annotations#props-label-7)

Required

Text to show as label for the point

Options:string

### [Supplying a Dataset](https://docs.evidence.dev/components/charts/annotations\#supplying-a-dataset-3)

[data](https://docs.evidence.dev/components/charts/annotations#props-data-4)

Required

Query name, wrapped in curly braces

Options:query name

[x](https://docs.evidence.dev/components/charts/annotations#props-x-6)

Column containing x-axis values for points

Options:column name

[y](https://docs.evidence.dev/components/charts/annotations#props-y-6)

Column containing y-axis values for points

Options:column name

[label](https://docs.evidence.dev/components/charts/annotations#props-label-8)

Required

Column containing a label to use for each line

Options:column name

### [Styling](https://docs.evidence.dev/components/charts/annotations\#styling-3)

[color](https://docs.evidence.dev/components/charts/annotations#props-color-4)

Color to override default line and label colors

Options:CSS name \| hexademical \| RGB \| HSLDefault:base-content-muted

[labelColor](https://docs.evidence.dev/components/charts/annotations#props-labelColor-5)

Color to override default label color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[labelWidth](https://docs.evidence.dev/components/charts/annotations#props-labelWidth-2)

The width available for the label. If text is longer than this width, it will wrap to new lines.

Options:fit \| string \| numberDefault:fit

[labelPadding](https://docs.evidence.dev/components/charts/annotations#props-labelPadding-4)

Padding between the text and the border of the label background

Options:number

[labelPosition](https://docs.evidence.dev/components/charts/annotations#props-labelPosition-4)

Where the label will appear relative to the point

Options:

top right bottom left

Default:top

[labelBackgroundColor](https://docs.evidence.dev/components/charts/annotations#props-labelBackgroundColor-3)

The color of the background behind the label

Options:CSS name \| hexademical \| RGB \| HSLDefault:hsla(360, 100%, 100%, 0.7)

[labelBorderWidth](https://docs.evidence.dev/components/charts/annotations#props-labelBorderWidth-4)

The thickness of the border around the label (in pixels)

Options:number

[labelBorderRadius](https://docs.evidence.dev/components/charts/annotations#props-labelBorderRadius-4)

The radius of rounded corners on the label background (in pixels)

Options:number

[labelBorderColor](https://docs.evidence.dev/components/charts/annotations#props-labelBorderColor-4)

The color of the border around the label background

Options:CSS name \| hexademical \| RGB \| HSL

[labelBorderType](https://docs.evidence.dev/components/charts/annotations#props-labelBorderType-4)

The type of border around the label background (dashed or dotted)

Options:

solid dotted dashed

[fontSize](https://docs.evidence.dev/components/charts/annotations#props-fontSize-4)

The size of the font in the label

Options:number

[align](https://docs.evidence.dev/components/charts/annotations#props-align-4)

How to align the label to the symbol, and the text within the label

Options:

left center right

[bold](https://docs.evidence.dev/components/charts/annotations#props-bold-4)

Make the label text bold

Options:

true false

Default:false

[italic](https://docs.evidence.dev/components/charts/annotations#props-italic-4)

Make the label text italic

Options:

true false

Default:false

[symbol](https://docs.evidence.dev/components/charts/annotations#props-symbol-2)

The type of symbol used to mark the x/y coordinate(s)

Options:

circle rect roundRect triangle diamond pin arrow none

Default:circle

[symbolColor](https://docs.evidence.dev/components/charts/annotations#props-symbolColor-2)

Color to override default symbol color. If used, takes precedence over \`color\`

Options:CSS name \| hexademical \| RGB \| HSL

[symbolSize](https://docs.evidence.dev/components/charts/annotations#props-symbolSize-2)

The size of the symbol

Options:numberDefault:8

[symbolOpacity](https://docs.evidence.dev/components/charts/annotations#props-symbolOpacity-2)

The opacity of the symbol

Options:number

[symbolBorderWidth](https://docs.evidence.dev/components/charts/annotations#props-symbolBorderWidth-2)

The width of the border around the symbol

Options:number

[symbolBorderColor](https://docs.evidence.dev/components/charts/annotations#props-symbolBorderColor-2)

The color of the border around the symbol

Options:CSS name \| hexademical \| RGB \| HSL

[preserveWhitespace](https://docs.evidence.dev/components/charts/annotations#props-preserveWhitespace-2)

When true, stops multiline labels from having whitespace at the start/end of lines trimmed

Options:

true false

Default:false

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/charts/annotations/index.md)