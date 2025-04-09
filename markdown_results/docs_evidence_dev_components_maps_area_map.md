[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Maps](https://docs.evidence.dev/components/maps) [Area Map](https://docs.evidence.dev/components/maps/area-map)

# Area Map

Compare a metric across different regions on a map using a choropleth map

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
/>
```

## [Examples](https://docs.evidence.dev/components/maps/area-map\#examples)

### [Custom Basemap](https://docs.evidence.dev/components/maps/area-map\#custom-basemap)

You can add a different basemap by passing in a basemap URL. You can find examples here: [https://leaflet-extras.github.io/leaflet-providers/preview/](https://leaflet-extras.github.io/leaflet-providers/preview/)

preview

code

**Note:** you need to wrap the url in curly braces and backticks to avoid the curly braces in the URL being read as variables on your page

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    basemap={`https://tile.openstreetmap.org/{z}/{x}/{y}.png`}
/>
```

### [Using an Online GeoJSON](https://docs.evidence.dev/components/maps/area-map\#using-an-online-geojson)

preview

code

```text-sm svelte
<AreaMap
    data={orders_by_state}
    areaCol=state
    geoJsonUrl=https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces.geojson
    geoId=name
    value=orders
/>
```

### [Custom Tooltip](https://docs.evidence.dev/components/maps/area-map\#custom-tooltip)

#### [`tooltipType=hover`](https://docs.evidence.dev/components/maps/area-map\#tooltiptypehover)

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    tooltip={[\
        {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
        {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'}\
    ]}
/>
```

#### [With clickable link and `tooltipType=click`](https://docs.evidence.dev/components/maps/area-map\#with-clickable-link-and-tooltiptypeclick)

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    tooltipType=click
    tooltip={[\
        {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
        {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
        {id: 'link_col', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
    ]}
/>
```

### [Custom Styling](https://docs.evidence.dev/components/maps/area-map\#custom-styling)

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    color=#fff5d9
    borderColor=#737373
    borderWidth=0.5
/>
```

### [Custom Color Palette](https://docs.evidence.dev/components/maps/area-map\#custom-color-palette)

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    colorPalette={[\
        ['yellow', 'yellow'],\
        ['orange', 'orange'],\
        ['red', 'red'],\
        ['darkred', 'darkred'],\
    ]}
/>
```

### [Link Drilldown](https://docs.evidence.dev/components/maps/area-map\#link-drilldown)

Pass in a `link` column to enable navigation on click of the point. These can be absolute or relative URLs

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    link=link_col
/>
```

### [Use Map as Input](https://docs.evidence.dev/components/maps/area-map\#use-map-as-input)

Use the `name` prop to set an input name for the map - when a point is clicked, it will set the input value to that row of data

preview

code

```text-sm svelte
<AreaMap
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl='path/to/your/geoJson'
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
    height=250
    name=my_area_map
/>
```

_Click an area on the map to see the input value get updated:_

#### [Selected value for `{inputs.my_area_map}`:](https://docs.evidence.dev/components/maps/area-map\#selected-value-for-123inputsmy_area_map125)

```
{
  "zip_code": {}
}
```

#### [Selected value for `{inputs.my_area_map.zip_code}`:](https://docs.evidence.dev/components/maps/area-map\#selected-value-for-123inputsmy_area_mapzip_code125)

#### [Filtered Data](https://docs.evidence.dev/components/maps/area-map\#filtered-data)

Loading...

### [Legends](https://docs.evidence.dev/components/maps/area-map\#legends)

#### [Categorical Legend](https://docs.evidence.dev/components/maps/area-map\#categorical-legend)

preview

code

```text-sm svelte
<AreaMap
   data={grouped_locations}
   lat=lat
   long=long
   value=Category
   geoId=ZCTA5CE10
   areaCol=zip_code
/>
```

#### [Custom Colors](https://docs.evidence.dev/components/maps/area-map\#custom-colors)

Set custom legend colors using the `colorPalette` prop to match the number of categories; excess categorical options will default to standard colors.

preview

code

```text-sm svelte
<AreaMap
   data={grouped_locations}
   lat=lat
   long=long
   value=Category
   geoId=ZCTA5CE10
   areaCol=zip_code
   colorPalette={['#C65D47', '#5BAF7A', '#4A8EBA', '#D35B85', '#E1C16D', '#6F5B9A', '#4E8D8D']}
/>
```

#### [Scalar Legend](https://docs.evidence.dev/components/maps/area-map\#scalar-legend)

preview

code

```text-sm svelte
<AreaMap
    data={grouped_locations}
    lat=lat
    long=long
    value=sales
    geoId=ZCTA5CE10
    areaCol=zip_code
    valueFmt=usd
/>
```

#### [Custom Colors](https://docs.evidence.dev/components/maps/area-map\#custom-colors-1)

Define scalar legend colors using the `colorPalette` prop, allowing specified colors to create a gradient based on the range of values.

preview

code

```text-sm svelte
<AreaMap
    data={grouped_locations}
    lat=lat
    long=long
    value=sales
    geoId=ZCTA5CE10
    areaCol=zip_code
    colorPalette={['#C65D47', '#4A8EBA']}
    valueFmt=usd
/>
```

## [Required GeoJSON Data Structure](https://docs.evidence.dev/components/maps/area-map\#required-geojson-data-structure)

The GeoJSON data you pass to the map must be a feature collection. [See here for an example](https://gist.github.com/sgillies/1233327#file-geojson-spec-1-0-L50)

## [Map Resources](https://docs.evidence.dev/components/maps/area-map\#map-resources)

Below are a selection of publically available GeoJSON files that may be useful for mapping. These are from the [Natural Earth Data](https://www.naturalearthdata.com/) project, and hosted by [GeoJSON.xyz](https://geojson.xyz/).

### [Country, State, and City Locations](https://docs.evidence.dev/components/maps/area-map\#country-state-and-city-locations)

No Results

All GeoJSON Files

## [Options](https://docs.evidence.dev/components/maps/area-map\#options)

### [Areas](https://docs.evidence.dev/components/maps/area-map\#areas)

[data](https://docs.evidence.dev/components/maps/area-map#props-data)

Required

Query result, referenced using curly braces

Options:query name

[geoJsonUrl](https://docs.evidence.dev/components/maps/area-map#props-geoJsonUrl)

Required

Path to source geoJSON data from - can be a URL (see [Map Resources](https://docs.evidence.dev/components/maps/area-map#map-resources)) or a file in your project.

If the file is in your `static` directory in the root of your project, reference it as `geoJsonUrl="/your_file.geojson"`

Options:URL

[areaCol](https://docs.evidence.dev/components/maps/area-map#props-areaCol)

Required

Column in the data that specifies the area each row belongs to.

Options:column name

[geoId](https://docs.evidence.dev/components/maps/area-map#props-geoId)

Required

Property in the GeoJSON that uniquely identifies each feature.

Options:geoJSON property name

[value](https://docs.evidence.dev/components/maps/area-map#props-value)

Column that determines the value displayed for each area (used for color scale)

Options:column name

[valueFmt](https://docs.evidence.dev/components/maps/area-map#props-valueFmt)

Format string for displaying the value.

Options:format string

[title](https://docs.evidence.dev/components/maps/area-map#props-title)

Title for the map

Options:string

[subtitle](https://docs.evidence.dev/components/maps/area-map#props-subtitle)

Subtitle - appears under the title

Options:string

[ignoreZoom](https://docs.evidence.dev/components/maps/area-map#props-ignoreZoom)

Stops map from zooming out to show all data for this layer

Options:

true false

Default:false

### [Color Scale](https://docs.evidence.dev/components/maps/area-map\#color-scale)

[colorPalette](https://docs.evidence.dev/components/maps/area-map#props-colorPalette)

Array of colors used for theming the areas based on data ``

Options:array of colors

[min](https://docs.evidence.dev/components/maps/area-map#props-min)

Minimum value to use for the color scale.

Options:numberDefault:min of value column

[max](https://docs.evidence.dev/components/maps/area-map#props-max)

Maximum value to use for the color scale.

Options:numberDefault:max of value column

### [Legend](https://docs.evidence.dev/components/maps/area-map\#legend)

[legend](https://docs.evidence.dev/components/maps/area-map#props-legend)

Turns legend on or off

Options:

true false

Default:true

[legendType](https://docs.evidence.dev/components/maps/area-map#props-legendType)

Appends a categorical or scalar legend to the map

Options:

categorical scalar

[legendPosition](https://docs.evidence.dev/components/maps/area-map#props-legendPosition)

Determines the legend's position on the map, with options provided

Options:

bottomLeft topLeft bottomRight topRight

Default:bottomLeft

### [Interactivity](https://docs.evidence.dev/components/maps/area-map\#interactivity)

[link](https://docs.evidence.dev/components/maps/area-map#props-link)

URL to navigate to when a area is clicked.

Options:URL

[name](https://docs.evidence.dev/components/maps/area-map#props-name)

Input name. Can be referenced on your page with \`\`

Options:string

### [Styling](https://docs.evidence.dev/components/maps/area-map\#styling)

[color](https://docs.evidence.dev/components/maps/area-map#props-color)

Color for the areas. Use when you want all areas to be the same color.

Options:CSS color value

[borderWidth](https://docs.evidence.dev/components/maps/area-map#props-borderWidth)

Width of the border around each area.

Options:pixel valueDefault:0.75

[borderColor](https://docs.evidence.dev/components/maps/area-map#props-borderColor)

Color of the border around each area.

Options:CSS color value

[opacity](https://docs.evidence.dev/components/maps/area-map#props-opacity)

Opacity of the areas.

Options:number between 0 and 1Default:0.8

### [Selected State](https://docs.evidence.dev/components/maps/area-map\#selected-state)

[selectedColor](https://docs.evidence.dev/components/maps/area-map#props-selectedColor)

When area is selected: Color for the areas. Use when you want all areas to be the same color.

Options:CSS color value

[selectedBorderWidth](https://docs.evidence.dev/components/maps/area-map#props-selectedBorderWidth)

When area is selected: Width of the border around each area.

Options:pixel valueDefault:0.75

[selectedBorderColor](https://docs.evidence.dev/components/maps/area-map#props-selectedBorderColor)

When area is selected: Color of the border around each area.

Options:CSS color value

[selectedOpacity](https://docs.evidence.dev/components/maps/area-map#props-selectedOpacity)

When area is selected: Opacity of the areas.

Options:number between 0 and 1Default:0.8

### [Tooltips](https://docs.evidence.dev/components/maps/area-map\#tooltips)

[showTooltip](https://docs.evidence.dev/components/maps/area-map#props-showTooltip)

Whether to show tooltips

Options:

true false

Default:true

[tooltipType](https://docs.evidence.dev/components/maps/area-map#props-tooltipType)

Determines whether tooltips are activated by hover or click.

Options:

hover click

Default:hover

[tooltipClass](https://docs.evidence.dev/components/maps/area-map#props-tooltipClass)

CSS class applied to the tooltip content. You can pass Tailwind classes into this prop to custom-style the tooltip

Options:CSS class

[tooltip](https://docs.evidence.dev/components/maps/area-map#props-tooltip)

Configuration for tooltips associated with each area. See below example for format

Options:array of objects

#### [`tooltip` example:](https://docs.evidence.dev/components/maps/area-map\#tooltip-example)

```text-sm javascript
tooltip={[\
    {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
    {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
    {id: 'zip_code', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
]}
```

#### [All options available in `tooltip`:](https://docs.evidence.dev/components/maps/area-map\#all-options-available-in-tooltip)

- `id`: column ID
- `title`: custom string to use as title of field
- `fmt`: format to use for value
- `showColumnName`: whether to show the column name. If `false`, only the value will be shown
- `contentType`: currently can only be "link"
- `linkLabel`: text to show for a link when contentType="link"
- `formatColumnTitle`: whether to automatically uppercase the first letter of the title. Only applies when `title` not passed explicitly
- `valueClass`: custom Tailwind classes to style the values
- `fieldClass`: custom Tailwind classes to style the column names

### [Base Map](https://docs.evidence.dev/components/maps/area-map\#base-map)

[basemap](https://docs.evidence.dev/components/maps/area-map#props-basemap)

URL template for the basemap tiles.

Options:URL

[attribution](https://docs.evidence.dev/components/maps/area-map#props-attribution)

Attribution text to display on the map (e.g., "© OpenStreetMap contributors").

Options:text

[title](https://docs.evidence.dev/components/maps/area-map#props-title-2)

Optional title displayed above the map.

Options:text

[startingLat](https://docs.evidence.dev/components/maps/area-map#props-startingLat)

Starting latitude for the map center.

Options:latitude coordinate

[startingLong](https://docs.evidence.dev/components/maps/area-map#props-startingLong)

Starting longitude for the map center.

Options:longitude coordinate

[startingZoom](https://docs.evidence.dev/components/maps/area-map#props-startingZoom)

Initial zoom level of the map.

Options:number (1 to 18)

[height](https://docs.evidence.dev/components/maps/area-map#props-height)

Height of the map in pixels.

Options:pixel valueDefault:300

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/maps/area-map/index.md)