[Home](https://docs.evidence.dev/) [Reference](https://docs.evidence.dev/reference) [CLI](https://docs.evidence.dev/reference/cli)

# [CLI Reference](https://docs.evidence.dev/reference/cli\#cli-reference)

## [Commands](https://docs.evidence.dev/reference/cli\#commands)

|  |  |  |
| --- | --- | --- |
| CLI | VS Code | Description |
| --- | --- | --- |
| `npx degit evidence-dev/template my-project` | `Evidence: New Evidence Project` | Create a new project from the template |
| `npm run sources` | `Evidence: Run Sources` | Extract data from sources |
| `npm run dev` | `Evidence: Start Server` | Start the development server in the current directory |
| `npm run build` | `Evidence: Build` | Build the app for production |
| `npm run build:strict` | `Evidence: Built Strict` | Build, but fails on query or component errors |
| `npm run preview` | N/A | Preview the built site |
| `Ctrl / Cmd` \+ `C` | `Evidence: Stop Server` | Stop the dev server (when running) |
| `r` | N/A | Restart the dev server (when running) |

No Results

|  |  |  |
| --- | --- | --- |
| CLI | VS Code | Description |
| --- | --- | --- |
| `npx degit evidence-dev/template my-project` | `Evidence: New Evidence Project` | Create a new project from the template |
| `npm run sources` | `Evidence: Run Sources` | Extract data from sources |
| `npm run dev` | `Evidence: Start Server` | Start the development server in the current directory |
| `npm run build` | `Evidence: Build` | Build the app for production |
| `npm run build:strict` | `Evidence: Built Strict` | Build, but fails on query or component errors |
| `npm run preview` | N/A | Preview the built site |
| `Ctrl / Cmd` \+ `C` | `Evidence: Stop Server` | Stop the dev server (when running) |
| `r` | N/A | Restart the dev server (when running) |

No Results

## [Options](https://docs.evidence.dev/reference/cli\#options)

Append flags with an extra `--` after the command to modify behavior.

For example, `npm run dev -- --port 4000` will start the development server on port 4000.

Some of the most common are:

|  |  |  |  |
| --- | --- | --- | --- |
| Command | Flag | Description | Detail |
| --- | --- | --- | --- |
| `sources` | `--changed` | Run sources whose queries have changed | null |
| `sources` | `--sources [source_name]` | Run sources from the specified sources | Seperate with commas `--sources source1,source2` |
| `sources` | `--queries [query_name]` | Run the specified queries | Seperate with commas |
| `sources` | `--debug` | Show debug output | null |
| `dev` | `--open [path]` | Open browser to <code>path</code> on startup | Default `--open /` opens in root of the project |
| `dev` | `--host [host]` | Specify hostname | `--host 0.0.0.0` can be helpful in containers |
| `dev` | `--port ` | Specify port | Automatically increment if default `3000` is in use |

No Results

|  |  |  |  |
| --- | --- | --- | --- |
| Command | Flag | Description | Detail |
| --- | --- | --- | --- |
| `sources` | `--changed` | Run sources whose queries have changed | null |
| `sources` | `--sources [source_name]` | Run sources from the specified sources | Seperate with commas `--sources source1,source2` |
| `sources` | `--queries [query_name]` | Run the specified queries | Seperate with commas |
| `sources` | `--debug` | Show debug output | null |
| `dev` | `--open [path]` | Open browser to <code>path</code> on startup | Default `--open /` opens in root of the project |
| `dev` | `--host [host]` | Specify hostname | `--host 0.0.0.0` can be helpful in containers |
| `dev` | `--port ` | Specify port | Automatically increment if default `3000` is in use |

No Results

Evidence's `dev` and `build` commands run using Vite, and so support [Vite's options](https://vitejs.dev/guide/cli.html#options).

Evidence's `preview` command runs using `npx serve` and supports [Serve's options](https://github.com/vercel/serve/blob/main/source/utilities/cli.ts#L30)

## [Environment Variables](https://docs.evidence.dev/reference/cli\#environment-variables)

You can set environment variables to configure Evidence in production. Most of these are used to set database credentials securely.

The format of environment variables for database credentials is `EVIDENCE_SOURCE__[source_name]__[variable_name]`.

You can copy all your current environment variable values from the settings page at [localhost:3000/settings](http://localhost:3000/settings).

N.B. Environment variables are **case sensitive**, so you should preserve the case specified in the settings page.

### [.env Files](https://docs.evidence.dev/reference/cli\#env-files)

Evidence will read in environment variables from a `.env` file in the root of your project. This is useful for local development.

### [Environment Variables in Source Queries](https://docs.evidence.dev/reference/cli\#environment-variables-in-source-queries)

Environment variables to be used in source queries should be prefixed with `EVIDENCE_VAR__` (note the double underscore). They can be used in source queries with `${EVIDENCE_VAR__variable_name}`.

```bash text-sm
EVIDENCE_VAR__customer_name="Acme Corporation"
```

```bash text-sm
select *
from orders
where customer_name = '${customer_name}'
```

The quotes would be omitted if the variable was not a string.

### [Environment Variables in Pages](https://docs.evidence.dev/reference/cli\#environment-variables-in-pages)

Environment variables to be used in pages should be prefixed with `VITE_`. They can be accessed with `import.meta.env.VITE_variable_name`.

`.env`

```bash text-sm
VITE_customer_attribute=premium
```

`index.md`

```svelte text-sm
<script>
  const customer_attribute = import.meta.env.VITE_customer_attribute;
</script>

{#if customer_attribute === 'premium'}

Premium content

{:else if customer_attribute === 'free'}

Free content

{/if}
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/reference/cli/index.md)