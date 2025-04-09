[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Last Refreshed](https://docs.evidence.dev/components/ui/last-refreshed)

# Last Refreshed

Displays the last time the data was refreshed. This component is useful for showing users how up-to-date the data is.

preview

code

Last refreshed 3 weeks ago

```text-sm markdown
<LastRefreshed/>
```

## [Examples](https://docs.evidence.dev/components/ui/last-refreshed\#examples)

### [Alternative Prefix](https://docs.evidence.dev/components/ui/last-refreshed\#alternative-prefix)

preview

code

Data last updated 3 weeks ago

```text-sm markdown
<LastRefreshed prefix="Data last updated"/>
```

## [Options](https://docs.evidence.dev/components/ui/last-refreshed\#options)

[prefix](https://docs.evidence.dev/components/ui/last-refreshed#props-prefix)

Text to display before the last refreshed time

Options:stringDefault:Last refreshed

[printShowDate](https://docs.evidence.dev/components/ui/last-refreshed#props-printShowDate)

On print/PDF, will show the date and time rather than "X hours ago".

Options:

true false

Default:true

[dateFmt](https://docs.evidence.dev/components/ui/last-refreshed#props-dateFmt)

If `printShowDate` is `true`, format to use for the date ( [see available formats](https://docs.evidence.dev/core-concepts/formatting))

Options:Excel-style format \| built-in format \| custom format

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/last-refreshed/index.md)