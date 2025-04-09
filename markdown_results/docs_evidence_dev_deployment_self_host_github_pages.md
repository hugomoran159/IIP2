[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [GitHub Pages](https://docs.evidence.dev/deployment/self-host/github-pages)

# GitHub Pages

GitHub Pages is a static site hosting service that publishes a website from HTML, CSS, and JavaScript files from a repository on GitHub. It optionally runs a build process to create these files. GitHub Pages can deploy Evidence apps from a GitHub repository.

**Base Path**

GitHub Pages serves sites at subpaths of github.io by default, e.g. `https://[username].github.io/your-app`, so you will need to adjust the [base path](https://docs.evidence.dev/deployment/configuration/base-paths) AND the [build directory](https://docs.evidence.dev/deployment/configuration/base-paths#configuring-the-build-directory-in-packagejson) for your app, unless using a custom domain.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/github-pages\#prerequisites)

- A GitHub account
- An Evidence project pushed to GitHub

## [Deploy Evidence to GitHub Pages](https://docs.evidence.dev/deployment/self-host/github-pages\#deploy-evidence-to-github-pages)

1. Adjust the [base path](https://docs.evidence.dev/deployment/configuration/base-paths) for your app to match the name of your GitHub repository.


   - If your repo is stored at `https://github.com/username/my-evidence-app`, your base path should be `/my-evidence-app`.

```text-sm yaml
# evidence.config.yaml
deployment:
  basePath: /my-evidence-app
```

```text-sm json
// package.json
"scripts": {
  "build": "EVIDENCE_BUILD_DIR=./build/my-evidence-app evidence build",
}
```

2. Add secrets to your GitHub repo: Settings > Secrets and variables > Actions

   - With your Evidence dev server running, go to the [settings page](http://localhost:3000/settings#deploy) and copy each of the environment variables
   - Alternatively, you can find credentials in `connection.options.yaml` files in your `/sources/your_source` directory. The key format used should be `EVIDENCE_SOURCE__[your_source]__[option_name]` (Note the casing matches your source names, and the double underscores). Note that the values are base64 encoded, and will need to be decoded.
3. From your GitHub repository, click the **Settings** tab, and then click **Pages** in the Code and automation section.

4. Under **Source**, select **GitHub Actions**

5. Directly underneath, where it says "Use a suggested workflow, browse all workflows or create your own", click **Create your own**, and use the following workflow file, naming it `deploy.yml` or similar.



```text-sm yaml
name: Deploy to GitHub Pages

on:
     push:
       branches: 'main' # or whichever branch you want to deploy from

jobs:
     build:
       runs-on: ubuntu-latest
       steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Install Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm

      - name: Install dependencies
        run: npm install

      - name: build
        env:
          BASE_PATH: '/${{ github.event.repository.name }}'
          ## Add and uncomment any environment variables here
          ## EVIDENCE_SOURCE__my_source__username: ${{ secrets.EVIDENCE_SOURCE__MY_SOURCE__USERNAME }}
          ## EVIDENCE_SOURCE__my_source__private_key: ${{ secrets.EVIDENCE_SOURCE__MY_SOURCE__PRIVATE_KEY }}
        run: |
          npm run sources
          npm run build

      - name: Upload Artifacts
        uses: actions/upload-pages-artifact@v3
        with:
          path: 'build/${{ github.event.repository.name }}'

deploy:
    needs: build
    runs-on: ubuntu-latest

    permissions:
      pages: write
      id-token: write

    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}

    steps:
      - name: Deploy
        id: deployment
        uses: actions/deploy-pages@v4
```

6. Click **Commit changes**, either directly to your branch, or create a PR and merge it to your specified branch.

7. The deploy workflow will run, you can see the progress in the **Actions** tab.


Your app should be available at `https://[username].github.io/[your-app]`.

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/self-host/github-pages\#domains-authentication-and-scheduling)

**Evidence Cloud**

Deploying on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud) comes with:

- **User authentication** with email-password or SSO via Google Workspace, Microsoft Entra, Okta etc.
- **Your own Evidence subdomain**, https://\[my-subdomain\].evidence.app, or custom domain.
- **Scheduled builds** to refresh your data at specific intervals, e.g., daily, hourly.

### [Authentication](https://docs.evidence.dev/deployment/self-host/github-pages\#authentication)

You can set up a private GitHub Pages site by setting the visibility of the repo to **Private**. This requires a GitHub Enterprise account.

This will mean only GitHub users with access to the repo will be able to access the site.

### [Custom domains](https://docs.evidence.dev/deployment/self-host/github-pages\#custom-domains)

You can add a custom domain to your GitHub Pages site. If you do this, you _do not_ need to adjust the base path for your app, as it does not need to be served from a subpath.

You can adjust the domain at:

\[your repo\] > Settings Tab > Pages > Custom domain

### [Data refresh](https://docs.evidence.dev/deployment/self-host/github-pages\#data-refresh)

You can adjust the schedule for your deployment using the workflow file by adding a `schedule` trigger with a cron expression.

```text-sm yaml
on:
push:
    branches: 'main'
schedule:
    # This is every 10 minutes
    - cron: '*/10 * * * *'
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/github-pages/index.md)