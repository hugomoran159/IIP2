[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Themes](https://docs.evidence.dev/core-concepts/themes)

# Themes

Customize the appearance of your Evidence application in light and dark mode.

# [Appearance Modes](https://docs.evidence.dev/core-concepts/themes\#appearance-modes)

Evidence supports three appearance modes: light, dark, and system. By default, new Evidence apps use the system mode and allow users to switch to light or dark via the appearance switcher.

When the appearance is `system`, the user's preferred appearance from their operating system is used.

The default appearance configuration is listed below, as well as in the [Evidence Template](https://github.com/evidence-dev/template/blob/main/evidence.config.yaml).

Default appearance configuration

## [Options](https://docs.evidence.dev/core-concepts/themes\#options)

[default](https://docs.evidence.dev/core-concepts/themes#props-default)

The default appearance mode.

Options:

dark light system

Default:light

[switcher](https://docs.evidence.dev/core-concepts/themes#props-switcher)

Shows/hides the appearance switcher in the kebab menu in the top right which allows users to switch the appearance of your application between light and dark mode.

Options:

true false

Default:false

## [Migration](https://docs.evidence.dev/core-concepts/themes\#migration)

To enable dark mode in an Evidence application created before themes was released, replace `evidence.plugins.yaml` with `evidence.config.yaml`:

```text-sm yaml
appearance:
    default: system
    switcher: true
plugins:
    [contents of evidence.plugins.yaml, indented one additional level]
```

# [Theme](https://docs.evidence.dev/core-concepts/themes\#theme)

The theme configuration defines the colors used by your app.

The theme consists of 3 elements that define colors for different purposes:

- [Color palettes](https://docs.evidence.dev/core-concepts/themes#color-palettes) configure colors for charts with different data series (e.g. [Bar Charts](https://docs.evidence.dev/components/charts/bar-chart#props-colorPalette)).
- [Color scales](https://docs.evidence.dev/core-concepts/themes#color-scales) configure color ranges for charts with continuous data (e.g. [Heatmaps](https://docs.evidence.dev/components/charts/heatmap#props-colorScale)).
- [Colors](https://docs.evidence.dev/core-concepts/themes#colors) configure colors of UI elements (e.g. background, text, inputs).

You can pass any valid CSS color values to these properties (hexadecimal, RGB, HSL, named CSS colors, etc).

The default theme configuration is listed below, as well as in the [Evidence Template](https://github.com/evidence-dev/templates/blob/main/evidence.config.yaml).

Default theme configuration

## [Color Palettes](https://docs.evidence.dev/core-concepts/themes\#color-palettes)

You can modify the default chart color palette, or create a custom palette for individual charts via their `colorPalette` prop.

Color palettes can have any number of colors listed. If a chart has more series than there are colors in a color palette, the colors will be reused.

### [Default Color Palette](https://docs.evidence.dev/core-concepts/themes\#default-color-palette)

The `default` color palette is used by all series-based charts (e.g. [Bar Charts](https://docs.evidence.dev/components/charts/bar-chart#props-colorPalette), [Line Charts](https://docs.evidence.dev/components/charts/line-chart#props-colorPalette)).

You can configure the default color palette for light and dark mode individually (different colors for each):

```text-sm yaml
theme:
    colorPalettes:
        default:
            light:
                - "#1d4ed8"
                - "#0f766e"
                - "#a16207"
                - "#c2410c"
                - "#7e22ce"
            dark:
                - "#93c5fd"
                - "#5eead4"
                - "#fde047"
                - "#fdba74"
                - "#d8b4fe"
```

…or together (same colors for both):

```text-sm yaml
theme:
    colorPalettes:
        default:
            - "#3b82f6"
            - "#14b8a6"
            - "#eab308"
            - "#f97316"
            - "#a855f7"
```

### [Custom Color Palettes](https://docs.evidence.dev/core-concepts/themes\#custom-color-palettes)

You can define your own custom color palettes in the same way, just replace `default` with your color palette's name:

```text-sm yaml
theme:
    colorPalettes:
        myCustomPalette:
            light:
                - "#e11d48"
                - "#be185d"
                - "#6d28d9"
            dark:
                - "#fb7185"
                - "#f9a8d4"
                - "#c4b5fd"
```

Then use it in the `colorPalette` prop

```text-sm markdown
<BarChart
    data={my_data}
    colorPalette=myCustomPalette
/>
```

### [Props](https://docs.evidence.dev/core-concepts/themes\#props)

The `colorPalette` prop accepted by many components accepts a color palette in several different formats to reduce the friction of theming your app.

1. **Use a color palette name from your theme.** Its configured light and dark values will be used.



```text-sm markdown
<BarChart
       data={my_data}
       colorPalette=myColorPalette
/>
```

2. **Use a list of color names from your theme.** Their configured light and dark values will be used.



```text-sm markdown
<BarChart
       data={my_data}
       colorPalette={[\
           'primary',\
           'accent',\
           'myCustomColor',\
       ]}
/>
```

3. **Use a list of colors (e.g. hex codes).** They will be automatically converted to similar colors for dark mode.



```text-sm markdown
<BarChart
       data={my_data}
       colorPalette={[\
           "#3b82f6",\
           "#14b8a6",\
           "#eab308",\
           "#f97316",\
           "#a855f7",\
       ]}
/>
```

4. **Use a list of pairs of colors** to explicitly define light and dark mode values. The first column will be used when your application is in light mode, and the second when its in dark mode.



```text-sm markdown
<BarChart
       data={my_data}
       colorPalette={[\
           ["#1d4ed8", "#93c5fd"],\
           ["#0f766e", "#5eead4"],\
           ["#a16207", "#fde047"],\
           ["#c2410c", "#fdba74"],\
           ["#7e22ce", "#d8b4fe"],\
       ]}
/>
```


## [Color Scales](https://docs.evidence.dev/core-concepts/themes\#color-scales)

You can modify the default chart color palette, or create a custom palette for individual charts via their `colorScale` prop.

Color scales can have any number of colors listed. The colors will be blended into a gradient for values to interpolate from.

### [Default Color Scale](https://docs.evidence.dev/core-concepts/themes\#default-color-scale)

The `default` color scale is used by charts that represent continuous data.

You can configure the default color palette for light and dark mode individually (different colors for each):

```text-sm yaml
theme:
    colorScales:
        default:
            light:
                - "#0d9488"
                - "#4f46e5"
            dark:
                - "#5eead4"
                - "#a5b4fc"
```

…or together (same colors for both):

```text-sm yaml
theme:
    colorScales:
        default:
            - "#eab308"
            - "#22c55e"
```

### [Custom Color Scales](https://docs.evidence.dev/core-concepts/themes\#custom-color-scales)

You can define your own custom color scales in the same way, just replace `default` with your color scale's name:

```text-sm yaml
theme:
    colorScales:
        myCustomScale:
            light:
                - "#f97316"
                - "#ef4444"
            dark:
                - "#fdba74"
                - "#fb7185"
```

Then use it in the `colorScale` prop

```text-sm markdown
<DataTable data={country_summary}>
    <Column id=country />
    <Column id=value_usd contentType=colorscale colorScale=myCustomScale />
</DataTable>
```

### [Props](https://docs.evidence.dev/core-concepts/themes\#props-1)

The `colorScale` prop accepted by many components accepts a color scale in several different formats to reduce the friction of theming your app.

1. **Use a color scale name from your theme.** Its configured light and dark values will be used.



```text-sm markdown
<BarChart
       data={my_data}
       colorScale=myColorScale
/>
```

2. **Use a list of color names from your theme.** Their configured light and dark values will be used.



```text-sm markdown
<BarChart
       data={my_data}
       colorScale={[\
           'primary',\
           'accent',\
       ]}
/>
```

3. **Use a list of colors (e.g. hex codes).** They will be automatically converted to similar colors for dark mode.



```text-sm markdown
<BarChart
       data={my_data}
       colorScale={["#3b82f6", "#14b8a6"]}
/>
```

4. **Use a list of pairs of colors** to explicitly define light and dark mode values. The first column will be used when your application is in light mode, and the second when its in dark mode.



```text-sm markdown
<BarChart
       data={my_data}
       colorScale={[\
           ["#1d4ed8", "#93c5fd"],\
           ["#0f766e", "#5eead4"],\
       ]}
/>
```


## [Colors](https://docs.evidence.dev/core-concepts/themes\#colors)

Evidence uses a fixed set of color "tokens" for all UI elements in the entire application. This allows you to create a customized look and feel with only a couple lines of configuration.

|  |  |  |
| --- | --- | --- |
| Color | Purpose | Where its used |
| --- | --- | --- |
| primary | Represents your project/brand | Logo color, buttons, links, DimensionGrid |
| accent | Focuses your attention | Map selected state (Chart selected state coming soon!) |
| base | The base color of your application | Background and text colors |
| info | Provide information | Alerts, annotations |
| positive | Indicate something is good | Alerts, annotations, Delta indicator |
| warning | Warn readers | Alerts, annotations |
| negative | Indicate something is bad | Alerts, annotations, Delta indicator |

No Results

|  |  |  |
| --- | --- | --- |
| Color | Purpose | Where its used |
| --- | --- | --- |
| primary | Represents your project/brand | Logo color, buttons, links, DimensionGrid |
| accent | Focuses your attention | Map selected state (Chart selected state coming soon!) |
| base | The base color of your application | Background and text colors |
| info | Provide information | Alerts, annotations |
| positive | Indicate something is good | Alerts, annotations, Delta indicator |
| warning | Warn readers | Alerts, annotations |
| negative | Indicate something is bad | Alerts, annotations, Delta indicator |

No Results

You can modify existing color tokens, or create your own to use in charts and other UI elements.

### [Overriding Colors](https://docs.evidence.dev/core-concepts/themes\#overriding-colors)

You can override a color for light and dark mode individually (different colors for each):

```text-sm yaml
theme:
	colors:
		primary:
			light: "#dc2626"
			dark: "#f87171"
		accent:
			light: "#7c3aed"
			dark: "#a78bfa"
```

…or together (same colors for both):

```text-sm yaml
theme:
	colors:
		primary: "#ef4444"
		accent: "#a855f7"
```

### [Defining Your Own Colors](https://docs.evidence.dev/core-concepts/themes\#defining-your-own-colors)

You can define your own custom colors in the same way, just replace the color name with your custom color's name:

```text-sm yaml
theme:
	colors:
		myColor: "#10b981"
		myOtherColor:
			light: "#c026d3"
			dark: "#f472b6"
```

Then use them in component props

```text-sm markdown
<Tabs color=myColor>
	<Tab label="Tab 1" id="tab1">Tab 1 content</Tab>
	<Tab label="Tab 2" id="tab2">Tab 2 content</Tab>
</Tabs>
```

```text-sm markdown
<BarChart
	data={my_data}
	fillColor=myOtherColor
/>
```

### [Props](https://docs.evidence.dev/core-concepts/themes\#props-2)

The color props accepted by many components (e.g. [`fillColor`](https://docs.evidence.dev/components/charts/bar-chart#props-fillColor), [`labelColor`](https://docs.evidence.dev/components/charts/annotations#props-labelColor)) accept a color in several different formats to reduce the friction of theming your app.

1. **Use a color name from your theme.** Its configured light and dark values will be used.



```text-sm markdown
<BarChart
       data={my_data}
       fillColor=primary
/>
```

2. **Use a single color (e.g. hex code).** It will be automatically converted to a similar color for dark mode.



```text-sm markdown
<BarChart
       data={my_data}
       fillColor="#3b82f6"
/>
```

3. **Use a pair of colors** to explicitly define light and dark mode values. The first color will be used when your application is in light mode, and the second when its in dark mode.



```text-sm markdown
<BarChart
       data={my_data}
       fillColor={["#1d4ed8", "#93c5fd"]}
/>
```


## [Advanced](https://docs.evidence.dev/core-concepts/themes\#advanced)

The [colors listed above](https://docs.evidence.dev/core-concepts/themes#colors) are the bare minimum you should configure to theme your application. If you need more control, there are other colors you can customize.

|  |  |  |
| --- | --- | --- |
| Color | Where its used | Default |
| --- | --- | --- |
| primary-content | Text color used on top of a primary background | A readable shade of primary |
| accent-content | Text color used on top of an accent background | A readable shade of accent |
| base-100 | Page background color | Alias of \`base\` |
| base-200 | Secondary page background color | A shade of base-100 |
| base-300 | Tertiary page background color | A shade of base-100 |
| base-content-muted | Muted text color | A shade of base-100 |
| base-content | Body text color | A shade of base-100 |
| base-heading | Header text color | A shade of base-100 |
| info-content | Text color used on top of an info background | A readable shade of info |
| positive-content | Text color used on top of a positive background | A readable shade of positive |
| warning-content | Text color used on top of a warning background | A readable shade of warning |
| negative-content | Text color used on top of a negative background | A readable shade of negative |

No Results

|  |  |  |
| --- | --- | --- |
| Color | Where its used | Default |
| --- | --- | --- |
| primary-content | Text color used on top of a primary background | A readable shade of primary |
| accent-content | Text color used on top of an accent background | A readable shade of accent |
| base-100 | Page background color | Alias of \`base\` |
| base-200 | Secondary page background color | A shade of base-100 |
| base-300 | Tertiary page background color | A shade of base-100 |
| base-content-muted | Muted text color | A shade of base-100 |
| base-content | Body text color | A shade of base-100 |
| base-heading | Header text color | A shade of base-100 |
| info-content | Text color used on top of an info background | A readable shade of info |
| positive-content | Text color used on top of a positive background | A readable shade of positive |
| warning-content | Text color used on top of a warning background | A readable shade of warning |
| negative-content | Text color used on top of a negative background | A readable shade of negative |

No Results

These colors are included in the [Tailwind](https://tailwindcss.com/) configuration for your Evidence application, so you can use them in your own HTML elements or custom Svelte components.

preview

code

Hello!

```text-sm markdown
<div class="bg-primary border border-primary p-4 text-primary-content">Hello!</div>
```

## [Custom Styles](https://docs.evidence.dev/core-concepts/themes\#custom-styles)

Evidence uses [Tailwind CSS](https://tailwindcss.com/) to style Evidence components and markdown, and you can use Tailwind to add your own styles.

To style with Tailwind you add _classes_ to HTML elements. You can use any HTML element in your markdown.

For more information on using Tailwind, see the [Tailwind documentation](https://tailwindcss.com/docs).

Tailwind removes styling from HTML elements by default, so should add your own styles to `<h1/>`, `<a/>` etc.

### [Using the Evidence Default Styles in Custom HTML](https://docs.evidence.dev/core-concepts/themes\#using-the-evidence-default-styles-in-custom-html)

Adding the `markdown` class to an element will style it the same as Evidence markdown, e.g. `<h1 class='markdown'/>`.

### [Examples](https://docs.evidence.dev/core-concepts/themes\#examples)

#### [Customize Fonts](https://docs.evidence.dev/core-concepts/themes\#customize-fonts)

preview

code

This is the default text style, which is used when you write text in a markdown file.


This red italic serif text is defined inside a HTML p (paragraph) element.

This is primary colored text using a monospace font, and a custom top margin.

```text-sm markdown
This is the default text style, which is used when you write text in a markdown file.

<p class="text-red-600 italic font-serif">This red italic serif text is defined inside a HTML p (paragraph) element.</p>

<p class="font-mono text-primary mt-3">This is primary colored text using a monospace font, and a custom top margin.</p>
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/themes/index.md)