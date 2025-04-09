[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Cloud](https://docs.evidence.dev/deployment/cloud) [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud)

# Evidence Cloud

Evidence Cloud is the easiest way to host Evidence apps. It's maintained by the Evidence team, and allows you to securely host Evidence apps without having to worry about maintaining your own infrastructure.

- **Easy to set up:** Deploy in 5 minutes without configuring any infrastructure.
- **Secure:** Manage access for users in your team.
- **Organizational domain:** Host your app at `[organisation].evidence.app`.
- **Scheduled refreshes:** Daily (or more frequent) data updates to your app.
- **Re-build on push:** Merge to your target branch to rebuild your app.
- **Custom domains:** Add a custom domain to your app.
- **Cloud execution engine:** Offload heavy queries to our Cloud SQL engine for faster performance.

## [Prerequisites](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#prerequisites)

- A GitHub account
- An Evidence project pushed to GitHub (optional)

## [Deploy Evidence to Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#deploy-evidence-to-evidence-cloud)

1. Go to [Evidence Cloud](https://evidence.app/) and login with GitHub
2. Choose an option to get started:
1. **If you have an existing Evidence project:** click `Add Project`
2. **If you don't have a Evidence project yet:** select `Start from our templates`, and choose evidence-dev/template.
3. Deploy your project
   - Repository: Choose the GitHub repository containing your Evidence project
   - Branch: Edit if required
   - Domain: Choose the subdomain you want to deploy to
   - (Optional) Root directory: Edit to point to your Evidence directory if you are using a monorepo
   - Authentication: None, Email and Password (Paid plans only), or SSO (Paid plans only)
4. Set your environment variables
   - **If you are deploying an existing project**, click "Paste Environment Variables"
     - Navigate to the [settings page](http://localhost:3000/settings#deploy) and use the **Copy All** button to copy them to your clipboard, then paste them into the Environment Variables section. Click **Save**.
     - Alternatively, you can find credentials in `connection.options.yaml` files in your `/sources/your_source` directory, and enter them in KEY=VALUE format on separate lines.
     - The key format used should be `EVIDENCE_SOURCE__[your_source]__[option_name]` (Note the casing matches your source names, and the double underscores). Note that the values are base64 encoded, and will need to be decoded.
   - **If you are deploying from a template**, click "Use Template Environment Variables"
5. Click `Deploy your project`

Your app will be deployed to https://\[your-subdomain\].evidence.app

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#domains-authentication-and-scheduling)

### [Authentication](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#authentication)

Evidence Cloud Team and Enterprise plans support private apps with auth. If you need to configure an SSO provider, reach out to our team on [Slack](https://slack.evidence.dev/).

### [Custom Domains](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#custom-domains)

Evidence Cloud Enterprise plans support custom domains. Reach out to our team on [Slack](https://slack.evidence.dev/) to set your domain up.

### [Data Refresh](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#data-refresh)

To adjust your deployment schedule, select your app in [Evidence Cloud](https://evidence.app/), click **Schedule**, and adjust the schedule.

Community Plan sites can be refreshed daily. More frequent refreshes are available on the Team and Enterprise plans.

## [Frequently Asked Questions](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#frequently-asked-questions)

### [Features](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#features)

What causes my data to update?

How frequently does Evidence Cloud refresh my data?

How does authentication work for my private app?

Can I create a public Evidence Cloud site?

How do I set up development previews?

### [Pricing](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#pricing)

Is Evidence Cloud free?

How do I get onto a Team or Enterprise plan?

### [Account Management](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#account-management)

How do I add a new developer to my Evidence app?

Which git providers can I use with Evidence Cloud?

### [Troubleshooting](https://docs.evidence.dev/deployment/cloud/evidence-cloud\#troubleshooting)

I've successfully deployed the template app. How do I edit it?

How long do builds take?

When can I expect build failures?

How can I prevent queries or components with errors from making it to my site?

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/cloud/evidence-cloud/index.md)