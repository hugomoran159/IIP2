[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [GitLab Pages](https://docs.evidence.dev/deployment/self-host/gitlab-pages)

# GitLab Pages

[GitLab Pages](https://docs.gitlab.com/ee/user/project/pages) is a service that allows you to host static websites and single-page apps. Evidence apps can be deployed to GitLab Pages by pushing your Evidence project to a GitLab repository and enabling Pages for the repository.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/gitlab-pages\#prerequisites)

- A [GitLab](https://gitlab.com/) account
- An Evidence project pushed to a GitLab repository

## [Deploy Evidence to GitLab Pages](https://docs.evidence.dev/deployment/self-host/gitlab-pages\#deploy-evidence-to-gitlab-pages)

1. In [GitLab](https://gitlab.com/), navigate to your Evidence project repository.
2. Add credentials as environment variables
   - Navigate to **Settings > CI/CD > Variables**
   - Click **Add Variable**, and use **Masked** visibility
   - Navigate to your Evidence project and go to the [settings page](http://localhost:3000/settings#deploy) and copy each of the environment variables keys and values
   - Alternatively, you can find credentials in `connection.options.yaml` files in your `/sources/your_source` directory. The key format used should be `EVIDENCE_SOURCE__[your_source]__[option_name]` (Note the casing matches your source names, and the double underscores). Note that the values are base64 encoded, and will need to be decoded.
3. Return to your GitLab project, and select **Deploy > Pages** in the left sidebar.
4. Get started with GitLab Pages
   - Build image: `node:22`
   - The application files are in the `public` folder: `true` (we'll change this in Evidence later)
   - Installation steps: `npm ci`
   - Build steps:
     - `npm run sources`
     - `npm run build`
     - `cp -r build public`
   - Add a commit message, and click **Commit**

Your app will be available at `https://[your-repo]-[hexcode].gitlab.io/`. It will be only accessible to your account by default.

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/self-host/gitlab-pages\#domains-authentication-and-scheduling)

**Evidence Cloud**

Deploying on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud) comes with:

- **User authentication** with email-password or SSO via Google Workspace, Microsoft Entra, Okta etc.
- **Your own Evidence subdomain**, https://\[my-subdomain\].evidence.app, or custom domain.
- **Scheduled builds** to refresh your data at specific intervals, e.g., daily, hourly.

### [Authentication](https://docs.evidence.dev/deployment/self-host/gitlab-pages\#authentication)

GitLab pages are only accessible to your account by default. To make it public, you can change the visibility at:

Settings > General > Visibility, project features and permissions > Pages

### [Custom domains](https://docs.evidence.dev/deployment/self-host/gitlab-pages\#custom-domains)

You can add a custom domain by navigating to:

Settings > Pages > Domains > New domain

### [Data refresh](https://docs.evidence.dev/deployment/self-host/gitlab-pages\#data-refresh)

You can add a pipeline schedule to refresh your data by navigating to:

Build > Pipeline schedule > Create a new pipeline schedule

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/gitlab-pages/index.md)