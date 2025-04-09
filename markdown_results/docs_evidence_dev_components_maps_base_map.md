[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [Maps](https://docs.evidence.dev/components/maps) [Base Map](https://docs.evidence.dev/components/maps/base-map)

# Base Map

Combine multiple map layers including areas, points, and bubbles.

preview

code

Sales

$1,071$234,510

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm html
<BaseMap>
  <Areas data={la_zip_sales} geoId=ZCTA5CE10 areaCol=zip_code value=sales valueFmt=usd/>
  <Points data={la_locations} lat=lat long=long color=#179917/>
</BaseMap>
```

## [Overview](https://docs.evidence.dev/components/maps/base-map\#overview)

The BaseMap component provides a flexible and extensible way to create maps with multiple layers. This component serves as the foundation for AreaMap, PointMap, and BubbleMap.

Within BaseMap, you can add layers using the following components:

- `<Areas/>`
- `<Points/>`
- `<Bubbles/>`

## [Examples](https://docs.evidence.dev/components/maps/base-map\#examples)

See the pages for [Area Map](https://docs.evidence.dev/components/maps/area-map), [Point Map](https://docs.evidence.dev/components/maps/point-map), and [Bubble Map](https://docs.evidence.dev/components/maps/bubble-map) for examples specific to those layers. The same options can be applied to the layer components within BaseMap.

### [Adding Multiple Layers](https://docs.evidence.dev/components/maps/base-map\#adding-multiple-layers)

preview

code

Sales

$16,585$218,270

Sales

$1,071$234,510

Hide Legend

![](https://a.basemaps.cartocdn.com/light_all/8/43/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/44/101.png)![](https://b.basemaps.cartocdn.com/light_all/8/43/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/44/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/42/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/45/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/42/102.png)![](https://d.basemaps.cartocdn.com/light_all/8/45/102.png)![](https://c.basemaps.cartocdn.com/light_all/8/41/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/46/101.png)![](https://d.basemaps.cartocdn.com/light_all/8/41/102.png)![](https://a.basemaps.cartocdn.com/light_all/8/46/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/40/101.png)![](https://a.basemaps.cartocdn.com/light_all/8/47/101.png)![](https://c.basemaps.cartocdn.com/light_all/8/40/102.png)![](https://b.basemaps.cartocdn.com/light_all/8/47/102.png)

```text-sm svelte
<BaseMap>
  <Areas
    data={la_zip_sales}
    areaCol=zip_code
    geoJsonUrl="path/to/your/geoJSON"
    geoId=ZCTA5CE10
    value=sales
    valueFmt=usd
  />
  <Bubbles
    data={la_locations}
    lat=lat
    long=long
    size=sales
    sizeFmt=usd
    value=sales
    valueFmt=usd
    pointName=point_name
    colorPalette={['yellow','orange','red','darkred']}
    opacity=0.5
  />
</BaseMap>
```

### [Custom Basemap](https://docs.evidence.dev/components/maps/base-map\#custom-basemap)

You can add a different basemap by passing in a basemap URL. You can find examples here: [https://leaflet-extras.github.io/leaflet-providers/preview/](https://leaflet-extras.github.io/leaflet-providers/preview/)

preview

code

Sales

$16,585$218,270

Hide Legend

![](https://tile.openstreetmap.org/8/43/101.png)![](https://tile.openstreetmap.org/8/44/101.png)![](https://tile.openstreetmap.org/8/43/102.png)![](https://tile.openstreetmap.org/8/44/102.png)![](https://tile.openstreetmap.org/8/42/101.png)![](https://tile.openstreetmap.org/8/45/101.png)![](https://tile.openstreetmap.org/8/42/102.png)![](https://tile.openstreetmap.org/8/45/102.png)![](https://tile.openstreetmap.org/8/41/101.png)![](https://tile.openstreetmap.org/8/46/101.png)![](https://tile.openstreetmap.org/8/41/102.png)![](https://tile.openstreetmap.org/8/46/102.png)![](https://tile.openstreetmap.org/8/40/101.png)![](https://tile.openstreetmap.org/8/47/101.png)![](https://tile.openstreetmap.org/8/40/102.png)![](https://tile.openstreetmap.org/8/47/102.png)

[Leaflet](https://leafletjs.com/ "A JavaScript library for interactive maps") \| © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors

```text-sm svelte
<BaseMap basemap={`https://tile.openstreetmap.org/{z}/{x}/{y}.png`} attribution='© <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'>
    <Points
        data={la_locations}
        lat=lat
        long=long
        value=sales
        valueFmt=usd
        pointName=point_name
        color=violet
        borderColor=black
        borderWidth=2
    />
</BaseMap>
```

### [Custom Tooltip](https://docs.evidence.dev/components/maps/base-map\#custom-tooltip)

#### [`tooltipType=hover`](https://docs.evidence.dev/components/maps/base-map\#tooltiptypehover)

preview

code

Sales

$1,071$234,510

Hide Legend

![](https://d.basemaps.cartocdn.com/light_all/9/87/204.png)![](https://a.basemaps.cartocdn.com/light_all/9/87/205.png)![](https://c.basemaps.cartocdn.com/light_all/9/86/204.png)![](https://a.basemaps.cartocdn.com/light_all/9/88/204.png)![](https://d.basemaps.cartocdn.com/light_all/9/86/205.png)![](https://b.basemaps.cartocdn.com/light_all/9/88/205.png)![](https://b.basemaps.cartocdn.com/light_all/9/85/204.png)![](https://b.basemaps.cartocdn.com/light_all/9/89/204.png)![](https://c.basemaps.cartocdn.com/light_all/9/85/205.png)![](https://c.basemaps.cartocdn.com/light_all/9/89/205.png)![](https://a.basemaps.cartocdn.com/light_all/9/84/204.png)![](https://c.basemaps.cartocdn.com/light_all/9/90/204.png)![](https://b.basemaps.cartocdn.com/light_all/9/84/205.png)![](https://d.basemaps.cartocdn.com/light_all/9/90/205.png)![](https://d.basemaps.cartocdn.com/light_all/9/83/204.png)![](https://d.basemaps.cartocdn.com/light_all/9/91/204.png)![](https://a.basemaps.cartocdn.com/light_all/9/83/205.png)![](https://a.basemaps.cartocdn.com/light_all/9/91/205.png)

```text-sm svelte
<BaseMap>
    <Areas
        data={la_zip_sales}
        areaCol=zip_code
        geoJsonUrl='/geo-json/ca_california_zip_codes_geo_1.min.json'
        geoId=ZCTA5CE10
        value=sales
        valueFmt=usd
        height=250
        tooltip={[\
            {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
            {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
            {id: 'zip_code', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
        ]}
    />
</BaseMap>
```

#### [With clickable link and `tooltipType=click`](https://docs.evidence.dev/components/maps/base-map\#with-clickable-link-and-tooltiptypeclick)

preview

code

Sales

$1,071$234,510

Hide Legend

![](https://d.basemaps.cartocdn.com/light_all/9/87/204.png)![](https://a.basemaps.cartocdn.com/light_all/9/87/205.png)![](https://c.basemaps.cartocdn.com/light_all/9/86/204.png)![](https://a.basemaps.cartocdn.com/light_all/9/88/204.png)![](https://d.basemaps.cartocdn.com/light_all/9/86/205.png)![](https://b.basemaps.cartocdn.com/light_all/9/88/205.png)![](https://b.basemaps.cartocdn.com/light_all/9/85/204.png)![](https://b.basemaps.cartocdn.com/light_all/9/89/204.png)![](https://c.basemaps.cartocdn.com/light_all/9/85/205.png)![](https://c.basemaps.cartocdn.com/light_all/9/89/205.png)![](https://a.basemaps.cartocdn.com/light_all/9/84/204.png)![](https://c.basemaps.cartocdn.com/light_all/9/90/204.png)![](https://b.basemaps.cartocdn.com/light_all/9/84/205.png)![](https://d.basemaps.cartocdn.com/light_all/9/90/205.png)![](https://d.basemaps.cartocdn.com/light_all/9/83/204.png)![](https://d.basemaps.cartocdn.com/light_all/9/91/204.png)![](https://a.basemaps.cartocdn.com/light_all/9/83/205.png)![](https://a.basemaps.cartocdn.com/light_all/9/91/205.png)

```text-sm svelte
<BaseMap>
    <Areas
        data={la_zip_sales}
        areaCol=zip_code
        geoJsonUrl='/geo-json/ca_california_zip_codes_geo_1.min.json'
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
</BaseMap>
```

## [Map Resources](https://docs.evidence.dev/components/maps/base-map\#map-resources)

Below are a selection of publically available GeoJSON files that may be useful for mapping. These are from the [Natural Earth Data](https://www.naturalearthdata.com/) project, and hosted by [GeoJSON.xyz](https://geojson.xyz/).

### [Country, State, and City Locations](https://docs.evidence.dev/components/maps/base-map\#country-state-and-city-locations)

|  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| File | Category | Scale | Summary | Size | URL |
| --- | --- | --- | --- | --- | --- |
| populated\_places | misc | 110 | 243 points | 0.4 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_populated\_places.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_populated_places.geojson) |
| populated\_places\_simple | misc | 110 | 243 points | 0.2 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_populated\_places\_simple.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_populated_places_simple.geojson) |
| admin\_0\_countries | political\_countries | 110 | 149 polygons | 0.6 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_0\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_0_countries.geojson) |
| admin\_0\_tiny\_countries | political\_countries | 110 | 37 points | 0.0 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_0\_tiny\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_0_tiny_countries.geojson) |
| admin\_1\_states\_provinces | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces.geojson) |
| admin\_1\_states\_provinces\_lines | political\_states | 110 | 110 lines | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_lines.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_lines.geojson) |
| admin\_1\_states\_provinces\_scale\_rank | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_scale_rank.geojson) |
| admin\_1\_states\_provinces\_shp | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_shp.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_shp.geojson) |
| admin\_1\_states\_provinces\_shp\_scale\_rank | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_shp\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_shp_scale_rank.geojson) |
| populated\_places | misc | 50 | 1,249 points | 2.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_populated\_places.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_populated_places.geojson) |
| populated\_places\_simple | misc | 50 | 1,249 points | 0.9 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_populated\_places\_simple.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_populated_places_simple.geojson) |
| admin\_0\_countries | political\_countries | 50 | 122 polygons | 4.0 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_0\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_countries.geojson) |
| admin\_0\_tiny\_countries | political\_countries | 50 | 76 points | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_0\_tiny\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_tiny_countries.geojson) |
| admin\_0\_tiny\_countries\_scale\_rank | political\_countries | 50 | 76 points | 0.0 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_0\_tiny\_countries\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_tiny_countries_scale_rank.geojson) |
| admin\_1\_states\_provinces | political\_states | 50 | 59 polygons | 1.4 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces.geojson) |
| admin\_1\_states\_provinces\_lines | political\_states | 50 | 202 lines | 0.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_lines.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_lines.geojson) |
| admin\_1\_states\_provinces\_scale\_rank | political\_states | 50 | 59 polygons | 1.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_scale_rank.geojson) |
| admin\_1\_states\_provinces\_shp | political\_states | 50 | 59 polygons | 1.4 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_shp.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_shp.geojson) |
| admin\_1\_states\_provinces\_shp\_scale\_rank | political\_states | 50 | 59 polygons | 1.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_shp\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_shp_scale_rank.geojson) |
| populated\_places\_simple | misc | 10 | 7,322 points | 5.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_10m\_populated\_places\_simple.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_10m_populated_places_simple.geojson) |

No Results

|  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| File | Category | Scale | Summary | Size | URL |
| --- | --- | --- | --- | --- | --- |
| populated\_places | misc | 110 | 243 points | 0.4 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_populated\_places.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_populated_places.geojson) |
| populated\_places\_simple | misc | 110 | 243 points | 0.2 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_populated\_places\_simple.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_populated_places_simple.geojson) |
| admin\_0\_countries | political\_countries | 110 | 149 polygons | 0.6 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_0\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_0_countries.geojson) |
| admin\_0\_tiny\_countries | political\_countries | 110 | 37 points | 0.0 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_0\_tiny\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_0_tiny_countries.geojson) |
| admin\_1\_states\_provinces | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces.geojson) |
| admin\_1\_states\_provinces\_lines | political\_states | 110 | 110 lines | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_lines.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_lines.geojson) |
| admin\_1\_states\_provinces\_scale\_rank | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_scale_rank.geojson) |
| admin\_1\_states\_provinces\_shp | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_shp.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_shp.geojson) |
| admin\_1\_states\_provinces\_shp\_scale\_rank | political\_states | 110 | 48 polygons | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_110m\_admin\_1\_states\_provinces\_shp\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_110m_admin_1_states_provinces_shp_scale_rank.geojson) |
| populated\_places | misc | 50 | 1,249 points | 2.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_populated\_places.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_populated_places.geojson) |
| populated\_places\_simple | misc | 50 | 1,249 points | 0.9 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_populated\_places\_simple.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_populated_places_simple.geojson) |
| admin\_0\_countries | political\_countries | 50 | 122 polygons | 4.0 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_0\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_countries.geojson) |
| admin\_0\_tiny\_countries | political\_countries | 50 | 76 points | 0.1 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_0\_tiny\_countries.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_tiny_countries.geojson) |
| admin\_0\_tiny\_countries\_scale\_rank | political\_countries | 50 | 76 points | 0.0 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_0\_tiny\_countries\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_0_tiny_countries_scale_rank.geojson) |
| admin\_1\_states\_provinces | political\_states | 50 | 59 polygons | 1.4 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces.geojson) |
| admin\_1\_states\_provinces\_lines | political\_states | 50 | 202 lines | 0.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_lines.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_lines.geojson) |
| admin\_1\_states\_provinces\_scale\_rank | political\_states | 50 | 59 polygons | 1.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_scale_rank.geojson) |
| admin\_1\_states\_provinces\_shp | political\_states | 50 | 59 polygons | 1.4 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_shp.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_shp.geojson) |
| admin\_1\_states\_provinces\_shp\_scale\_rank | political\_states | 50 | 59 polygons | 1.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_50m\_admin\_1\_states\_provinces\_shp\_scale\_rank.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_50m_admin_1_states_provinces_shp_scale_rank.geojson) |
| populated\_places\_simple | misc | 10 | 7,322 points | 5.3 MB | [https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne\_10m\_populated\_places\_simple.geojson](https://d2ad6b4ur7yvpq.cloudfront.net/naturalearth-3.3.0/ne_10m_populated_places_simple.geojson) |

No Results

All GeoJSON Files

## [Base Map Options](https://docs.evidence.dev/components/maps/base-map\#base-map-options)

[basemap](https://docs.evidence.dev/components/maps/base-map#props-basemap)

URL template for the basemap tiles.

Options:URL

[attribution](https://docs.evidence.dev/components/maps/base-map#props-attribution)

Attribution text to display on the map (e.g., "© OpenStreetMap contributors").

Options:text

[title](https://docs.evidence.dev/components/maps/base-map#props-title)

Optional title displayed above the map.

Options:text

[startingLat](https://docs.evidence.dev/components/maps/base-map#props-startingLat)

Starting latitude for the map center.

Options:latitude coordinate

[startingLong](https://docs.evidence.dev/components/maps/base-map#props-startingLong)

Starting longitude for the map center.

Options:longitude coordinate

[startingZoom](https://docs.evidence.dev/components/maps/base-map#props-startingZoom)

Initial zoom level of the map.

Options:number (1 to 18)

[height](https://docs.evidence.dev/components/maps/base-map#props-height)

Height of the map in pixels.

Options:pixel valueDefault:300

[title](https://docs.evidence.dev/components/maps/base-map#props-title-2)

Title for the map

Options:string

[subtitle](https://docs.evidence.dev/components/maps/base-map#props-subtitle)

Subtitle - appears under the title

Options:string

## [Layer Options](https://docs.evidence.dev/components/maps/base-map\#layer-options)

### [Areas](https://docs.evidence.dev/components/maps/base-map\#areas)

Use the `<Areas/>` component to add an area layer

[data](https://docs.evidence.dev/components/maps/base-map#props-data)

Required

Query result, referenced using curly braces.

Options:query name

[geoJsonUrl](https://docs.evidence.dev/components/maps/base-map#props-geoJsonUrl)

Required

Path to source geoJSON data from - can be a URL (see [Map Resources](https://docs.evidence.dev/components/maps/base-map#map-resources)) or a file in your project.

If the file is in your `static` directory in the root of your project, reference it as `geoJsonUrl="/your_file.geojson"`

Options:URL

[areaCol](https://docs.evidence.dev/components/maps/base-map#props-areaCol)

Required

Column in the data that specifies the area each row belongs to.

Options:column name

[geoId](https://docs.evidence.dev/components/maps/base-map#props-geoId)

Required

Property in the GeoJSON that uniquely identifies each feature.

Options:geoJSON property name

[value](https://docs.evidence.dev/components/maps/base-map#props-value)

Column that determines the value displayed for each area (used for color scale).

Options:column name

[valueFmt](https://docs.evidence.dev/components/maps/base-map#props-valueFmt)

Format string for displaying the value.

Options:format string

[ignoreZoom](https://docs.evidence.dev/components/maps/base-map#props-ignoreZoom)

Stops map from zooming out to show all data for this layer

Options:

true false

Default:false

### [Points](https://docs.evidence.dev/components/maps/base-map\#points)

Use the `<Points/>` component to add an area layer

[data](https://docs.evidence.dev/components/maps/base-map#props-data-2)

Required

Query result, referenced using curly braces.

Options:query name

[lat](https://docs.evidence.dev/components/maps/base-map#props-lat)

Required

Column containing latitude values.

Options:column name

[long](https://docs.evidence.dev/components/maps/base-map#props-long)

Required

Column containing longitude values.

Options:column name

[value](https://docs.evidence.dev/components/maps/base-map#props-value-2)

Column that determines the value displayed at each point.

Options:column name

[valueFmt](https://docs.evidence.dev/components/maps/base-map#props-valueFmt-2)

Format string for displaying the value.

Options:format string

[pointName](https://docs.evidence.dev/components/maps/base-map#props-pointName)

Column containing the names/labels of the points - by default, this is shown as the title of the tooltip.

Options:column name

[ignoreZoom](https://docs.evidence.dev/components/maps/base-map#props-ignoreZoom-2)

Stops map from zooming out to show all data for this layer

Options:

true false

Default:false

### [Bubbles](https://docs.evidence.dev/components/maps/base-map\#bubbles)

Use the `<Bubbles/>` component to add an area layer

[data](https://docs.evidence.dev/components/maps/base-map#props-data-3)

Required

Query result, referenced using curly braces.

Options:query name

[lat](https://docs.evidence.dev/components/maps/base-map#props-lat-2)

Required

Column containing latitude values.

Options:column name

[long](https://docs.evidence.dev/components/maps/base-map#props-long-2)

Required

Column containing longitude values.

Options:column name

[size](https://docs.evidence.dev/components/maps/base-map#props-size)

Required

Column that determines the size displayed for each point.

Options:column name

[sizeFmt](https://docs.evidence.dev/components/maps/base-map#props-sizeFmt)

Format string for displaying the size value in tooltips.

Options:format string

[maxSize](https://docs.evidence.dev/components/maps/base-map#props-maxSize)

Maximum size of the bubbles.

Options:numberDefault:20

[value](https://docs.evidence.dev/components/maps/base-map#props-value-3)

Column that determines the value displayed at each point (used for color scale).

Options:column name

[valueFmt](https://docs.evidence.dev/components/maps/base-map#props-valueFmt-3)

Format string for displaying the value.

Options:format string

[pointName](https://docs.evidence.dev/components/maps/base-map#props-pointName-2)

Column containing the names/labels of the points - by default, this is shown as the title of the tooltip.

Options:column name

[paneType](https://docs.evidence.dev/components/maps/base-map#props-paneType)

Specifies the type of pane where the bubbles will be rendered.

Options:text

[z](https://docs.evidence.dev/components/maps/base-map#props-z)

Represents the z-index value for the pane, controlling its stacking order relative to other panes (higher values are on top, e.g., z=2 is above z=1).

Options:number

[ignoreZoom](https://docs.evidence.dev/components/maps/base-map#props-ignoreZoom-3)

Stops map from zooming out to show all data for this layer

Options:

true false

Default:false

### [Common Layer Options](https://docs.evidence.dev/components/maps/base-map\#common-layer-options)

#### [Color Scale](https://docs.evidence.dev/components/maps/base-map\#color-scale)

[colorPalette](https://docs.evidence.dev/components/maps/base-map#props-colorPalette)

Array of colors used for theming the points or areas based on data.

Options:array of colors

[min](https://docs.evidence.dev/components/maps/base-map#props-min)

Minimum value to use for the color scale.

Options:numberDefault:min of value column

[max](https://docs.evidence.dev/components/maps/base-map#props-max)

Maximum value to use for the color scale.

Options:numberDefault:max of value column

#### [Interactivity](https://docs.evidence.dev/components/maps/base-map\#interactivity)

[link](https://docs.evidence.dev/components/maps/base-map#props-link)

URL to navigate to when a point or area is clicked.

Options:URL

[name](https://docs.evidence.dev/components/maps/base-map#props-name)

Input name. Can be referenced on your page with .

Options:string

#### [Styling](https://docs.evidence.dev/components/maps/base-map\#styling)

[color](https://docs.evidence.dev/components/maps/base-map#props-color)

Color for the points or areas. Use when you want all points or areas to be the same color.

Options:CSS color value

[borderWidth](https://docs.evidence.dev/components/maps/base-map#props-borderWidth)

Width of the border around each point or area.

Options:pixel value

[borderColor](https://docs.evidence.dev/components/maps/base-map#props-borderColor)

Color of the border around each point or area.

Options:CSS color value

[opacity](https://docs.evidence.dev/components/maps/base-map#props-opacity)

Opacity of the points or areas.

Options:number between 0 and 1

#### [Selected State](https://docs.evidence.dev/components/maps/base-map\#selected-state)

[selectedColor](https://docs.evidence.dev/components/maps/base-map#props-selectedColor)

When point or area is selected: Color for the points or areas.

Options:CSS color value

[selectedBorderWidth](https://docs.evidence.dev/components/maps/base-map#props-selectedBorderWidth)

When point or area is selected: Width of the border around each point or area.

Options:pixel value

[selectedBorderColor](https://docs.evidence.dev/components/maps/base-map#props-selectedBorderColor)

When point or area is selected: Color of the border around each point or area.

Options:CSS color value

[selectedOpacity](https://docs.evidence.dev/components/maps/base-map#props-selectedOpacity)

When point or area is selected: Opacity of the points or areas.

Options:number between 0 and 1

#### [Tooltips](https://docs.evidence.dev/components/maps/base-map\#tooltips)

[showTooltip](https://docs.evidence.dev/components/maps/base-map#props-showTooltip)

Whether to show tooltips.

Options:

true false

Default:true

[tooltipType](https://docs.evidence.dev/components/maps/base-map#props-tooltipType)

Determines whether tooltips are activated by hover or click.

Options:

hover click

Default:hover

[tooltipClass](https://docs.evidence.dev/components/maps/base-map#props-tooltipClass)

CSS class applied to the tooltip content. You can pass Tailwind classes into this prop to custom-style the tooltip.

Options:CSS class

[tooltip](https://docs.evidence.dev/components/maps/base-map#props-tooltip)

Configuration for tooltips associated with each area. See below example for format

Options:array of objects

#### [`tooltip` example:](https://docs.evidence.dev/components/maps/base-map\#tooltip-example)

```text-sm javascript
tooltip={[\
    {id: 'zip_code', fmt: 'id', showColumnName: false, valueClass: 'text-xl font-semibold'},\
    {id: 'sales', fmt: 'eur', fieldClass: 'text-[grey]', valueClass: 'text-[green]'},\
    {id: 'zip_code', showColumnName: false, contentType: 'link', linkLabel: 'Click here', valueClass: 'font-bold mt-1'}\
]}
```

#### [All options available in `tooltip`:](https://docs.evidence.dev/components/maps/base-map\#all-options-available-in-tooltip)

- `id`: column ID
- `title`: custom string to use as title of field
- `fmt`: format to use for value
- `showColumnName`: whether to show the column name. If `false`, only the value will be shown
- `contentType`: currently can only be "link"
- `linkLabel`: text to show for a link when contentType="link"
- `formatColumnTitle`: whether to automatically uppercase the first letter of the title. Only applies when `title` not passed explicitly
- `valueClass`: custom Tailwind classes to style the values
- `fieldClass`: custom Tailwind classes to style the column names

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/maps/base-map/index.md)