[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [Netlify](https://docs.evidence.dev/deployment/self-host/netlify)

# Netlify

[Netlify](https://www.netlify.com/) is a cloud platform for building and deploying web apps and frontend sites. Netlify can deploy Evidence apps from a Git repository.

**Netlify URL Lowercasing**

All URLs on Netlify are converted to lowercase. This can cause issues if you're using `{params.my_param}` to filter data in your markdown. It's recommended to use lowercase any time you're using a URL parameter to filter data, like this:

```text-sm sql
SELECT * FROM source_name.my_table
WHERE LOWER(my_column) = LOWER('${params.my_param}')
```

Netlify lets you host a public version of your app for free, or you can create and host a password-protected version with Netlify's $15/month plan.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/netlify\#prerequisites)

- An Evidence project pushed to a Git service like GitHub, GitLab, or Bitbucket.
- A Netlify account.

## [Deploy Evidence to Netlify](https://docs.evidence.dev/deployment/self-host/netlify\#deploy-evidence-to-netlify)

1. From the [Netlify dashboard](https://app.netlify.com/), select **Add new site > Import an existing project**
2. Choose your Git provider (GitHub, GitLab, Bitbucket, Azure DevOps)
3. Select the repository containing your Evidence project
4. In the build settings
   - **Build command**: `npm run sources && npm run build`
   - **Publish directory**: `build`
5. In the environment variables
   - Click **New variable**
   - With your Evidence dev server running, go to the [settings page](http://localhost:3000/settings#deploy) and copy each of the environment variables
   - Alternatively, you can find credentials in `connection.options.yaml` files in your `/sources/your_source` directory. The key format used should be `EVIDENCE_SOURCE__[your_source]__[option_name]` (Note the casing matches your source names, and the double underscores). Note that the values are base64 encoded, and will need to be decoded.
   - Paste them into the Netlify environment variables section
6. (If using a monorepo) edit the base directory to point to your Evidence project
7. Click **Deploy \[your-site-name\]**

Your app will be available at `https://[your-site-name].netlify.app`.

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/self-host/netlify\#domains-authentication-and-scheduling)

**Evidence Cloud**

Deploying on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud) comes with:

- **User authentication** with email-password or SSO via Google Workspace, Microsoft Entra, Okta etc.
- **Your own Evidence subdomain**, https://\[my-subdomain\].evidence.app, or custom domain.
- **Scheduled builds** to refresh your data at specific intervals, e.g., daily, hourly.

### [Authentication](https://docs.evidence.dev/deployment/self-host/netlify\#authentication)

#### [Global password](https://docs.evidence.dev/deployment/self-host/netlify\#global-password)

Setting a global password requires a Netlify paid plan ($15/month).

Follow the directions provided by Netlify to set up a password for your site:

Netlify Dashboard >> \[your-site\] >> Site configuration >> Access & security >> Visitor access >> Configure site protection >> Basic password protection

#### [OAuth](https://docs.evidence.dev/deployment/self-host/netlify\#oauth)

Netlify only supports OAuth via GitHub, GitLab, and Bitbucket.

Netlify Dashboard >> \[your-site\] >> Site configuration >> Access & security >> OAuth

### [Custom domains](https://docs.evidence.dev/deployment/self-host/netlify\#custom-domains)

Your app will be deployed to https://\[your-site-name\].netlify.app

You can set a custom domain using Netlify from the console:

Netlify Dashboard >> \[your-site\] >> Domain management >> Add a domain

### [Data refresh](https://docs.evidence.dev/deployment/self-host/netlify\#data-refresh)

#### [Schedule updates using Build Hooks](https://docs.evidence.dev/deployment/self-host/netlify\#schedule-updates-using-build-hooks)

If you want your site to update on a regular schedule, you can use GitHub Actions (or another similar service) to schedule regular calls to a [Netlify build hook](https://docs.netlify.com/configure-builds/build-hooks).

1. Create a [Netlify build hook](https://docs.netlify.com/configure-builds/build-hooks) in **Site configuration > Build & deploy > Continuous deployment > Build hooks**![netlify-add-build-hook](https://docs.evidence.dev/img/netlify-add-build-hook.png)
This will give you a URL that GitHub will use to trigger builds
2. Add `NETLIFY_BUILD_HOOK` to your Github Repo's Secrets
   - In your GitHub repo, go to Settings > Secrets > Actions and click **New repository secret**



     ![netlify-github-new-secret](https://docs.evidence.dev/img/netlify-github-new-secret.png)
   - Add the build hook URL as the secret value
     ![netlify-github-secret](https://docs.evidence.dev/img/netlify-github-secret.png)
3. Add a schedule file to your project
   - Create a new directory in your project called `.github`
   - Within that directory, create another called `workflows`
   - Add a new file in `.github/workflows` called `main.yml`
4. Add the following text to the `main.yml` file you just created. Be sure that the spacing and indentation is exactly as presented here, as it will impact whether the action runs correctly


```text-sm yaml
name: Schedule Netlify Build
on:
     workflow_dispatch:
     schedule:
    - cron: '0 10 * * *' # Once a day around 6am ET (10am UTC)
jobs:
build:
    name: Request Netlify Webhook
    runs-on: ubuntu-latest
    steps:
      - name: POST to Build Hook
        env:
          BUILD_HOOK: ${{ secrets.NETLIFY_BUILD_HOOK }}
        run: curl -X POST -d {} $BUILD_HOOK
```

5. See your GitHub Actions run in the **Actions** tab of your GitHub repo

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/netlify/index.md)