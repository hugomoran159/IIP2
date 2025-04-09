[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Accordion](https://docs.evidence.dev/components/ui/accordion)

# Accordion

Use accordions to organize content into collapsible sections.

preview

code

Item 1

Item 2

Item 3

```text-sm markdown
<Accordion>
  <AccordionItem title="Item 1">

    This is the first item's accordion body.

    You can use **markdown** here too!

    Make sure to include an empty line after the component if you want to use markdown.

  </AccordionItem>
  <AccordionItem title="Item 2">

    This is the second item's accordion body with <b>bold text</b>.

  </AccordionItem>
  <AccordionItem title="Item 3">

    This is the third item's accordion body.

  </AccordionItem>
</Accordion>
```

## [Examples](https://docs.evidence.dev/components/ui/accordion\#examples)

### [Single Accordion](https://docs.evidence.dev/components/ui/accordion\#single-accordion)

preview

code

Item 1

Item 2

Item 3

```text-sm markdown
<Accordion single>
  <AccordionItem title="Item 1">
    <p>Content 1</p>
  </AccordionItem>
  <AccordionItem title="Item 2">
    <p>Content 2</p>
  </AccordionItem>
  <AccordionItem title="Item 3">
    <p>Content 3</p>
  </AccordionItem>
</Accordion>
```

### [Overriding Styles](https://docs.evidence.dev/components/ui/accordion\#overriding-styles)

Use the `class` options to override the styles on the accordion.

preview

code

Item 1

Item 2

Item 3

```text-sm markdown
<Accordion class="rounded-xl bg-gray-50 px-4 mt-4">
  <AccordionItem title="Item 1" class="border-none">
    <p>Content 1</p>
  </AccordionItem>
  <AccordionItem title="Item 2" class="border-none">
    <p>Content 2</p>
  </AccordionItem>
  <AccordionItem title="Item 3" class="border-none">
    <p>Content 3</p>
  </AccordionItem>
</Accordion>
```

### [Title Slot](https://docs.evidence.dev/components/ui/accordion\#title-slot)

Pass components into the accordion title by using the slot `title`.

preview

code

Custom Title 36.6%

Item 2

Item 3

```text-sm markdown
<Accordion>
  <AccordionItem title="Item 1">
    <span slot='title'>Custom Title <Value data={growth} fmt=pct1 /></span>
    Content 1
  </AccordionItem>
  <AccordionItem title="Item 2">
    <p>Content 2</p>
  </AccordionItem>
  <AccordionItem title="Item 3">
    <p>Content 3</p>
  </AccordionItem>
</Accordion>
```

## [Options](https://docs.evidence.dev/components/ui/accordion\#options)

### [Accordion](https://docs.evidence.dev/components/ui/accordion\#accordion)

[single](https://docs.evidence.dev/components/ui/accordion#props-single)

When true, only a single accordian item can be open at once.

Options:

true false

[class](https://docs.evidence.dev/components/ui/accordion#props-class)

Pass custom classes to control the styling of the accordion body. Supports [tailwind classes](https://tailwindcss.com/).

### [AccordionItem](https://docs.evidence.dev/components/ui/accordion\#accordionitem)

[title](https://docs.evidence.dev/components/ui/accordion#props-title)

Required

The title of the accordion item. This will be displayed as the header.

[class](https://docs.evidence.dev/components/ui/accordion#props-class-2)

Pass custom classes to control the styling of an accordion item. Supports [tailwind classes](https://tailwindcss.com/).

[description](https://docs.evidence.dev/components/ui/accordion#props-description)

Adds an info icon with description tooltip on hover

Options:string

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/accordion/index.md)