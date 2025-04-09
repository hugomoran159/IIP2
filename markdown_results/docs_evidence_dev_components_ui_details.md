[Home](https://docs.evidence.dev/) [Components](https://docs.evidence.dev/components) [UI](https://docs.evidence.dev/components/ui) [Details](https://docs.evidence.dev/components/ui/details)

# Details

The details component allows you to add a collapsible section to your markdown. This is useful for adding additional information that you don't want to be visible by default, but can be expanded by the reader.

## [Default state](https://docs.evidence.dev/components/ui/details\#default-state)

preview

code

Definitions

```text-sm markdown
<Details title="Definitions">

    Definition of metrics in Solutions Targets

    ### Time to Proposal

    Average number of days it takes to create a proposal for a customer

    *Calculation:*
    Sum of the number of days it took to create each proposal, divided by the number of proposals created

    *Source:*
    Hubspot

</Details>
```

## [Expanded state](https://docs.evidence.dev/components/ui/details\#expanded-state)

preview

code

Definitions

Definition of metrics in Solutions Targets

### [Time to Proposal](https://docs.evidence.dev/components/ui/details\#time-to-proposal-1)

Average number of days it takes to create a proposal for a customer

_Calculation:_
Sum of the number of days it took to create each proposal, divided by the number of proposals created

_Source:_
Hubspot

```text-sm markdown
<Details title="Definitions">

    Definition of metrics in Solutions Targets

    ### Time to Proposal

    Average number of days it takes to create a proposal for a customer

    *Calculation:*
    Sum of the number of days it took to create each proposal, divided by the number of proposals created

    *Source:*
    Hubspot

</Details>
```

## [Options](https://docs.evidence.dev/components/ui/details\#options)

[title](https://docs.evidence.dev/components/ui/details#props-title)

The text shown next to the triangle icon.

Default:Details

[open](https://docs.evidence.dev/components/ui/details#props-open)

Whether expanded by default.

Options:

true false

Default:false

[printShowAll](https://docs.evidence.dev/components/ui/details#props-printShowAll)

On print/PDF, the Details component will expand by default. Turn this off to leave the component collapsed in print.

Options:

true false

Default:true

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/components/ui/details/index.md)