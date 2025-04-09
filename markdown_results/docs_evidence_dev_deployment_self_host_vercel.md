[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [Vercel](https://docs.evidence.dev/deployment/self-host/vercel)

# Vercel

[Vercel](https://vercel.com/) is a cloud platform that allows you to simply deploy web applications. Vercel can deploy Evidence apps from a Git repository.

Vercel lets you host a public version of your app for free, or you can create and host a password-protected version with Vercel's $150/month pro plan.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/vercel\#prerequisites)

- An Evidence project pushed to a Git service like GitHub, GitLab, or Bitbucket.
- A Vercel account.

## [Deploy Evidence to Vercel](https://docs.evidence.dev/deployment/self-host/vercel\#deploy-evidence-to-vercel)

1. From the [Vercel dashboard](https://vercel.com/dashboard), select **Add new… Project**
2. Import the Git repository containing your Evidence project.
3. Edit the build and output settings:
   - **Build command**: `npm run sources && npm run build`
   - **Output directory**: `build`
4. (If using a monorepo) edit the root directory to point to your Evidence project
5. Edit the environment variables:
   - With your Evidence dev server running, use the **Copy All** button on the [settings page](http://localhost:3000/settings#deploy)
   - Paste them into the Vercel environment variables section, (they will automatically populate all the fields)
   - Alternatively, you can find credentials in `connection.options.yaml` files in your `/sources/your_source` directory. The key format used should be `EVIDENCE_SOURCE__[your_source]__[option_name]` (Note the casing matches your source names, and the double underscores). Note that the values are base64 encoded, and will need to be decoded.
6. Click **Deploy**

Your app will be deployed to https://\[project-name\].vercel.app

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/self-host/vercel\#domains-authentication-and-scheduling)

**Evidence Cloud**

Deploying on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud) comes with:

- **User authentication** with email-password or SSO via Google Workspace, Microsoft Entra, Okta etc.
- **Your own Evidence subdomain**, https://\[my-subdomain\].evidence.app, or custom domain.
- **Scheduled builds** to refresh your data at specific intervals, e.g., daily, hourly.

### [Authentication](https://docs.evidence.dev/deployment/self-host/vercel\#authentication)

Your deployed app will be public by default.

#### [Global password](https://docs.evidence.dev/deployment/self-host/vercel\#global-password)

This requires a Vercel paid plan with [advanced deployment protection](https://vercel.com/docs/security/deployment-protection#advanced-deployment-protection), starting at $150/month.

Vercel Dashboard > \[your-project\] > Settings > Deployment Protection > Password protection

### [Custom domains](https://docs.evidence.dev/deployment/self-host/vercel\#custom-domains)

Your app will be deployed to https://\[project-name\].vercel.app

You can set a custom domain using Vercel from the console:

Vercel Dashboard > \[your-project\] > Settings > Domains

### [Data refresh](https://docs.evidence.dev/deployment/self-host/vercel\#data-refresh)

Your project will be automatically built when you push to your repository, refreshing your data.

#### [Schedule updates using Deploy Hooks](https://docs.evidence.dev/deployment/self-host/vercel\#schedule-updates-using-deploy-hooks)

If you want your site to update on a specific schedule, you can use GitHub Actions (or another similar service) to schedule regular calls to a [Vercel deploy hook](https://vercel.com/docs/concepts/git/deploy-hooks).

1. Create a [Vercel deploy hook](https://vercel.com/docs/concepts/git/deploy-hooks).
This will give you a URL that GitHub will use to trigger builds
2. Add `VERCEL_DEPLOY_HOOK` to your Github Repo's Secrets
   - In your GitHub repo, go to Settings > Secrets > Actions and click **New repository secret** and create a secret, `VERCEL_DEPLOY_HOOK`, with the URL from step 1.
3. Add a schedule file to your project
   - Create a new directory in your project called `.github`
   - Within that directory, create another called `workflows`
   - Add a new file in `.github/workflows` called `main.yml`
4. Add the following text to the `main.yml` file you just created. Be sure that the indentation in your `main.yml` matches the below.

```text-sm yaml
name: Schedule Vercel Deploy
on:
  workflow_dispatch:
  schedule:
    - cron: '0 10 * * *' # Once a day around 6am ET (10am UTC)
jobs:
  build:
    name: Request Vercel Webhook
    runs-on: ubuntu-latest
    steps:
      - name: POST to Deploy Hook
        env:
          BUILD_HOOK: ${{ secrets.VERCEL_DEPLOY_HOOK }}
        run: curl -X POST -d {} $BUILD_HOOK
```

5. See your GitHub Actions run in the **Actions** tab of your GitHub repo

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/vercel/index.md)