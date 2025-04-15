Visual Encoding:

The Sankey diagram encodes each node of the raw data into a small rectangle. Different nodes are presented in different colors as far as possible. The label next to the small rectangle encodes the name of the node.

In addition, the edge between two small rectangles in the diagram encodes the link of the raw data. The width of edge is shown proportionally to the value of link.

Properties
series-sankey. type  = 'sankey'
string
series-sankey. id
string
Component ID, not specified by default. If specified, it can be used to refer the component in option or API.

series-sankey. name
string
Series name used for displaying in tooltip and filtering with legend, or updating data and configuration with setOption.

series-sankey. zlevel
number
zlevel value of all graphical elements in .

zlevel is used to make layers with Canvas. Graphical elements with different zlevel values will be placed in different Canvases, which is a common optimization technique. We can put those frequently changed elements (like those with animations) to a separate zlevel. Notice that too many Canvases will increase memory cost, and should be used carefully on mobile phones to avoid crash.

Canvases with bigger zlevel will be placed on Canvases with smaller zlevel.

series-sankey. z = 2
number
z value of all graphical elements in , which controls order of drawing graphical components. Components with smaller z values may be overwritten by those with larger z values.

z has a lower priority to zlevel, and will not create new Canvas.

series-sankey. left = 5%
stringnumber
Distance between sankey component and the left side of the container.

left can be a pixel value like 20; it can also be a percentage value relative to container width like '20%'; and it can also be 'left', 'center', or 'right'.

If the left value is set to be 'left', 'center', or 'right', then the component will be aligned automatically based on position.

series-sankey. top = 5%
stringnumber
Distance between sankey component and the top side of the container.

top can be a pixel value like 20; it can also be a percentage value relative to container width like '20%'; and it can also be 'top', 'middle', or 'bottom'.

If the top value is set to be 'top', 'middle', or 'bottom', then the component will be aligned automatically based on position.

series-sankey. right = 20%
stringnumber
Distance between sankey component and the right side of the container.

right can be a pixel value like 20; it can also be a percentage value relative to container width like '20%'.

series-sankey. bottom = 5%
stringnumber
Distance between sankey component and the bottom side of the container.

bottom can be a pixel value like 20; it can also be a percentage value relative to container width like '20%'.

series-sankey. width
stringnumber
Width of sankey component.

series-sankey. height
stringnumber
Height of sankey component.

series-sankey. nodeWidth = 20
number
The node width of rectangle in Sankey diagram.

series-sankey. nodeGap = 8
number
The gap between any two rectangles in each column of the Sankey diagram.

series-sankey. nodeAlign = 'justify'
string
Controls the horizontal alignment of nodes in the diagram.

May be:

left: initial nodes (those with no incoming links) are aligned to the left of the diagram.

right: terminal nodes (those with no outgoing links) are aligned to the right of the diagram.

justify: initial and terminal nodes are aligned on the left and right edges.

Note when orient is vertical, nodeAlign controls vertical alignment.

series-sankey. layoutIterations = 32
number
The iterations of layout, which is used to iteratively optimize the position of the nodes and edges in the Sankey diagram to reduce the overlapping between nodes and edges. The default value is 32. If you want the order of the nodes in the chart to be the same with the order in the original data, you can set the value to be 0.

series-sankey. orient = 'horizontal'
string
The layout direction of the nodes in the Sankey diagram, which can be horizontal from left to right or vertical from top to bottom. The corresponding parameter values ​​are horizontal or vertical.

series-sankey. draggable = true
boolean
The drag-and-drop interaction of the node, which is enabled by default. After opening, the user can drag any node in the Sankey diagram to any position. To turn this interaction off, simply set the value to false.

 series-sankey. edgeLabel
Object
Since v5.4.1

The label style of each edge/link.

 series-sankey.edgeLabel. show
boolean
Whether to show label.

 series-sankey.edgeLabel. distance = 5
number
Distance to the host graphic element.

 series-sankey.edgeLabel. rotate
number
Rotate label, from -90 degree to 90, positive value represents rotate anti-clockwise.

See: label rotation.

 series-sankey.edgeLabel. offset
Array
Whether to move text slightly. For example: [30, 40] means move 30 horizontally and move 40 vertically.

 series-sankey.edgeLabel. formatter
stringFunction
Data label formatter, which supports string template and callback function. In either form, \n is supported to represent a new line.

String template

Model variation includes:

{a}: series name.
{b}: the name of a data item.
{c}: the value of a data item.
{d}: the percent.
{@xxx}: the value of a dimension named 'xxx', for example, {@product} refers the value of 'product' dimension.
{@[n]}: the value of a dimension at the index of n, for example, {@[3]} refers the value at dimensions[3].
example:

formatter: '{b}: {d}'
Callback function

Callback function is in form of:

(params: Object|Array) => string
where params is the single dataset needed by formatter, which is formed as:

{
    componentType: 'series',
    // Series type
    seriesType: string,
    // Series index in option.series
    seriesIndex: number,
    // Series name
    seriesName: string,
    // Data name, or category name
    name: string,
    // Data index in input data array
    dataIndex: number,
    // Original data as input
    data: Object,
    // Value of data. In most series it is the same as data.
    // But in some series it is some part of the data (e.g., in map, radar)
    value: number|Array|Object,
    // encoding info of coordinate system
    // Key: coord, like ('x' 'y' 'radius' 'angle')
    // value: Must be an array, not null/undefined. Contain dimension indices, like:
    // {
    //     x: [2] // values on dimension index 2 are mapped to x axis.
    //     y: [0] // values on dimension index 0 are mapped to y axis.
    // }
    encode: Object,
    // dimension names list
    dimensionNames: Array<String>,
    // data dimension index, for example 0 or 1 or 2 ...
    // Only work in `radar` series.
    dimensionIndex: number,
    // Color of data
    color: string
}
How to use encode and dimensionNames?

When the dataset is like

dataset: {
    source: [
        ['Matcha Latte', 43.3, 85.8, 93.7],
        ['Milk Tea', 83.1, 73.4, 55.1],
        ['Cheese Cocoa', 86.4, 65.2, 82.5],
        ['Walnut Brownie', 72.4, 53.9, 39.1]
    ]
}
We can get the value of the y-axis via

params.value[params.encode.y[0]]
When the dataset is like

dataset: {
    dimensions: ['product', '2015', '2016', '2017'],
    source: [
        {product: 'Matcha Latte', '2015': 43.3, '2016': 85.8, '2017': 93.7},
        {product: 'Milk Tea', '2015': 83.1, '2016': 73.4, '2017': 55.1},
        {product: 'Cheese Cocoa', '2015': 86.4, '2016': 65.2, '2017': 82.5},
        {product: 'Walnut Brownie', '2015': 72.4, '2016': 53.9, '2017': 39.1}
    ]
}
We can get the value of the y-axis via

params.value[params.dimensionNames[params.encode.y[0]]]
 series-sankey.edgeLabel. color = '#fff'
Color
text color.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.edgeLabel. fontStyle = 'normal'
string
font style.

Options are:

'normal'
'italic'
'oblique'
 series-sankey.edgeLabel. fontWeight = 'normal'
stringnumber
font thick weight.

Options are:

'normal'
'bold'
'bolder'
'lighter'
100 | 200 | 300 | 400...
 series-sankey.edgeLabel. fontFamily = 'sans-serif'
string
font family.

Can also be 'serif' , 'monospace', ...

 series-sankey.edgeLabel. fontSize = 12
number
font size.

 series-sankey.edgeLabel. align
string
Horizontal alignment of text, automatic by default.

Options are:

'left'
'center'
'right'
If align is not set in rich, align in parent level will be used. For example:

{
    align: right,
    rich: {
        a: {
            // `align` is not set, then it will be right
        }
    }
}
 series-sankey.edgeLabel. verticalAlign
string
Vertical alignment of text, automatic by default.

Options are:

'top'
'middle'
'bottom'
If verticalAlign is not set in rich, verticalAlign in parent level will be used. For example:

{
    verticalAlign: bottom,
    rich: {
        a: {
            // `verticalAlign` is not set, then it will be bottom
        }
    }
}
 series-sankey.edgeLabel. lineHeight
number
Line height of the text fragment.

If lineHeight is not set in rich, lineHeight in parent level will be used. For example:

{
    lineHeight: 56,
    rich: {
        a: {
            // `lineHeight` is not set, then it will be 56
        }
    }
}
 series-sankey.edgeLabel. backgroundColor = 'transparent'
stringObject
Background color of the text fragment.

Can be color string, like '#123234', 'red', 'rgba(0,23,11,0.3)'.

Or image can be used, for example:

backgroundColor: {
    image: 'xxx/xxx.png'
    // It can be URL of a image,
    // or dataURI,
    // or HTMLImageElement,
    // or HTMLCanvasElement.
}
width or height can be specified when using background image, or auto adapted by default.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.edgeLabel. borderColor
Color
Border color of the text fragment.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.edgeLabel. borderWidth
number
Border width of the text fragment.

 series-sankey.edgeLabel. borderType = 'solid'
stringnumberArray
the text fragment border type.

Possible values are:

'solid'
'dashed'
'dotted'
Since v5.0.0, it can also be a number or a number array to specify the dash array of the line. With borderDashOffset , we can make the line style more flexible.

For example：

{

borderType: [5, 10],

borderDashOffset: 5
}
 series-sankey.edgeLabel. borderDashOffset
number
Since v5.0.0

To set the line dash offset. With borderType , we can make the line style more flexible.

Refer to MDN lineDashOffset for more details.

 series-sankey.edgeLabel. borderRadius
number
Border radius of the text fragment.

 series-sankey.edgeLabel. padding
numberArray
Padding of the text fragment, for example:

padding: [3, 4, 5, 6]: represents padding of [top, right, bottom, left].
padding: 4: represents padding: [4, 4, 4, 4].
padding: [3, 4]: represents padding: [3, 4, 3, 4].
Notice, width and height specifies the width and height of the content, without padding.

 series-sankey.edgeLabel. shadowColor = 'transparent'
Color
Shadow color of the text block.

 series-sankey.edgeLabel. shadowBlur
number
Show blur of the text block.

 series-sankey.edgeLabel. shadowOffsetX
number
Shadow X offset of the text block.

 series-sankey.edgeLabel. shadowOffsetY
number
Shadow Y offset of the text block.

 series-sankey.edgeLabel. width
number
Width of text block.

 series-sankey.edgeLabel. height
number
Height of text block.

 series-sankey.edgeLabel. textBorderColor
Color
Stroke color of the text.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.edgeLabel. textBorderWidth
number
Stroke line width of the text.

 series-sankey.edgeLabel. textBorderType = 'solid'
stringnumberArray
Stroke line type of the text.

Possible values are:

'solid'
'dashed'
'dotted'
Since v5.0.0, it can also be a number or a number array to specify the dash array of the line. With textBorderDashOffset , we can make the line style more flexible.

For example：

{

textBorderType: [5, 10],

textBorderDashOffset: 5
}
 series-sankey.edgeLabel. textBorderDashOffset
number
Since v5.0.0

To set the line dash offset. With textBorderType , we can make the line style more flexible.

Refer to MDN lineDashOffset for more details.

 series-sankey.edgeLabel. textShadowColor = 'transparent'
Color
Shadow color of the text itself.

 series-sankey.edgeLabel. textShadowBlur
number
Shadow blue of the text itself.

 series-sankey.edgeLabel. textShadowOffsetX
number
Shadow X offset of the text itself.

 series-sankey.edgeLabel. textShadowOffsetY
number
Shadow Y offset of the text itself.

 series-sankey.edgeLabel. overflow = 'none'
string
Determine how to display the text when it's overflow. Available when width is set.

'truncate' Truncate the text and trailing with ellipsis.
'break' Break by word
'breakAll' Break by character.
 series-sankey.edgeLabel. ellipsis = '...'
string
Ellipsis to be displayed when overflow is set to truncate.

'truncate' Truncate the overflow lines.
  series-sankey.edgeLabel. rich
Object
"Rich text styles" can be defined in this rich property. For example:

label: {
    // Styles defined in 'rich' can be applied to some fragments
    // of text by adding some markers to those fragment, like
    // `{styleName|text content text content}`.
    // `'\n'` is the newline character.
    formatter: [
        '{a|Style "a" is applied to this snippet}'
        '{b|Style "b" is applied to this snippet}This snippet use default style{x|use style "x"}'
    ].join('\n'),

    rich: {
        a: {
            color: 'red',
            lineHeight: 10
        },
        b: {
            backgroundColor: {
                image: 'xxx/xxx.jpg'
            },
            height: 40
        },
        x: {
            fontSize: 18,
            fontFamily: 'Microsoft YaHei',
            borderColor: '#449933',
            borderRadius: 4
        },
        ...
    }
}
For more details, see Rich Text please.

Properties
{ <style_name> }
 series-sankey. levels
Array
The setting of each layer of Sankey diagram. Can be set layer by layer, as follows:

levels: [{
    depth: 0,
    itemStyle: {
        color: '#fbb4ae'
    },
    lineStyle: {
        color: 'source',
        opacity: 0.6
    }
}, {
    depth: 1,
    itemStyle: {
        color: '#b3cde3'
    },
    lineStyle: {
        color: 'source',
        opacity: 0.6
    }
}]
You can also only set a certain layer:

levels: [{
    depth: 3,
    itemStyle: {
        color: '#fbb4ae'
    },
    lineStyle: {
        color: 'source',
        opacity: 0.6
    }
}]
 series-sankey.levels. depth
number
Specify which layer is set, value starts from 0.

  series-sankey.levels. label
Object
Properties
{ show , position , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.levels. edgeLabel
Object
Since v5.4.1

The label style of each edge/link.

Properties
{ show , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.levels. itemStyle
Object
Properties
{ color , borderColor , borderWidth , borderType , borderDashOffset , borderCap , borderJoin , borderMiterLimit , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY , opacity }
  series-sankey.levels. lineStyle
Object
Properties
{ color , opacity , curveness , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY }
  series-sankey.levels. emphasis
Object
Properties
{ disabled , label , edgeLabel , itemStyle , lineStyle }
  series-sankey.levels. blur
Object
Since v5.0.0

Properties
{ label , edgeLabel , itemStyle , lineStyle }
  series-sankey.levels. select
Object
Since v5.0.0

Properties
{ disabled , label , edgeLabel , itemStyle , lineStyle }
 series-sankey. label
Object
label describes the text label style in each rectangular node.

 series-sankey.label. show = true
boolean
Whether to show label.

 series-sankey.label. position = 'right'
stringArray
Label position.

Followings are the options:

[x, y]

Use relative percentage, or absolute pixel values to represent position of label relative to top-left corner of bounding box. For example:

  // Absolute pixel values
  position: [10, 10],
  // Relative percentage
  position: ['50%', '50%']
'top'

'left'
'right'
'bottom'
'inside'
'insideLeft'
'insideRight'
'insideTop'
'insideBottom'
'insideTopLeft'
'insideBottomLeft'
'insideTopRight'
'insideBottomRight'
See: label position.

 series-sankey.label. distance = 5
number
Distance to the host graphic element.

It is valid only when position is string value (like 'top'、'insideRight').

See: label position.

 series-sankey.label. rotate
number
Rotate label, from -90 degree to 90, positive value represents rotate anti-clockwise.

See: label rotation.

 series-sankey.label. offset
Array
Whether to move text slightly. For example: [30, 40] means move 30 horizontally and move 40 vertically.

 series-sankey.label. minMargin
number
Since v5.0.0

Minimal margin between labels. Used when label has layout.

 series-sankey.label. formatter
stringFunction
Data label formatter, which supports string template and callback function. In either form, \n is supported to represent a new line.

String template

Model variation includes:

{a}: series name.
{b}: the name of a data item.
{c}: the value of a data item.
{d}: the percent.
{@xxx}: the value of a dimension named 'xxx', for example, {@product} refers the value of 'product' dimension.
{@[n]}: the value of a dimension at the index of n, for example, {@[3]} refers the value at dimensions[3].
example:

formatter: '{b}: {d}'
Callback function

Callback function is in form of:

(params: Object|Array) => string
where params is the single dataset needed by formatter, which is formed as:

{
    componentType: 'series',
    // Series type
    seriesType: string,
    // Series index in option.series
    seriesIndex: number,
    // Series name
    seriesName: string,
    // Data name, or category name
    name: string,
    // Data index in input data array
    dataIndex: number,
    // Original data as input
    data: Object,
    // Value of data. In most series it is the same as data.
    // But in some series it is some part of the data (e.g., in map, radar)
    value: number|Array|Object,
    // encoding info of coordinate system
    // Key: coord, like ('x' 'y' 'radius' 'angle')
    // value: Must be an array, not null/undefined. Contain dimension indices, like:
    // {
    //     x: [2] // values on dimension index 2 are mapped to x axis.
    //     y: [0] // values on dimension index 0 are mapped to y axis.
    // }
    encode: Object,
    // dimension names list
    dimensionNames: Array<String>,
    // data dimension index, for example 0 or 1 or 2 ...
    // Only work in `radar` series.
    dimensionIndex: number,
    // Color of data
    color: string
}
How to use encode and dimensionNames?

When the dataset is like

dataset: {
    source: [
        ['Matcha Latte', 43.3, 85.8, 93.7],
        ['Milk Tea', 83.1, 73.4, 55.1],
        ['Cheese Cocoa', 86.4, 65.2, 82.5],
        ['Walnut Brownie', 72.4, 53.9, 39.1]
    ]
}
We can get the value of the y-axis via

params.value[params.encode.y[0]]
When the dataset is like

dataset: {
    dimensions: ['product', '2015', '2016', '2017'],
    source: [
        {product: 'Matcha Latte', '2015': 43.3, '2016': 85.8, '2017': 93.7},
        {product: 'Milk Tea', '2015': 83.1, '2016': 73.4, '2017': 55.1},
        {product: 'Cheese Cocoa', '2015': 86.4, '2016': 65.2, '2017': 82.5},
        {product: 'Walnut Brownie', '2015': 72.4, '2016': 53.9, '2017': 39.1}
    ]
}
We can get the value of the y-axis via

params.value[params.dimensionNames[params.encode.y[0]]]
 series-sankey.label. color = '#fff'
Color
text color.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.label. fontStyle = 'normal'
string
font style.

Options are:

'normal'
'italic'
'oblique'
 series-sankey.label. fontWeight = 'normal'
stringnumber
font thick weight.

Options are:

'normal'
'bold'
'bolder'
'lighter'
100 | 200 | 300 | 400...
 series-sankey.label. fontFamily = 'sans-serif'
string
font family.

Can also be 'serif' , 'monospace', ...

 series-sankey.label. fontSize = 12
number
font size.

 series-sankey.label. align
string
Horizontal alignment of text, automatic by default.

Options are:

'left'
'center'
'right'
If align is not set in rich, align in parent level will be used. For example:

{
    align: right,
    rich: {
        a: {
            // `align` is not set, then it will be right
        }
    }
}
 series-sankey.label. verticalAlign
string
Vertical alignment of text, automatic by default.

Options are:

'top'
'middle'
'bottom'
If verticalAlign is not set in rich, verticalAlign in parent level will be used. For example:

{
    verticalAlign: bottom,
    rich: {
        a: {
            // `verticalAlign` is not set, then it will be bottom
        }
    }
}
 series-sankey.label. lineHeight
number
Line height of the text fragment.

If lineHeight is not set in rich, lineHeight in parent level will be used. For example:

{
    lineHeight: 56,
    rich: {
        a: {
            // `lineHeight` is not set, then it will be 56
        }
    }
}
 series-sankey.label. backgroundColor = 'transparent'
stringObject
Background color of the text fragment.

Can be color string, like '#123234', 'red', 'rgba(0,23,11,0.3)'.

Or image can be used, for example:

backgroundColor: {
    image: 'xxx/xxx.png'
    // It can be URL of a image,
    // or dataURI,
    // or HTMLImageElement,
    // or HTMLCanvasElement.
}
width or height can be specified when using background image, or auto adapted by default.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.label. borderColor
Color
Border color of the text fragment.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.label. borderWidth
number
Border width of the text fragment.

 series-sankey.label. borderType = 'solid'
stringnumberArray
the text fragment border type.

Possible values are:

'solid'
'dashed'
'dotted'
Since v5.0.0, it can also be a number or a number array to specify the dash array of the line. With borderDashOffset , we can make the line style more flexible.

For example：

{

borderType: [5, 10],

borderDashOffset: 5
}
 series-sankey.label. borderDashOffset
number
Since v5.0.0

To set the line dash offset. With borderType , we can make the line style more flexible.

Refer to MDN lineDashOffset for more details.

 series-sankey.label. borderRadius
number
Border radius of the text fragment.

 series-sankey.label. padding
numberArray
Padding of the text fragment, for example:

padding: [3, 4, 5, 6]: represents padding of [top, right, bottom, left].
padding: 4: represents padding: [4, 4, 4, 4].
padding: [3, 4]: represents padding: [3, 4, 3, 4].
Notice, width and height specifies the width and height of the content, without padding.

 series-sankey.label. shadowColor = 'transparent'
Color
Shadow color of the text block.

 series-sankey.label. shadowBlur
number
Show blur of the text block.

 series-sankey.label. shadowOffsetX
number
Shadow X offset of the text block.

 series-sankey.label. shadowOffsetY
number
Shadow Y offset of the text block.

 series-sankey.label. width
number
Width of text block.

 series-sankey.label. height
number
Height of text block.

 series-sankey.label. textBorderColor
Color
Stroke color of the text.

If set as 'inherit', the color will assigned as visual color, such as series color.

 series-sankey.label. textBorderWidth
number
Stroke line width of the text.

 series-sankey.label. textBorderType = 'solid'
stringnumberArray
Stroke line type of the text.

Possible values are:

'solid'
'dashed'
'dotted'
Since v5.0.0, it can also be a number or a number array to specify the dash array of the line. With textBorderDashOffset , we can make the line style more flexible.

For example：

{

textBorderType: [5, 10],

textBorderDashOffset: 5
}
 series-sankey.label. textBorderDashOffset
number
Since v5.0.0

To set the line dash offset. With textBorderType , we can make the line style more flexible.

Refer to MDN lineDashOffset for more details.

 series-sankey.label. textShadowColor = 'transparent'
Color
Shadow color of the text itself.

 series-sankey.label. textShadowBlur
number
Shadow blue of the text itself.

 series-sankey.label. textShadowOffsetX
number
Shadow X offset of the text itself.

 series-sankey.label. textShadowOffsetY
number
Shadow Y offset of the text itself.

 series-sankey.label. overflow = 'none'
string
Determine how to display the text when it's overflow. Available when width is set.

'truncate' Truncate the text and trailing with ellipsis.
'break' Break by word
'breakAll' Break by character.
 series-sankey.label. ellipsis = '...'
string
Ellipsis to be displayed when overflow is set to truncate.

'truncate' Truncate the overflow lines.
  series-sankey.label. rich
Object
"Rich text styles" can be defined in this rich property. For example:

label: {
    // Styles defined in 'rich' can be applied to some fragments
    // of text by adding some markers to those fragment, like
    // `{styleName|text content text content}`.
    // `'\n'` is the newline character.
    formatter: [
        '{a|Style "a" is applied to this snippet}'
        '{b|Style "b" is applied to this snippet}This snippet use default style{x|use style "x"}'
    ].join('\n'),

    rich: {
        a: {
            color: 'red',
            lineHeight: 10
        },
        b: {
            backgroundColor: {
                image: 'xxx/xxx.jpg'
            },
            height: 40
        },
        x: {
            fontSize: 18,
            fontFamily: 'Microsoft YaHei',
            borderColor: '#449933',
            borderRadius: 4
        },
        ...
    }
}
For more details, see Rich Text please.

Properties
{ <style_name> }
 series-sankey. labelLayout
ObjectFunction
Since v5.0.0

Unified layout configuration of labels.

It provide a chance to adjust the labels' (x, y) position, alignment based on the original layout each series provides.

This option can be a callback with following parameters.

// corresponding index of data
dataIndex: number
// corresponding type of data. Only available in graph, in which it can be 'node' or 'edge'
dataType?: string
// corresponding index of series
seriesIndex: number
// Displayed text of label.
text: string
// Bounding rectangle of label.
labelRect: {x: number, y: number, width: number, height: number}
// Horizontal alignment of label.
align: 'left' | 'center' | 'right'
// Vertical alignment of label.
verticalAlign: 'top' | 'middle' | 'bottom'
// Bounding rectangle of the element corresponding to.
rect: {x: number, y: number, width: number, height: number}
// Default points array of labelLine. Currently only provided in pie and funnel series.
// It's null in other series.
labelLinePoints?: number[][]
Example:

Align the labels on the right. Left 10px margin to the edge.

labelLayout(params) {
    return {
        x: params.rect.x + 10,
        y: params.rect.y + params.rect.height / 2,
        verticalAlign: 'middle',
        align: 'left'
    }
}
Set the text size based on the size of element bounding rectangle.


labelLayout(params) {
    return {
        fontSize: Math.max(params.rect.width / 10, 5)
    };
}
 series-sankey.labelLayout. hideOverlap
boolean
If hide the overlapped labels.

The following example shows how to hide the overlapped labels in graph automatically when zooming.


 series-sankey.labelLayout. moveOverlap
string
If move the overlapped labels to avoid overlapping.

Currently supported configurations:

'shiftX' Place the labels on horizontal direction sequencely, used when aligned horizontally.
'shiftY' Place the labels on vertical direction sequencely, used when aligned vertically.
The following example shows how to use moverOverlap: 'shiftY' to place the labels aligned vertically.


 series-sankey.labelLayout. x
numberstring
The x position of the label. Support absolute pixel values ​​or relative values ​​such as '20%'.

 series-sankey.labelLayout. y
numberstring
The y position of the label. Support absolute pixel values ​​or relative values ​​such as '20%'.

 series-sankey.labelLayout. dx
number
The pixel offset of the label in the x direction. Can be used with x.

 series-sankey.labelLayout. dy
number
The pixel offset of the label in the y direction. Can be used with y

 series-sankey.labelLayout. rotate
number
Label rotation angle.

 series-sankey.labelLayout. width
number
The width of displayed label. It can be used with overflow to constraint the label in a fixed width.

 series-sankey.labelLayout. height
number
The height of displayed label.

 series-sankey.labelLayout. align
string
The horizontal alignment of the label. Can be 'left', 'center', 'right'.

 series-sankey.labelLayout. verticalAlign
string
The vertical alignment of the label. Can be 'top', 'middle', 'bottom'.

 series-sankey.labelLayout. fontSize
number
The text size of the label.

 series-sankey.labelLayout. draggable
boolean
Whether to allow the user to adjust the position by dragging.

 series-sankey.labelLayout. labelLinePoints
Array
The array of the three points of the label guide line. The format is:

[[x, y], [x, y], [x, y]]
It is often used in pie charts to fine-tune the guide line that has been calculated. Usually not recommended to set it in other situations.

 series-sankey. itemStyle
Object
The style of node rectangle in Sankey diagram.

 series-sankey.itemStyle. color
Color
color. Color is taken from option.color Palette by default.

Supports setting as solid color using rgb(255,255,255), rgba(255,255,255,1), #fff, etc. Also supports setting as gradient color and pattern fill, see option.color for details

 series-sankey.itemStyle. borderColor = 'none'
Color
border color, whose format is similar to that of color.

 series-sankey.itemStyle. borderWidth = 1
number
border width. No border when it is set to be 0.

border width. No border when it is set to be 0.

 series-sankey.itemStyle. borderType = 'solid'
stringnumberArray
border type.

Possible values are:

'solid'
'dashed'
'dotted'
Since v5.0.0, it can also be a number or a number array to specify the dash array of the line. With borderDashOffset , we can make the line style more flexible.

For example：

{

borderType: [5, 10],

borderDashOffset: 5
}
 series-sankey.itemStyle. borderDashOffset
number
Since v5.0.0

To set the line dash offset. With borderType , we can make the line style more flexible.

Refer to MDN lineDashOffset for more details.

 series-sankey.itemStyle. borderCap = 'butt'
string
Since v5.0.0

To specify how to draw the end points of the line. Possible values are:

'butt': The ends of lines are squared off at the endpoints.
'round': The ends of lines are rounded.
'square': The ends of lines are squared off by adding a box with an equal width and half the height of the line's thickness.
Default value is 'butt'. Refer to MDN lineCap for more details.

 series-sankey.itemStyle. borderJoin = 'bevel'
string
Since v5.0.0

To determine the shape used to join two line segments where they meet.

Possible values are:

'bevel': Fills an additional triangular area between the common endpoint of connected segments, and the separate outside rectangular corners of each segment.
'round': Rounds off the corners of a shape by filling an additional sector of disc centered at the common endpoint of connected segments. The radius for these rounded corners is equal to the line width.
'miter': Connected segments are joined by extending their outside edges to connect at a single point, with the effect of filling an additional lozenge-shaped area. This setting is affected by the borderMiterLimit property.
Default value is 'bevel'. Refer to MDN lineJoin for more details.

 series-sankey.itemStyle. borderMiterLimit = 10
number
Since v5.0.0

To set the miter limit ratio. Only works when borderJoin is set as miter.

Default value is 10. Negative、0、Infinity and NaN values are ignored.

Refer to MDN miterLimit for more details.

 series-sankey.itemStyle. shadowBlur
number
Size of shadow blur. This attribute should be used along with shadowColor,shadowOffsetX, shadowOffsetY to set shadow to component.

For example:

{
    shadowColor: 'rgba(0, 0, 0, 0.5)',
    shadowBlur: 10
}
 series-sankey.itemStyle. shadowColor
Color
Shadow color. Support same format as color.

 series-sankey.itemStyle. shadowOffsetX
number
Offset distance on the horizontal direction of shadow.

 series-sankey.itemStyle. shadowOffsetY
number
Offset distance on the vertical direction of shadow.

 series-sankey.itemStyle. opacity
number
Opacity of the component. Supports value from 0 to 1, and the component will not be drawn when set to 0.

  series-sankey.itemStyle. decal
Object
The style of the decal pattern. It works only if aria.enabled and aria.decal.show are both set to be true.

If it is set to be 'none', no decal will be used.

Properties
{ symbol , symbolSize , symbolKeepAspect , color , backgroundColor , dashArrayX , dashArrayY , rotation , maxTileWidth , maxTileHeight }
 series-sankey.itemStyle. borderRadius
numberArray
Since v5.5.1

The radius of rounded corner. Its unit is px. And it supports use array to respectively specify the 4 corner radiuses.

For example:

borderRadius: 5, // consistently set the size of 4 rounded corners
borderRadius: [5, 5, 0, 0] // (clockwise upper left, upper right, bottom right and bottom left)
 series-sankey. lineStyle
Object
The edge style of Sankey diagram

 series-sankey.lineStyle. color = '#314656'
Color
The color of the edge in Sankey diagram.

'source': use source node color.
'target': use target node color.
'gradient': gradient color between source node and target node. (Since v5.0.0)
 series-sankey.lineStyle. opacity = 0.2
number
The opacity of the edge in Sankey diagram.

 series-sankey.lineStyle. curveness = 0.5
number
The curveness of the edge in Sankey diagram.

 series-sankey.lineStyle. shadowBlur
number
Size of shadow blur. This attribute should be used along with shadowColor,shadowOffsetX, shadowOffsetY to set shadow to component.

For example:

{
    shadowColor: 'rgba(0, 0, 0, 0.5)',
    shadowBlur: 10
}
 series-sankey.lineStyle. shadowColor
Color
Shadow color. Support same format as color.

 series-sankey.lineStyle. shadowOffsetX
number
Offset distance on the horizontal direction of shadow.

 series-sankey.lineStyle. shadowOffsetY
number
Offset distance on the vertical direction of shadow.

 series-sankey. emphasis
Object
Configurations of emphasis state.

 series-sankey.emphasis. disabled
boolean
Since v5.3.0

Whether to disable the emphasis state.

When emphasis state is disabled. There will be no highlight effect when the mouse hovered the element, tooltip is triggered, or the legend is hovered. It can be used to improve interaction fluency when there are massive graphic elements.

 series-sankey.emphasis. focus = 'none'
string
Since v5.0.0

When the data is highlighted, whether to fade out of other data to focus the highlighted. The following configurations are supported:

'none' Do not fade out other data, it's by default.
'self' Only focus (not fade out) the element of the currently highlighted data.
'series' Focus on all elements of the series which the currently highlighted data belongs to.
'adjacency' Focus on the elements of adjacent nodes and edges in the graph.
'trajectory' Focus on all the elements connected to the node or edge in the graph. (Since v5.4.3)
Example:

emphasis: {
    focus: 'series',
    blurScope: 'coordinateSystem'
}

 series-sankey.emphasis. blurScope = 'coordinateSystem'
string
Since v5.0.0

The range of fade out when focus is enabled. Support the following configurations

'coordinateSystem'
'series'
'global'
  series-sankey.emphasis. label
Object
Properties
{ show , position , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.emphasis. edgeLabel
Object
Since v5.4.1

The label style of each edge/link.

Properties
{ show , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.emphasis. itemStyle
Object
Properties
{ color , borderColor , borderWidth , borderType , borderDashOffset , borderCap , borderJoin , borderMiterLimit , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY , opacity }
  series-sankey.emphasis. lineStyle
Object
Properties
{ color , opacity , curveness , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY }
 series-sankey. blur
Object
Since v5.0.0

Configurations of blur state. Available when emphasis.focus is set.

  series-sankey.blur. label
Object
Properties
{ show , position , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.blur. edgeLabel
Object
Since v5.4.1

The label style of each edge/link.

Properties
{ show , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.blur. itemStyle
Object
Properties
{ color , borderColor , borderWidth , borderType , borderDashOffset , borderCap , borderJoin , borderMiterLimit , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY , opacity }
  series-sankey.blur. lineStyle
Object
Properties
{ color , opacity , curveness , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY }
 series-sankey. select
Object
Since v5.0.0

Configurations of selected state. Available when selectedMode is set.

 series-sankey.select. disabled
boolean
Since v5.3.0

If data can be selected. Available when selectedMode is used. Can be used to disable selection for part of the data.

  series-sankey.select. label
Object
Properties
{ show , position , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.select. edgeLabel
Object
Since v5.4.1

The label style of each edge/link.

Properties
{ show , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.select. itemStyle
Object
Properties
{ color , borderColor , borderWidth , borderType , borderDashOffset , borderCap , borderJoin , borderMiterLimit , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY , opacity }
  series-sankey.select. lineStyle
Object
Properties
{ color , opacity , curveness , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY }
series-sankey. selectedMode
booleanstring
Since v5.0.0

Selected mode. It is disabled by default, and you may set it to be true to enable it.

Besides, it can be set to 'single', 'multiple' or 'series', for single selection, multiple selections and whole series selection.

'series' is supported since v5.3.0

 series-sankey. data
Array
The nodes list of the sankey diagram.

data: [{
    name: 'node1',
    // This attribute decides the layer of the current node.
    depth: 0
}, {
    name: 'node2',
    depth: 1
}]
Notice: The name of the node cannot be repeated.

Properties
{ name , value , depth , itemStyle , label , emphasis , blur , select , tooltip }
series-sankey. nodes
Array
Equals to data

 series-sankey. links
Array
The links between nodes. Notes: The Sankey diagram theoretically only supports Directed Acyclic Graph(DAG), so please make sure that there is no cycle in the links. For instance:

links: [{
    source: 'n1',
    target: 'n2'
}, {
    source: 'n2',
    target: 'n3'
}]
 series-sankey.links. source
string
The name of source node of edge

 series-sankey.links. target
string
The name of target node of edge

 series-sankey.links. value
number
The value of edge, which decides the width of edge.

  series-sankey.links. edgeLabel
Object
Since v5.4.1

The label style of each edge/link.

Properties
{ show , distance , rotate , offset , formatter , color , fontStyle , fontWeight , fontFamily , fontSize , align , verticalAlign , lineHeight , backgroundColor , borderColor , borderWidth , borderType , borderDashOffset , borderRadius , padding , shadowColor , shadowBlur , shadowOffsetX , shadowOffsetY , width , height , textBorderColor , textBorderWidth , textBorderType , textBorderDashOffset , textShadowColor , textShadowBlur , textShadowOffsetX , textShadowOffsetY , overflow , ellipsis , rich }
  series-sankey.links. lineStyle
Object
The line style of edge.

Properties
{ color , opacity , curveness , shadowBlur , shadowColor , shadowOffsetX , shadowOffsetY }
  series-sankey.links. emphasis
Object
Properties
{ disabled , edgeLabel , lineStyle }
  series-sankey.links. blur
Object
Since v5.0.0

Properties
{ edgeLabel , lineStyle }
  series-sankey.links. select
Object
Since v5.0.0

Properties
{ disabled , edgeLabel , lineStyle }
series-sankey. edges
Array
Equals to links

series-sankey. silent
boolean
Whether to ignore mouse events. Default value is false, for triggering and responding to mouse events.

series-sankey. animation = true
boolean
Whether to enable animation.

series-sankey. animationThreshold = 2000
number
Whether to set graphic number threshold to animation. Animation will be disabled when graphic number is larger than threshold.

series-sankey. animationDuration = 1000
numberFunction
Duration of the first animation, which supports callback function for different data to have different animation effect:

animationDuration: function (idx) {
    // delay for later data is larger
    return idx * 100;
}
series-sankey. animationEasing = 'linear'
string
Easing method used for the first animation. Varied easing effects can be found at easing effect example.

series-sankey. animationDelay
numberFunction
Delay before updating the first animation, which supports callback function for different data to have different animation effect.

For example:

animationDelay: function (idx) {
    // delay for later data is larger
    return idx * 100;
}
See this example for more information.

series-sankey. animationDurationUpdate = 300
numberFunction
Time for animation to complete, which supports callback function for different data to have different animation effect:

animationDurationUpdate: function (idx) {
    // delay for later data is larger
    return idx * 100;
}
series-sankey. animationEasingUpdate = 'cubicOut'
string
Easing method used for animation.

series-sankey. animationDelayUpdate
numberFunction
Delay before updating animation, which supports callback function for different data to have different animation effects.

For example:

animationDelayUpdate: function (idx) {
    // delay for later data is larger
    return idx * 100;
}
See this example for more information.

 series-sankey. tooltip
Object
tooltip settings in this series.

Properties
{ position , formatter , valueFormatter , backgroundColor , borderColor , borderWidth , padding , textStyle , extraCssText }