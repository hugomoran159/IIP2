[Home](https://docs.evidence.dev/) [Plugins](https://docs.evidence.dev/plugins) [Create Data Source Plugin](https://docs.evidence.dev/plugins/create-source-plugin)

# Create Data Source Plugin

To see a working example of a data source plugin, the [Evidence postgres source plugin](https://github.com/evidence-dev/evidence/tree/main/packages/datasources/postgres) is a good
reference.

## [Get started](https://docs.evidence.dev/plugins/create-source-plugin\#get-started)

To get started, go to [the data source template repo](https://github.com/evidence-dev/datasource-template) and click to "Use This Template". Then, follow the directions in the `README` in that repo.

## [Options Specification](https://docs.evidence.dev/plugins/create-source-plugin\#options-specification)

Evidence Datasources must provide an `options` export; this is used to
build UI and validation to ensure an excellent UX for Evidence users.

Options can have the following fields:

[title](https://docs.evidence.dev/plugins/create-source-plugin#props-title)

Required

Name or Title of the option

Type:string

[type](https://docs.evidence.dev/plugins/create-source-plugin#props-type)

Required

Control to show

Type:

stringnumberbooleanselectfile

[secret](https://docs.evidence.dev/plugins/create-source-plugin#props-secret)

Secret values are placed in `connection.options.yaml`, which is not source controlled

Type:boolean

[shown](https://docs.evidence.dev/plugins/create-source-plugin#props-shown)

Displays value in UI elements (e.g. for usernames, that should not be source controlled but are not 'secret'. Otherwise the field will display as ∙∙∙)

Type:boolean

[virtual](https://docs.evidence.dev/plugins/create-source-plugin#props-virtual)

Disables saving a field, useful for credential files

Type:boolean

[references](https://docs.evidence.dev/plugins/create-source-plugin#props-references)

Indicates that the field should get its value from another field if it is available, useful for credential files. Formatted as a [json path](https://www.npmjs.com/package/@astronautlabs/jsonpath)

Type:string

[forceReference](https://docs.evidence.dev/plugins/create-source-plugin#props-forceReference)

If true, the input is disabled and the value can only come from a reference

Type:boolean

[fileFormat](https://docs.evidence.dev/plugins/create-source-plugin#props-fileFormat)

If `type` is `file`, set how it should be parsed. It will then be available to `references`

Type:

jsonyaml

[description](https://docs.evidence.dev/plugins/create-source-plugin#props-description)

Description of the option, shown as a hint in UI

Type:string

[children](https://docs.evidence.dev/plugins/create-source-plugin#props-children)

See [children](https://docs.evidence.dev/plugins/create-source-plugin#children)

Type:Record<string\|number\|boolean, Options>

[required](https://docs.evidence.dev/plugins/create-source-plugin#props-required)

Indicates that the user must provide this option

Type:boolean

[options](https://docs.evidence.dev/plugins/create-source-plugin#props-options)

Available options for `select` type

Type:Array<{label: string, value:string}>

[nest](https://docs.evidence.dev/plugins/create-source-plugin#props-nest)

Determines behavior of `children`

Type:boolean

[default](https://docs.evidence.dev/plugins/create-source-plugin#props-default)

Default Value

Type:

stringnumberboolean

### [Children](https://docs.evidence.dev/plugins/create-source-plugin\#children)

Many datasources have variable configuration (e.g. if ssl is enabled for postgres, then an ssl mode can be selected), and Evidence
options support this workflow.

Consider this partial postgres ssl option:

```text-sm javascript
ssl: {
    type: 'boolean',
    // ...
    nest: true,
    children: {
        [true]: {
            sslmode: {
                // ...
            }
        }
    }
},
```

`ssl.children` is a record of possible values to an additional set of options that are exposed then the values match.
In this example, the `sslmode` option is only displayed when `ssl` is true.

The resulting type of this option is:

```text-sm typescript
{ ssl: false } | { ssl: { sslmode: string } }
```

In cases where you want a flat object, rather than a nested object; set `nest` to false.

This would produce

```text-sm typescript
{ ssl: false } | { ssl: true, sslmode: string }
```

## [Promoting Your Plugin](https://docs.evidence.dev/plugins/create-source-plugin\#promoting-your-plugin)

If you are building a plugin for other Evidence users, [let us know in Slack](https://slack.evidence.dev/) and we can share it with the community.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/plugins/create-source-plugin/index.md)