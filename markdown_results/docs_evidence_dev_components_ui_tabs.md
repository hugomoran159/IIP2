[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Tabs](https://docs.evidence.dev/components/ui/tabs)

# Tabs

Use Tabs to organize content across multiple panes.

preview

code

Content of the First Tab

You can use **markdown** here too!

```text-sm markdown
<Tabs>
    <Tab label="First Tab">
        Content of the First Tab

        You can use **markdown** here too!
    </Tab>
    <Tab label="Second Tab">
        Content of the Second Tab

        Here's a [link](https://www.google.com)
    </Tab>
</Tabs>
```

## [Examples](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#examples)

### [Full Width](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#full-width)

preview

code

Content of the First Tab

```text-sm markdown
<Tabs fullWidth=true>
    <Tab label="First Tab">
        Content of the First Tab
    </Tab>
    <Tab label="Second Tab">
        Content of the Second Tab
    </Tab>
</Tabs>
```

### [Theme Color](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#theme-color)

preview

code

Content of the First Tab

```text-sm markdown
<Tabs color=primary>
    <Tab label="Primary Tabs">
        Content of the First Tab
    </Tab>
    <Tab label="Second Tab">
        Content of the Second Tab
    </Tab>
</Tabs>
```

### [Custom Color](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#custom-color)

preview

code

Content of the First Tab

```text-sm markdown
<Tabs color=#ff0000>
    <Tab label="Red Tabs">
        Content of the First Tab
    </Tab>
    <Tab label="Second Tab">
        Content of the Second Tab
    </Tab>
</Tabs>
```

### [Background Color](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#background-color)

preview

code

Content of the First Tab

```text-sm markdown
<Tabs background=true>
    <Tab label="First Tab">
        Content of the First Tab
    </Tab>
    <Tab label="Second Tab">
        Content of the Second Tab
    </Tab>
</Tabs>
```

### [Persist Selected Tab to URL](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#persist-selected-tab-to-url)

preview

code

Click Second id Tab and notice the the url updates!

```text-sm markdown
<Tabs id="example-tab">
    <Tab label="One">
        Click Second id Tab and notice the the url updates!
    </Tab>
    <Tab label="Two">
        Refresh the page and the tab you selected persists!
    </Tab>
</Tabs>
```

# [Tabs](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#tabs)

## [Options](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#options)

[id](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-id)

Unique Id for this set of tabs. When set, the selected tab is included in the URL so it can be shared.

Options:string

[color](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-color)

Color for the active tab. Accepts [theme tokens](https://docs.evidence.dev/core-concepts/themes#colors)

Options:Any valid hex, rgb, or hsl stringDefault:base-content

[fullWidth](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-fullWidth)

Tabs take up full width of page

Options:

true false

Default:false

[background](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-background)

Include background color on active tab. Color is automatically determined based on `color` prop

Options:

true false

Default:false

# [Tab](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#tab)

## [Options](https://docs.evidence.dev/components/ui/tabs?example-tab=One\#options-1)

[label](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-label)

Required

Label for the tab

[id](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-id-2)

Unique Id for this tab. Only needed if 2 tabs have the same label (not recommended).

[printShowAll](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-printShowAll)

On print/PDF, the Tabs will repeat to show all content by default. Turn this off to leave the component collapsed in print.

Options:

true false

Default:true

[description](https://docs.evidence.dev/components/ui/tabs?example-tab=One#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/tabs/index.md)