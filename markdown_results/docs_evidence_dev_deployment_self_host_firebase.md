[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [Firebase](https://docs.evidence.dev/deployment/self-host/firebase)

# Firebase

[Firebase Hosting](https://firebase.google.com/products/hosting) is a GCP service that allows you to host static websites and single-page apps. Firebase Hosting can deploy Evidence apps by linking to a Git repository.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/firebase\#prerequisites)

- A GCP account
- An Evidence project pushed to Git service like GitHub, GitLab, or Bitbucket.

## [Deploy Evidence to Firebase](https://docs.evidence.dev/deployment/self-host/firebase\#deploy-evidence-to-firebase)

**Firebase CLI**

The Firebase CLI is somewhat buggy, so you sometimes need to try the commands multiple times for them to succeed.

01. From the [Firebase console](https://console.firebase.google.com/), click **Create a project**.
    - Enter a project name, accept the terms of service, and click **Continue**.
    - Choose whether to enable Google Analytics (not required), and click **Create project**.
02. In the terminal, install the Firebase CLI:


    ```text-sm bash
    npm install -g firebase-tools
    ```

03. Log in to Firebase, and authenticate via the browser:


    ```text-sm bash
    firebase login
    ```

04. Initialize Firebase Hosting in your project:


    ```text-sm bash
    firebase init hosting
    ```



    - Select `Use an existing project`
    - Select a default Firebase project for this directory: Select project you created
    - What do you want to use as your public directory? `build`
    - Configure as a single-page app (rewrite all URLs to /index.html)? `No`
    - (If asked) File build/index.html already exists. Overwrite? `No`
    - Set up automatic builds and deploys with GitHub? `Yes`
    - Select a GitHub repository to connect to this project: Type your repo name
    - Set up the workflow to run a build script before every deploy? `Yes`
    - What script should be run before every deploy? `npm ci && npm run sources && npm run build`
    - Set up automatic deployment to your site's live channel when a PR is merged? `Yes`
    - What is the name of the GitHub branch associated with your site's live channel? `main`
05. Add secrets to your GitHub repo: Settings > Secrets and variables > Actions
    - With your Evidence dev server running, go to the [settings page](http://localhost:3000/settings#deploy) and copy each of the environment variables
    - Alternatively, you can find credentials in `connection.options.yaml` files in your `/sources/your_source` directory. The key format used should be `EVIDENCE_SOURCE__[your_source]__[option_name]` (Note the casing matches your source names, and the double underscores). Note that the values are base64 encoded, and will need to be decoded.
    - Add each of them as secrets to your GitHub repo
06. Build your app locally (if you haven't already):


    ```text-sm bash
    npm i && npm run sources && npm run build
    ```

07. Deploy your app for the first time


    ```text-sm bash
    firebase deploy --only hosting
    ```

08. Edit `firebase-hosting-merge.yml` and `firebase-hosting-pull-request.yml` to add your environment variables as GitHub secrets (note that GitHub capitalizes the names of secrets)


    ```text-sm yaml
- run: npm ci && npm run sources && npm run build
env:
    EVIDENCE_SOURCE__my_source__username: ${{ secrets.EVIDENCE_SOURCE__MY_SOURCE__USERNAME }}
    EVIDENCE_SOURCE__my_source__private_key: ${{ secrets.EVIDENCE_SOURCE__MY_SOURCE__PRIVATE_KEY }}
```

09. Commit and push these newly created files: `firebase.json`, `.firebaserc`, `firebase-hosting-merge.yml`, `firebase-hosting-pull-request.yml`.
10. Update your GitHub workflow settings to allow Workflows to Read and write permissions. This is required for the Pull Request preview GitHub Action to work. \[your repo\] > Settings > Actions > General > Workflow permissions

Your app should now be live on Firebase Hosting at `https://<project-id>.web.app`.

## [Domains, Authentication and Scheduling](https://docs.evidence.dev/deployment/self-host/firebase\#domains-authentication-and-scheduling)

**Evidence Cloud**

Deploying on [Evidence Cloud](https://docs.evidence.dev/deployment/cloud/evidence-cloud) comes with:

- **User authentication** with email-password or SSO via Google Workspace, Microsoft Entra, Okta etc.
- **Your own Evidence subdomain**, https://\[my-subdomain\].evidence.app, or custom domain.
- **Scheduled builds** to refresh your data at specific intervals, e.g., daily, hourly.

### [Authentication](https://docs.evidence.dev/deployment/self-host/firebase\#authentication)

Firebase Authentication is _not_ a suitable authentication for static apps on Firebase Hosting.

### [Custom domains](https://docs.evidence.dev/deployment/self-host/firebase\#custom-domains)

You can set up a custom domain on Firebase Hosting.

[Firebase dashboard](https://console.firebase.google.com/u/0/) \> \[your project\] > Hosting (in the left sidebar) > Domains > Add custom domain

### [Data refresh](https://docs.evidence.dev/deployment/self-host/firebase\#data-refresh)

To adjust your deployment schedule, modify the workflow file in your repository, adding a `schedule` trigger.

```text-sm yaml
on:
schedule:
    - cron: '0 0 * * *' # This is midnight every day
```

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/firebase/index.md)