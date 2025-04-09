[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [If / Else](https://docs.evidence.dev/core-concepts/if-else)

# If / Else

Programmatically control what is displayed using data through `{#if}` and `{:else}` blocks.

## [If and Else Statements](https://docs.evidence.dev/core-concepts/if-else\#if-and-else-statements)

Conditionals are useful for managing information overload, and ensuring that your reporting is consistently showing actionable information.

Conditionals allow you to show a section of your document if a condition is met. You can optionally include `{:else}` and `{:else if}` blocks inside of your `{#if}...{/if}` blocks.

```text-sm javascript
{#if condition}

Display some content.

{:else if another condition}

Another thing instead.

{:else }

Something completely different.

{/if}
```

## [Example](https://docs.evidence.dev/core-concepts/if-else\#example)

Hide a table if it is empty.

```text-sm javascript
{#if query_name.length !== 0}

<DataTable data={query_name}>

{/if}
```

## [Another Example](https://docs.evidence.dev/core-concepts/if-else\#another-example)

Imagine creating reports to encourage sales leaders "up-sell" low margin customers, but only when there were enough low-margin customers to do that work in-bulk. This could be done using a conditional.

```text-sm javascript
{#if low_margin_customers.length > 15}

The following customers are generating low margins.

Consider re-allocating an account management call block to up-sell these customers.

<DataTable data={low_margin_customers}/>

{:else }

There are fewer than fifteen low margin customers, which is not enough to fill a call block.

{/if}
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/if-else/index.md)