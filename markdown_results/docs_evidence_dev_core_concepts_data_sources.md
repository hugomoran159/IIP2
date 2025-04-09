[Home](https://docs.evidence.dev/) [Core Concepts](https://docs.evidence.dev/core-concepts) [Data Sources](https://docs.evidence.dev/core-concepts/data-sources)

# Data Sources

## [Overview of Data Sources](https://docs.evidence.dev/core-concepts/data-sources\#overview-of-data-sources)

Evidence extracts all data sources into a common storage format (called Parquet) to enable querying across multiple data sources using SQL.

- To query against your data sources, you first need to extract the data into Parquet, using `npm run sources`
- Supported sources including SQL databases, flat data files (CSV etc), and non-SQL data sources (e.g. APIs)

![Universal SQL Data Source Architecture](https://docs.evidence.dev/img/usql-architecture.png)

More information about the architecture design can be found in [this article](https://evidence.dev/blog/why-we-built-usql).

## [Connect your Data Sources](https://docs.evidence.dev/core-concepts/data-sources\#connect-your-data-sources)

To connect your local development environment to a database:

1. Run your evidence app with `npm run dev`
2. Navigate to [localhost:3000/settings](http://localhost:3000/settings)
3. Select your data source, name it, and enter required credentials
4. (If required) Open the `connections.yaml` file inside `/sources/[source_name]` and add any additional configuration options
5. (If required) Add [source queries](https://docs.evidence.dev/core-concepts/data-sources#configure-source-queries)
6. Rerun sources with `npm run sources`

Evidence will save your credentials locally, and run a test query to confirm that it can connect.

Connections to databases in production are managed via [environment variables](https://docs.evidence.dev/reference/cli#environment-variables)

Evidence supports:

- [BigQuery](https://docs.evidence.dev/core-concepts/data-sources/bigquery)
- [Snowflake](https://docs.evidence.dev/core-concepts/data-sources/snowflake)
- [Redshift](https://docs.evidence.dev/core-concepts/data-sources/redshift)
- [PostgreSQL](https://docs.evidence.dev/core-concepts/data-sources/postgres)
- [Timescale](https://docs.evidence.dev/core-concepts/data-sources/postgres)
- [Trino](https://docs.evidence.dev/core-concepts/data-sources/trino)
- [Microsoft SQL Server](https://docs.evidence.dev/core-concepts/data-sources/mssql)
- [MySQL](https://docs.evidence.dev/core-concepts/data-sources/mysql)
- [SQLite](https://docs.evidence.dev/core-concepts/data-sources/sqlite)
- [DuckDB](https://docs.evidence.dev/core-concepts/data-sources/duckdb)
- [MotherDuck](https://docs.evidence.dev/core-concepts/data-sources/motherduck)
- [Databricks](https://docs.evidence.dev/core-concepts/data-sources/databricks)
- [Cube](https://docs.evidence.dev/core-concepts/data-sources/postgres#cube)
- [Google Sheets](https://docs.evidence.dev/core-concepts/data-sources/google-sheets)
- [CSV](https://docs.evidence.dev/core-concepts/data-sources/csv)
- [JavaScript](https://docs.evidence.dev/core-concepts/data-sources/javascript)
- & More

## [Configure Source Queries](https://docs.evidence.dev/core-concepts/data-sources\#configure-source-queries)

For SQL data sources, choose which data to extract by adding .sql files to the `/sources/[source_name]/` folder.

**N.B: These queries use the data source's native SQL dialect.**

```text-sm code
.-- sources/
   `-- my_source/
      |-- connection.yaml
      `-- my_source_query.sql
```

Each of these .sql files will create a table that can be queried in Evidence as `[my_source].[my_source_query]`.

**Non-SQL data sources**

For non-SQL data sources, configuring the data extracted is achieved in other ways. Refer to the documentation for the specific data source for details.

## [Run Sources](https://docs.evidence.dev/core-concepts/data-sources\#run-sources)

You can extract data from configured sources in Evidence using `npm run sources`. Sources will also rerun automatically if you have the dev server running and you make changes to your source queries or source configuration.

### [Working with Large Sources](https://docs.evidence.dev/core-concepts/data-sources\#working-with-large-sources)

In dev mode, if you have large sources which take a while to run, it can be helpful to only run the sources which have changed. There are a few ways to accomplish this:

- If your dev server is running, any changes you make to source queries will only re-run the queries which have changed
- Run a modified sources command to specify the source you want to run:
  - `npm run sources -- --changed` run only the sources with changed queries
  - `npm run sources -- --sources my_source` run `my_source` only
  - `npm run sources -- --sources my_source --queries query_one,query_two` run `my_source.query_one` and `my_source.query_two` only

### [Increase Process Memory](https://docs.evidence.dev/core-concepts/data-sources\#increase-process-memory)

If you are working with large data sources (~1M+ rows), your `npm run sources` process may run out of memory, with an error similar to this:

```text-sm code
FATAL ERROR: Reached heap limit Allocation failed - JavaScript heap out of memory
```

One way to circumvent this is to increase the amount of memory allocated to the process. The below command increases the memory to 4GB (the number is measured in MB), but you can set it arbitrarily up to the RAM of your machine

#### [Mac OS / Linux](https://docs.evidence.dev/core-concepts/data-sources\#mac-os--linux)

```text-sm code
NODE_OPTIONS="--max-old-space-size=4096" npm run sources
```

#### [Windows](https://docs.evidence.dev/core-concepts/data-sources\#windows)

```text-sm code
set NODE_OPTIONS=--max-old-space-size=4096 && npm run sources
```

### [Build Time Variables](https://docs.evidence.dev/core-concepts/data-sources\#build-time-variables)

You can pass variables to your source queries at build time using environment variables of the format `EVIDENCE_VAR__variable_name=value`.

`.env`

```text-sm bash
EVIDENCE_VAR__client_id=123
```

Then in your **source queries**, you can access the variable using `${}` syntax:

```text-sm sql
select * from customers
where client_id = ${client_id}
```

This will interpolate the value of `client_id` into the query:

```text-sm sql
select * from customers
where client_id = 123
```

Note that these variables are only accessible in source queries, not in file queries or queries in markdown files.

## [New Data Sources](https://docs.evidence.dev/core-concepts/data-sources\#new-data-sources)

We're adding new connectors regularly. [Create a GitHub issue](https://github.com/evidence-dev/evidence/issues) or [send us a message in Slack](https://slack.evidence.dev/) if you'd like to use Evidence with a database that isn't currently supported.

The source code for Evidence's connectors is available [on GitHub](https://github.com/evidence-dev/evidence/tree/main/packages/datasources)

## [Troubleshooting](https://docs.evidence.dev/core-concepts/data-sources\#troubleshooting)

If you need help with connecting to your data, please feel free to [send us a message in Slack](https://slack.evidence.dev/).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/core-concepts/data-sources/index.md)