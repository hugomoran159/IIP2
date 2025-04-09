[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Maps](https://docs.evidence.dev/components/maps) [Bubble Map](https://docs.evidence.dev/components/maps/bubble-map)

# Bubble Map

Compare points of interest on a map using bubble size, and optionally color, to visualize metrics. It is easier to distinguish size than color, so the primary metric should generally be used to set the size.

preview

code

Sales

€16,585€218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm html
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    size=sales
    sizeFmt=eur
    value=sales
    valueFmt=eur
    pointName=point_name
/>
```

## [Examples](https://docs.evidence.dev/components/maps/bubble-map\#examples)

### [Custom Basemap](https://docs.evidence.dev/components/maps/bubble-map\#custom-basemap)

You can add a different basemap by passing in a basemap URL. You can find examples here: [https://leaflet-extras.github.io/leaflet-providers/preview/](https://leaflet-extras.github.io/leaflet-providers/preview/)

preview

code

Sales

16,585218,270

Hide Legend

![](https://tile.openstreetmap.org/8/43/101.png)![](https://tile.openstreetmap.org/8/44/101.png)![](https://tile.openstreetmap.org/8/43/102.png)![](https://tile.openstreetmap.org/8/44/102.png)![](https://tile.openstreetmap.org/8/42/101.png)![](https://tile.openstreetmap.org/8/45/101.png)![](https://tile.openstreetmap.org/8/42/102.png)![](https://tile.openstreetmap.org/8/45/102.png)![](https://tile.openstreetmap.org/8/41/101.png)![](https://tile.openstreetmap.org/8/46/101.png)![](https://tile.openstreetmap.org/8/41/102.png)![](https://tile.openstreetmap.org/8/46/102.png)![](https://tile.openstreetmap.org/8/40/101.png)![](https://tile.openstreetmap.org/8/47/101.png)![](https://tile.openstreetmap.org/8/40/102.png)![](https://tile.openstreetmap.org/8/47/102.png)

[Leaflet](https://leafletjs.com/ "A JavaScript library for interactive maps") \| © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors

**Note:** you need to wrap the url in curly braces and backticks to avoid the curly braces in the URL being read as variables on your page

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    pointName=point_name
    height=200
    basemap={`https://tiles.stadiamaps.com/tiles/alidade_smooth_dark/{z}/{x}/{y}{r}.{ext}`}
    attribution='© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
```

### [Custom Tooltip](https://docs.evidence.dev/components/maps/bubble-map\#custom-tooltip)

#### [`tooltipType=hover`](https://docs.evidence.dev/components/maps/bubble-map\#tooltiptypehover)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    size=sales
    sizeFmt=usd
    pointName=point_name
    tooltipType=hover
    tooltip={[\
        {id: 'point_name', showColumnName: false, valueClass: 'text-xl font-semibold'},\
        {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'}\
    ]}
/>
```

#### [With clickable link and `tooltipType=click`](https://docs.evidence.dev/components/maps/bubble-map\#with-clickable-link-and-tooltiptypeclick)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    size=sales
    sizeFmt=usd
    pointName=point_name
    tooltipType=click
    tooltip={[\
        {id: 'point_name', showColumnName: false, valueClass: 'text-xl font-semibold'},\
        {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
        {id: 'link_col', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
    ]}
/>
```

### [Custom Color Palette](https://docs.evidence.dev/components/maps/bubble-map\#custom-color-palette)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    value=sales
    valueFmt=usd
    pointName=point_name
    colorPalette={['yellow','orange','red','darkred']}
/>
```

### [Custom Styling](https://docs.evidence.dev/components/maps/bubble-map\#custom-styling)

preview

code

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    size=sales
    sizeFmt=usd
    pointName=point_name
    color=#128c2b
    opacity=1
    borderWidth=1
    borderColor=black
/>
```

### [Max Bubble Size](https://docs.evidence.dev/components/maps/bubble-map\#max-bubble-size)

preview

code

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    size=sales
    sizeFmt=usd
    pointName=point_name
    maxSize=10
/>
```

### [Link Drilldown](https://docs.evidence.dev/components/maps/bubble-map\#link-drilldown)

Pass in a `link` column to enable navigation on click of the point. These can be absolute or relative URLs

preview

code

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    size=sales
    sizeFmt=usd
    link=link_col
/>
```

### [Use Map as Input](https://docs.evidence.dev/components/maps/bubble-map\#use-map-as-input)

Use the `name` prop to set an input name for the map - when a point is clicked, it will set the input value to that row of data

preview

code

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={la_locations}
    lat=lat
    long=long
    size=sales
    sizeFmt=usd
    name=my_point_map
/>
```

_Click a point on the map to see the input value get updated:_

#### [Selected value for `{inputs.my_point_map}`:](https://docs.evidence.dev/components/maps/bubble-map\#selected-value-for-123inputsmy_point_map125)

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

#### [Selected value for `{inputs.my_point_map.point_name}`:](https://docs.evidence.dev/components/maps/bubble-map\#selected-value-for-123inputsmy_point_mappoint_name125)

true

#### [Filtered Data](https://docs.evidence.dev/components/maps/bubble-map\#filtered-data)

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

### [Legends](https://docs.evidence.dev/components/maps/bubble-map\#legends)

#### [Categorical Legend](https://docs.evidence.dev/components/maps/bubble-map\#categorical-legend)

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
<BubbleMap
    data={grouped_locations}
    lat=lat
    long=long
    value=Category
    size=sales
/>
```

#### [Custom Colors](https://docs.evidence.dev/components/maps/bubble-map\#custom-colors)

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
<BubbleMap
    data={grouped_locations}
    lat=lat
    long=long
    value=Category
    size=sales
    colorPalette={['#C65D47', '#5BAF7A', '#4A8EBA', '#D35B85', '#E1C16D', '#6F5B9A', '#4E8D8D']}
/>
```

#### [Scalar Legend](https://docs.evidence.dev/components/maps/bubble-map\#scalar-legend)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={grouped_locations}
    lat=lat
    long=long
    value=sales
    size=sales
    valueFmt=usd
/>
```

#### [Custom Colors](https://docs.evidence.dev/components/maps/bubble-map\#custom-colors-1)

Define scalar legend colors using the `colorPalette` prop, allowing specified colors to create a gradient based on the range of values.

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BubbleMap
    data={grouped_locations}
    lat=lat
    long=long
    value=sales
    size=sales
    colorPalette={['#C65D47', '#4A8EBA']}
    valueFmt=usd
/>
```

## [Options](https://docs.evidence.dev/components/maps/bubble-map\#options)

### [Bubbles](https://docs.evidence.dev/components/maps/bubble-map\#bubbles)

[data](https://docs.evidence.dev/components/maps/bubble-map#props-data)

Required

Query result, referenced using curly braces

Options:query name

[lat](https://docs.evidence.dev/components/maps/bubble-map#props-lat)

Required

Column containing latitude values

Options:column name

[long](https://docs.evidence.dev/components/maps/bubble-map#props-long)

Required

Column containing longitude values

Options:column name

[size](https://docs.evidence.dev/components/maps/bubble-map#props-size)

Required

Column that determines the size displayed for each point.

Options:column name

[sizeFmt](https://docs.evidence.dev/components/maps/bubble-map#props-sizeFmt)

Format string for displaying the size value in tooltips.

Options:format string

[maxSize](https://docs.evidence.dev/components/maps/bubble-map#props-maxSize)

Maximum size of the bubbles

Options:numberDefault:20

[value](https://docs.evidence.dev/components/maps/bubble-map#props-value)

Column that determines the value displayed at each point (used for color scale)

Options:column name

[valueFmt](https://docs.evidence.dev/components/maps/bubble-map#props-valueFmt)

Format string for displaying the value.

Options:format string

[pointName](https://docs.evidence.dev/components/maps/bubble-map#props-pointName)

Column containing the names/labels of the points - by default, this is shown as the title of the tooltip.

Options:column name

[title](https://docs.evidence.dev/components/maps/bubble-map#props-title)

Title for the map

Options:string

[subtitle](https://docs.evidence.dev/components/maps/bubble-map#props-subtitle)

Subtitle - appears under the title

Options:string

[ignoreZoom](https://docs.evidence.dev/components/maps/bubble-map#props-ignoreZoom)

Stops map from zooming out to show all data for this layer

Options:

true false

Default:false

### [Color Scale](https://docs.evidence.dev/components/maps/bubble-map\#color-scale)

[colorPalette](https://docs.evidence.dev/components/maps/bubble-map#props-colorPalette)

Array of colors used for theming the points based on data ``

Options:array of colors

[min](https://docs.evidence.dev/components/maps/bubble-map#props-min)

Minimum value to use for the color scale.

Options:numberDefault:min of value column

[max](https://docs.evidence.dev/components/maps/bubble-map#props-max)

Maximum value to use for the color scale.

Options:numberDefault:max of value column

### [Legend](https://docs.evidence.dev/components/maps/bubble-map\#legend)

[legend](https://docs.evidence.dev/components/maps/bubble-map#props-legend)

Turns legend on or off

Options:

true false

Default:true

[legendType](https://docs.evidence.dev/components/maps/bubble-map#props-legendType)

Appends a categorical or scalar legend to the map

Options:

categorical scalar

[legendPosition](https://docs.evidence.dev/components/maps/bubble-map#props-legendPosition)

Determines the legend's position on the map, with options provided

Options:

bottomLeft topLeft bottomRight topRight

Default:bottomLeft

### [Interactivity](https://docs.evidence.dev/components/maps/bubble-map\#interactivity)

[link](https://docs.evidence.dev/components/maps/bubble-map#props-link)

URL to navigate to when a point is clicked.

Options:URL

[name](https://docs.evidence.dev/components/maps/bubble-map#props-name)

Input name. Can be referenced on your page with \`\`

Options:string

### [Styling](https://docs.evidence.dev/components/maps/bubble-map\#styling)

[color](https://docs.evidence.dev/components/maps/bubble-map#props-color)

Color for the points. Use when you want all points to be the same color.

Options:CSS color value

[borderWidth](https://docs.evidence.dev/components/maps/bubble-map#props-borderWidth)

Width of the border around each point.

Options:pixel valueDefault:0.75

[borderColor](https://docs.evidence.dev/components/maps/bubble-map#props-borderColor)

Color of the border around each point.

Options:CSS color value

[opacity](https://docs.evidence.dev/components/maps/bubble-map#props-opacity)

Opacity of the points.

Options:number between 0 and 1Default:0.8

### [Selected State](https://docs.evidence.dev/components/maps/bubble-map\#selected-state)

[selectedColor](https://docs.evidence.dev/components/maps/bubble-map#props-selectedColor)

When point is selected: Color for the points. Use when you want all points to be the same color.

Options:CSS color value

[selectedBorderWidth](https://docs.evidence.dev/components/maps/bubble-map#props-selectedBorderWidth)

When point is selected: Width of the border around each point.

Options:pixel valueDefault:0.75

[selectedBorderColor](https://docs.evidence.dev/components/maps/bubble-map#props-selectedBorderColor)

When point is selected: Color of the border around each point.

Options:CSS color value

[selectedOpacity](https://docs.evidence.dev/components/maps/bubble-map#props-selectedOpacity)

When point is selected: Opacity of the points.

Options:number between 0 and 1Default:0.8

### [Tooltips](https://docs.evidence.dev/components/maps/bubble-map\#tooltips)

[showTooltip](https://docs.evidence.dev/components/maps/bubble-map#props-showTooltip)

Whether to show tooltips

Options:

true false

Default:true

[tooltipType](https://docs.evidence.dev/components/maps/bubble-map#props-tooltipType)

Determines whether tooltips are activated by hover or click.

Options:

hover click

Default:hover

[tooltipClass](https://docs.evidence.dev/components/maps/bubble-map#props-tooltipClass)

CSS class applied to the tooltip content. You can pass Tailwind classes into this prop to custom-style the tooltip

Options:CSS class

[tooltip](https://docs.evidence.dev/components/maps/bubble-map#props-tooltip)

Configuration for tooltips associated with each area. See below example for format

Options:array of objects

#### [`tooltip` example:](https://docs.evidence.dev/components/maps/bubble-map\#tooltip-example)

```text-sm javascript
tooltip={[\
    {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
    {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
    {id: 'zip_code', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
]}
```

#### [All options available in `tooltip`:](https://docs.evidence.dev/components/maps/bubble-map\#all-options-available-in-tooltip)

- `id`: column ID
- `title`: custom string to use as title of field
- `fmt`: format to use for value
- `showColumnName`: whether to show the column name. If `false`, only the value will be shown
- `contentType`: currently can only be "link"
- `linkLabel`: text to show for a link when contentType="link"
- `formatColumnTitle`: whether to automatically uppercase the first letter of the title. Only applies when `title` not passed explicitly
- `valueClass`: custom Tailwind classes to style the values
- `fieldClass`: custom Tailwind classes to style the column names

### [Base Map](https://docs.evidence.dev/components/maps/bubble-map\#base-map)

[basemap](https://docs.evidence.dev/components/maps/bubble-map#props-basemap)

URL template for the basemap tiles.

Options:URL

[attribution](https://docs.evidence.dev/components/maps/bubble-map#props-attribution)

Attribution text to display on the map (e.g., "© OpenStreetMap contributors").

Options:text

[title](https://docs.evidence.dev/components/maps/bubble-map#props-title-2)

Optional title displayed above the map.

Options:text

[startingLat](https://docs.evidence.dev/components/maps/bubble-map#props-startingLat)

Starting latitude for the map center.

Options:latitude coordinate

[startingLong](https://docs.evidence.dev/components/maps/bubble-map#props-startingLong)

Starting longitude for the map center.

Options:longitude coordinate

[startingZoom](https://docs.evidence.dev/components/maps/bubble-map#props-startingZoom)

Initial zoom level of the map.

Options:number (1 to 18)

[height](https://docs.evidence.dev/components/maps/bubble-map#props-height)

Height of the map in pixels.

Options:pixel valueDefault:300

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/maps/bubble-map/index.md)