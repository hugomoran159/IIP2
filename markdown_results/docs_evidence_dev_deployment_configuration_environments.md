[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Configuration](https://docs.evidence.dev/deployment/configuration) [Environments](https://docs.evidence.dev/deployment/configuration/environments)

# Environments

## [What are environments?](https://docs.evidence.dev/deployment/configuration/environments\#what-are-environments)

In software engineering, _environments_ are used to develop and test code without impacting end users.

> “Production” (prod) refers to the environment that end users interact with, while “development” (dev) is the environment engineers write code in. This allows engineers to work iteratively when writing and testing new code in development, and once they are confident in these changes, deploy their code to production.

Data warehouses often also use separate environments – the _production_ environment refers to the data end users can access.

## [Typical data environment configurations](https://docs.evidence.dev/deployment/configuration/environments\#typical-data-environment-configurations)

There are three typical ways that data teams separate their data environments:

1. **Separate databases** _(Bigquery - projects)_: Each environment has its own database, but with the same schemas and tables in each database. This is the most common way to separate environments.
2. **Separate schemas** _(Bigquery - datasets)_: Each environment has its own schema, with schemas hosted on the same database.
3. **Separate accounts** _(Bigquery - clusters/instances/organizations)_: Each environment has its own account. This is less common.

## [Setting up Evidence to use different environments](https://docs.evidence.dev/deployment/configuration/environments\#setting-up-evidence-to-use-different-environments)

You can configure both your dev and prod environments using [environment variables](https://docs.evidence.dev/reference/cli#environment-variables). Using `.env` files at the project root is supported.

### [Dev environment](https://docs.evidence.dev/deployment/configuration/environments\#dev-environment)

Add your dev database credentials for your dev environment via the **settings page**. If you are running Evidence locally, typically at [http://localhost:3000/settings](http://localhost:3000/settings).

### [Prod environment](https://docs.evidence.dev/deployment/configuration/environments\#prod-environment)

Add your prod database credentials as environment variables. The specific instructions depend on how you are deploying Evidence. Instructions can be be found in the deployment section of the settings page of your app running locally.

If you are using separate schemas, you will need to add the optional `schema` parameter to your credentials in dev, and an environment variable in prod. This is only currently supported for Postgres.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/configuration/environments/index.md)