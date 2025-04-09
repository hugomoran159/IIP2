[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [Cloudflare Pages](https://docs.evidence.dev/deployment/self-host/cloudflare-pages)

# Cloudflare Pages

Cloudflare is a popular CDN and DNS provider that also offers a static site hosting service called [Cloudflare Pages](https://pages.cloudflare.com/). Cloudflare Pages can deploy Evidence apps from a Git repository.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/cloudflare-pages\#prerequisites)

- A Cloudflare account
- An Evidence project pushed to a Git service like GitHub or GitLab

## [Deploy Evidence to Cloudflare Pages](https://docs.evidence.dev/deployment/self-host/cloudflare-pages\#deploy-evidence-to-cloudflare-pages)

1. Navigate to the [Cloudflare dashboard](https://dash.cloudflare.com/)
2. Select **Workers & Pages** from the left-hand menu, and select **Create**
3. There are two tabs: **Workers** and **Pages** \- choose **Pages**
4. Select **Connect to Git**, and choose GitHub or GitLab
5. Select Repository
   - Authenticate with your Git provider
   - Choose the repository to deploy from
   - You may need to configure repository access permissions
6. Set up builds and deployments
   - Choose a production branch
   - Set the build command: `npm run sources && npm run build`
   - Set the build output directory: `/build`
7. (Optionally select the root path containing your Evidence project if using a monorepo)
8. Add environment variables
   - Click **Add variable**
   - With your Evidence dev server running, go to the [settings page](http://localhost:3000/settings#deploy) and copy each of the environment variables
   - Paste them into the Cloudflare Pages environment variables section
9. Click **Save and Deploy**

Your app will be deployed to a URL like `https://[repo-name].pages.dev`. It can take a few minutes for the site to be available after deployment.

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/self-host/cloudflare-pages\#domains-authentication-and-scheduling)

**Evidence Cloud**

Deploying on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud) comes with:

- **User authentication** with email-password or SSO via Google Workspace, Microsoft Entra, Okta etc.
- **Your own Evidence subdomain**, https://\[my-subdomain\].evidence.app, or custom domain.
- **Scheduled builds** to refresh your data at specific intervals, e.g., daily, hourly.

### [Authentication](https://docs.evidence.dev/deployment/self-host/cloudflare-pages\#authentication)

By default, your app will be public.

Authentication can be configured with [Cloudflare Access](https://developers.cloudflare.com/cloudflare-one/identity/access).

Workers & Pages > \[Your app\] > Settings > General > Access Policy > Manage

You will need to set up access groups and policies to control access to your app. A one time PIN code can be configured for user login.

## [Custom Domains](https://docs.evidence.dev/deployment/self-host/cloudflare-pages\#custom-domains)

Cloudflare Pages supports custom domains.

Workers & Pages > \[Your app\] > Custom Domains > Set up a custom domain

## [Data refresh](https://docs.evidence.dev/deployment/self-host/cloudflare-pages\#data-refresh)

Cloudflare Pages does not have built in functionality for data refresh.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/cloudflare-pages/index.md)