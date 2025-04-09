[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Modal](https://docs.evidence.dev/components/ui/modal)

# Modal

preview

code

Open Modal

```text-sm markdown
<Modal title="Title" buttonText='Open Modal'>

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

</Modal>
```

## [Styling](https://docs.evidence.dev/components/ui/modal\#styling)

Modals support markdown in the body, but you need to leave whitespace between the text and the modal tags.

preview

code

Open Modal

```text-sm markdown
<Modal title="Title" buttonText='Open Modal'>

**bold** and _italic_ text is supported.

</Modal>
```

## [Including Components](https://docs.evidence.dev/components/ui/modal\#including-components)

You can include components inside a Modal, like charts or tables:

preview

code

Click to See Chart

```text-sm svelte
<Modal title='Chart Example' buttonText='Click to See Chart'>
    <LineChart
        data={orders_by_month}
        x=order_month
        y=sales_usd0k
    />
</Modal>
```

## [Options](https://docs.evidence.dev/components/ui/modal\#options)

[buttonText](https://docs.evidence.dev/components/ui/modal#props-buttonText)

Required

The text displayed on the button that triggers the modal.

Options:string

[title](https://docs.evidence.dev/components/ui/modal#props-title)

The title of the modal. Visible at the top of the modal when it is open

Options:string

[open](https://docs.evidence.dev/components/ui/modal#props-open)

A boolean value that determines whether the modal is closed by default.

Options:

true false

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/modal/index.md)