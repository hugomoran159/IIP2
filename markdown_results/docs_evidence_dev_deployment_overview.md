[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Overview](https://docs.evidence.dev/deployment/overview)

# [Deployment Overview](https://docs.evidence.dev/deployment/overview\#deployment-overview)

In production, Evidence generates [static sites](https://www.netlify.com/blog/2020/04/14/what-is-a-static-site-generator-and-3-ways-to-find-the-best-one) by default. This means it doesn't run queries against your database when someone visits your site, but queries and pre-builds all pages as HTML beforehand.

Static sites are very versatile, and so you can host your Evidence app using Evidence Cloud, cloud services like AWS, Azure, Netlify or Vercel, or your own infrastructure.

You can also configure Evidence as a [Single Page App (SPA)](https://docs.evidence.dev/deployment/configuration/rendering-modes). In SPA mode Evidence will not pre-build all the pages in your application. This can be preferrable if your app has many pages (>1,000) causing long build times.

## [Evidence Cloud](https://docs.evidence.dev/deployment/overview\#evidence-cloud)

The easiest way to deploy Evidence is on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud). Evidence Cloud is free for public apps, and has paid plans for private apps.

## [Self-host](https://docs.evidence.dev/deployment/overview\#self-host)

You can also self-host Evidence anywhere suitable for hosting static sites. See guides for:

- [AWS Amplify](https://docs.evidence.dev/deployment/self-host/aws-amplify)
- [Azure Static Apps](https://docs.evidence.dev/deployment/self-host/azure-static-apps)
- [Cloudflare Pages](https://docs.evidence.dev/deployment/self-host/cloudflare-pages)
- [Firebase](https://docs.evidence.dev/deployment/self-host/firebase)
- [GitHub Pages](https://docs.evidence.dev/deployment/self-host/github-pages)
- [GitLab Pages](https://docs.evidence.dev/deployment/self-host/gitlab-pages)
- [Hugging Face Spaces](https://docs.evidence.dev/deployment/self-host/hugging-face-spaces)
- [Netlify](https://docs.evidence.dev/deployment/self-host/netlify)
- [Vercel](https://docs.evidence.dev/deployment/self-host/vercel)
- [Windows IIS](https://docs.evidence.dev/deployment/self-host/windows-iis)

## [Build Process](https://docs.evidence.dev/deployment/overview\#build-process)

Evidence doesn't run new queries each time someone visits one of your reports.

Instead, Evidence runs your queries once, at build time, and statically generates _all_ of the pages in your app. This includes all possible permutations of any paramaterized pages.

You can schedule (or trigger) regular builds of your site to keep it up-to-date with your data warehouse.

This has two benefits for you and your users:

1. If something goes wrong with your SQL, Evidence just stops building your app, and continues to serve older results.
2. Your site will be exceptionally fast. Under most conditions, pages will load in milliseconds.

## [Build Commands](https://docs.evidence.dev/deployment/overview\#build-commands)

Ensure that your build environment aligns with the [system requirements](https://docs.evidence.dev/guides/system-requirements)

### [Build](https://docs.evidence.dev/deployment/overview\#build)

The command `npm run build` will build a static version of your reports and place them in the `build` directory.

### [Build:Strict](https://docs.evidence.dev/deployment/overview\#buildstrict)

The command `npm run build:strict` is a much less permissive build command. Use this to ensure you never deploy a broken report.
This command will fail if:

- **Any SQL query fails.** A successful query returning no rows is _not_ a failure
- **Any component renders an error state.** A component passed a valid query returning no rows _will_ fail - you can avoid this with an [`{#if}` statement](https://docs.evidence.dev/core-concepts/if-else) if needed.

## [Storing Credentials](https://docs.evidence.dev/deployment/overview\#storing-credentials)

In production, Evidence expects to find your database credentials in **environment variables**.

To find the environment variables that you'll need to set for your app:

1. Run your app in development mode
2. Visit the [settings page](http://localhost:3000/settings)
3. Open the deployment panel, and select your deployment target

For details on how to use different data for different environments, see [Environments](https://docs.evidence.dev/deployment/configuration/environments).

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/overview/index.md)