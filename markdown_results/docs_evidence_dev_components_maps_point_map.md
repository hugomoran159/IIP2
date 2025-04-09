[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Maps](https://docs.evidence.dev/components/maps) [Point Map](https://docs.evidence.dev/components/maps/point-map)

# Point Map

Show points of interest on a map, optionally color-coded by a metric.

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm html
<PointMap
    data={la_locations}
    lat=lat
    long=long
    pointName=point_name
    height=200
/>
```

## [Examples](https://docs.evidence.dev/components/maps/point-map\#examples)

### [Custom Basemap](https://docs.evidence.dev/components/maps/point-map\#custom-basemap)

You can add a different basemap by passing in a basemap URL. You can find examples here: [https://leaflet-extras.github.io/leaflet-providers/preview/](https://leaflet-extras.github.io/leaflet-providers/preview/)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://tile.openstreetmap.org/7/21/50.png)![](https://tile.openstreetmap.org/7/22/50.png)![](https://tile.openstreetmap.org/7/21/51.png)![](https://tile.openstreetmap.org/7/22/51.png)![](https://tile.openstreetmap.org/7/20/50.png)![](https://tile.openstreetmap.org/7/23/50.png)![](https://tile.openstreetmap.org/7/20/51.png)![](https://tile.openstreetmap.org/7/23/51.png)![](https://tile.openstreetmap.org/7/19/50.png)![](https://tile.openstreetmap.org/7/24/50.png)![](https://tile.openstreetmap.org/7/19/51.png)![](https://tile.openstreetmap.org/7/24/51.png)![](https://tile.openstreetmap.org/7/18/50.png)![](https://tile.openstreetmap.org/7/25/50.png)![](https://tile.openstreetmap.org/7/18/51.png)![](https://tile.openstreetmap.org/7/25/51.png)

[Leaflet](https://leafletjs.com/ "A JavaScript library for interactive maps") \| © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors

**Note:** you need to wrap the url in curly braces and backticks to avoid the curly braces in the URL being read as variables on your page

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    pointName=point_name
    height=200
    basemap={`https://tiles.stadiamaps.com/tiles/alidade_smooth_dark/{z}/{x}/{y}{r}.{ext}`}
    attribution='© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
/>
```

### [Custom Tooltip](https://docs.evidence.dev/components/maps/point-map\#custom-tooltip)

#### [`tooltipType=hover`](https://docs.evidence.dev/components/maps/point-map\#tooltiptypehover)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    pointName=point_name
    height=200
    tooltipType=hover
    tooltip={[\
        {id: 'point_name', showColumnName: false, valueClass: 'text-xl font-semibold'},\
        {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'}\
    ]}
/>
```

#### [With clickable link and `tooltipType=click`](https://docs.evidence.dev/components/maps/point-map\#with-clickable-link-and-tooltiptypeclick)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    pointName=point_name
    height=200
    tooltipType=click
    tooltip={[\
        {id: 'point_name', showColumnName: false, valueClass: 'text-xl font-semibold'},\
        {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
        {id: 'link_col', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
    ]}
/>
```

### [Custom Color Palette](https://docs.evidence.dev/components/maps/point-map\#custom-color-palette)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    pointName=point_name
    height=200
    colorPalette={['yellow','orange','red','darkred']}
/>
```

### [Custom Styling](https://docs.evidence.dev/components/maps/point-map\#custom-styling)

preview

code

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    pointName=point_name
    height=200
    color=#128c2b
    size=10
    opacity=0.6
    borderWidth=0
/>
```

### [Link Drilldown](https://docs.evidence.dev/components/maps/point-map\#link-drilldown)

Pass in a `link` column to enable navigation on click of the point. These can be absolute or relative URLs

preview

code

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    link=link_col
    height=200
/>
```

### [Use Map as Input](https://docs.evidence.dev/components/maps/point-map\#use-map-as-input)

Use the `name` prop to set an input name for the map - when a point is clicked, it will set the input value to that row of data

preview

code

![](https://d.basemaps.cartocdn.com/light_all/7/21/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/22/50.png)![](https://a.basemaps.cartocdn.com/light_all/7/21/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/22/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/20/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/23/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/20/51.png)![](https://c.basemaps.cartocdn.com/light_all/7/23/51.png)![](https://b.basemaps.cartocdn.com/light_all/7/19/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/24/50.png)![](https://c.basemaps.cartocdn.com/light_all/7/19/51.png)![](https://d.basemaps.cartocdn.com/light_all/7/24/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/18/50.png)![](https://d.basemaps.cartocdn.com/light_all/7/25/50.png)![](https://b.basemaps.cartocdn.com/light_all/7/18/51.png)![](https://a.basemaps.cartocdn.com/light_all/7/25/51.png)

```text-sm svelte
<PointMap
    data={la_locations}
    lat=lat
    long=long
    name=my_point_map
    height=200
/>
```

_Click a point on the map to see the input value get updated:_

#### [Selected value for `{inputs.my_point_map}`:](https://docs.evidence.dev/components/maps/point-map\#selected-value-for-123inputsmy_point_map125)

```
{
  "id": true,
  "point_name": true,
  "lat": true,
  "long": true,
  "sales": true,
  "link_col": true
}
```

#### [Selected value for `{inputs.my_point_map.point_name}`:](https://docs.evidence.dev/components/maps/point-map\#selected-value-for-123inputsmy_point_mappoint_name125)

true

#### [Filtered Data](https://docs.evidence.dev/components/maps/point-map\#filtered-data)

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| ID | Point Name | Lat | Long | Sales |
| --- | --- | --- | --- | --- |
| 0 | Ondrickaton | 34.2 | -118 | $119k |
| 1 | South Gate | 34.8 | -118 | $110k |
| 2 | Leonorafort | 34.3 | -118 | $157k |
| 3 | Schaeferchester | 34.7 | -118 | $94k |
| 4 | Wizaboro | 34.0 | -118 | $17k |
| 5 | Mayerton | 34.3 | -119 | $133k |
| 6 | South Devante | 34.2 | -118 | $86k |
| 7 | South Shyanne | 34.2 | -119 | $125k |
| 8 | West Moses | 34.7 | -119 | $198k |
| 9 | Larkinhaven | 34.6 | -118 | $166k |
| 10 | South Neoma | 34.0 | -119 | $148k |
| 11 | North Korey | 34.6 | -118 | $138k |
| 12 | Lake Damaris | 34.3 | -119 | $38k |
| 13 | South Ricoboro | 34.6 | -118 | $142k |
| 14 | Fort Edwinchester | 34.5 | -118 | $200k |
| 15 | Hegmannport | 33.8 | -118 | $85k |
| 16 | Port Dora | 34.6 | -118 | $141k |
| 17 | Port Kenton | 34.7 | -119 | $210k |
| 18 | Norbertoburgh | 33.8 | -118 | $218k |
| 19 | Beierport | 34.6 | -118 | $88k |
| 20 | Dollyton | 34.1 | -119 | $20k |
| 21 | Pacochaview | 33.8 | -118 | $60k |
| 22 | Casa Grande | 34.6 | -118 | $152k |
| 23 | Myleneport | 34.4 | -119 | $197k |
| 24 | Port Alessandra | 34.0 | -118 | $159k |
| 25 | Elenoraport | 34.0 | -119 | $169k |
| 26 | East Camrenville | 33.9 | -119 | $174k |
| 27 | East Emeraldbury | 34.0 | -119 | $174k |
| 28 | Neldaborough | 34.1 | -118 | $160k |
| 29 | East Dangeloberg | 34.8 | -118 | $40k |
| 30 | Blickmouth | 34.5 | -118 | $216k |
| 31 | Lewberg | 34.0 | -118 | $199k |
| 32 | New Meghanville | 34.4 | -118 | $168k |
| 33 | Roobmouth | 34.2 | -118 | $121k |
| 34 | East Salvatore | 34.0 | -118 | $203k |

No Results

|  |  |  |  |  |
| --- | --- | --- | --- | --- |
| ID | Point Name | Lat | Long | Sales |
| --- | --- | --- | --- | --- |
| 0 | Ondrickaton | 34.2 | -118 | $119k |
| 1 | South Gate | 34.8 | -118 | $110k |
| 2 | Leonorafort | 34.3 | -118 | $157k |
| 3 | Schaeferchester | 34.7 | -118 | $94k |
| 4 | Wizaboro | 34.0 | -118 | $17k |
| 5 | Mayerton | 34.3 | -119 | $133k |
| 6 | South Devante | 34.2 | -118 | $86k |
| 7 | South Shyanne | 34.2 | -119 | $125k |
| 8 | West Moses | 34.7 | -119 | $198k |
| 9 | Larkinhaven | 34.6 | -118 | $166k |

No Results

Page

/
410 of 35 records

### [Legends](https://docs.evidence.dev/components/maps/point-map\#legends)

#### [Categorical Legend](https://docs.evidence.dev/components/maps/point-map\#categorical-legend)

preview

code

Category

Hotels

Restaurants

Golf Courses

Shops

Bars

Entertainment

Banks

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<PointMap
    data={grouped_locations}
    lat=lat
    long=long
    value=Category
/>
```

#### [Custom Colors](https://docs.evidence.dev/components/maps/point-map\#custom-colors)

Set custom legend colors using the `colorPalette` prop to match the number of categories; excess categorical options will default to standard colors.

preview

code

Category

Hotels

Restaurants

Golf Courses

Shops

Bars

Entertainment

Banks

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<PointMap
    data={grouped_locations}
    lat=lat
    long=long
    value=Category
    colorPalette={['#C65D47', '#5BAF7A', '#4A8EBA', '#D35B85', '#E1C16D', '#6F5B9A', '#4E8D8D']}
/>
```

#### [Scalar Legend](https://docs.evidence.dev/components/maps/point-map\#scalar-legend)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<PointMap
    data={grouped_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
/>
```

#### [Custom Colors](https://docs.evidence.dev/components/maps/point-map\#custom-colors-1)

Define scalar legend colors using the `colorPalette` prop, allowing specified colors to create a gradient based on the range of values.

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<PointMap
    data={grouped_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    colorPalette={['#C65D47', '#4A8EBA']}
/>
```

## [Options](https://docs.evidence.dev/components/maps/point-map\#options)

### [Points](https://docs.evidence.dev/components/maps/point-map\#points)

[data](https://docs.evidence.dev/components/maps/point-map#props-data)

Required

Query result, referenced using curly braces

Options:query name

[value](https://docs.evidence.dev/components/maps/point-map#props-value)

Column that determines the value displayed at each point.

Options:column name

[valueFmt](https://docs.evidence.dev/components/maps/point-map#props-valueFmt)

Format string for displaying the value.

Options:format string

[pointName](https://docs.evidence.dev/components/maps/point-map#props-pointName)

Column containing the names/labels of the points - by default, this is shown as the title of the tooltip.

Options:column name

[title](https://docs.evidence.dev/components/maps/point-map#props-title)

Title for the map

Options:string

[subtitle](https://docs.evidence.dev/components/maps/point-map#props-subtitle)

Subtitle - appears under the title

Options:string

[ignoreZoom](https://docs.evidence.dev/components/maps/point-map#props-ignoreZoom)

Stops map from zooming out to show all data for this layer

Options:

true false

Default:false

### [Color Scale](https://docs.evidence.dev/components/maps/point-map\#color-scale)

[colorPalette](https://docs.evidence.dev/components/maps/point-map#props-colorPalette)

Array of colors used for theming the points based on data ``

Options:array of colors

[min](https://docs.evidence.dev/components/maps/point-map#props-min)

Minimum value to use for the color scale.

Options:number

[max](https://docs.evidence.dev/components/maps/point-map#props-max)

Maximum value to use for the color scale.

Options:number

### [Legend](https://docs.evidence.dev/components/maps/point-map\#legend)

[legend](https://docs.evidence.dev/components/maps/point-map#props-legend)

Turns legend on or off

Options:

true false

Default:true

[legendType](https://docs.evidence.dev/components/maps/point-map#props-legendType)

Appends a categorical or scalar legend to the map

Options:

categorical scalar

[legendPosition](https://docs.evidence.dev/components/maps/point-map#props-legendPosition)

Determines the legend's position on the map, with options provided

Options:

bottomLeft topLeft bottomRight topRight

Default:bottomLeft

### [Interactivity](https://docs.evidence.dev/components/maps/point-map\#interactivity)

[link](https://docs.evidence.dev/components/maps/point-map#props-link)

URL to navigate to when a point is clicked.

Options:URL

[name](https://docs.evidence.dev/components/maps/point-map#props-name)

Input name. Can be referenced on your page with \`\`

Options:string

### [Styling](https://docs.evidence.dev/components/maps/point-map\#styling)

[color](https://docs.evidence.dev/components/maps/point-map#props-color)

Color for the points. Use when you want all points to be the same color.

Options:CSS color value

[size](https://docs.evidence.dev/components/maps/point-map#props-size)

Size of the points

Options:numberDefault:5

[borderWidth](https://docs.evidence.dev/components/maps/point-map#props-borderWidth)

Width of the border around each point.

Options:pixel value

[borderColor](https://docs.evidence.dev/components/maps/point-map#props-borderColor)

Color of the border around each point.

Options:CSS color value

[opacity](https://docs.evidence.dev/components/maps/point-map#props-opacity)

Opacity of the points.

Options:number between 0 and 1

### [Selected State](https://docs.evidence.dev/components/maps/point-map\#selected-state)

[selectedColor](https://docs.evidence.dev/components/maps/point-map#props-selectedColor)

When point is selected: Color for the points. Use when you want all points to be the same color.

Options:CSS color value

[selectedBorderWidth](https://docs.evidence.dev/components/maps/point-map#props-selectedBorderWidth)

When point is selected: Width of the border around each point.

Options:pixel valueDefault:0.75

[selectedBorderColor](https://docs.evidence.dev/components/maps/point-map#props-selectedBorderColor)

When point is selected: Color of the border around each point.

Options:CSS color value

[selectedOpacity](https://docs.evidence.dev/components/maps/point-map#props-selectedOpacity)

When point is selected: Opacity of the points.

Options:number between 0 and 1Default:0.8

### [Tooltips](https://docs.evidence.dev/components/maps/point-map\#tooltips)

[showTooltip](https://docs.evidence.dev/components/maps/point-map#props-showTooltip)

Whether to show tooltips

Options:booleanDefault:true

[tooltipType](https://docs.evidence.dev/components/maps/point-map#props-tooltipType)

Determines whether tooltips are activated by hover or click.

Options:

hover click

Default:hover

[tooltipClass](https://docs.evidence.dev/components/maps/point-map#props-tooltipClass)

CSS class applied to the tooltip content. You can pass Tailwind classes into this prop to custom-style the tooltip

Options:CSS class

[tooltip](https://docs.evidence.dev/components/maps/point-map#props-tooltip)

Configuration for tooltips associated with each area. See below example for format

Options:array of objects

#### [`tooltip` example:](https://docs.evidence.dev/components/maps/point-map\#tooltip-example)

```text-sm javascript
tooltip={[\
    {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
    {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
    {id: 'zip_code', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
]}
```

#### [All options available in `tooltip`:](https://docs.evidence.dev/components/maps/point-map\#all-options-available-in-tooltip)

- `id`: column ID
- `title`: custom string to use as title of field
- `fmt`: format to use for value
- `showColumnName`: whether to show the column name. If `false`, only the value will be shown
- `contentType`: currently can only be "link"
- `linkLabel`: text to show for a link when contentType="link"
- `formatColumnTitle`: whether to automatically uppercase the first letter of the title. Only applies when `title` not passed explicitly
- `valueClass`: custom Tailwind classes to style the values
- `fieldClass`: custom Tailwind classes to style the column names

### [Base Map](https://docs.evidence.dev/components/maps/point-map\#base-map)

[basemap](https://docs.evidence.dev/components/maps/point-map#props-basemap)

URL template for the basemap tiles.

Options:URL

[attribution](https://docs.evidence.dev/components/maps/point-map#props-attribution)

Attribution text to display on the map (e.g., "© OpenStreetMap contributors").

Options:text

[title](https://docs.evidence.dev/components/maps/point-map#props-title-2)

Optional title displayed above the map.

Options:text

[startingLat](https://docs.evidence.dev/components/maps/point-map#props-startingLat)

Starting latitude for the map center.

Options:latitude coordinate

[startingLong](https://docs.evidence.dev/components/maps/point-map#props-startingLong)

Starting longitude for the map center.

Options:longitude coordinate

[startingZoom](https://docs.evidence.dev/components/maps/point-map#props-startingZoom)

Initial zoom level of the map.

Options:number (1 to 18)

[height](https://docs.evidence.dev/components/maps/point-map#props-height)

Height of the map in pixels.

Options:pixel valueDefault:300

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/maps/point-map/index.md)