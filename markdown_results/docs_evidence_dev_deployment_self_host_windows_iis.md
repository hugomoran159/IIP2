[Home](https://docs.evidence.dev/) [Deployment](https://docs.evidence.dev/deployment) [Self Host](https://docs.evidence.dev/deployment/self-host) [Windows IIS](https://docs.evidence.dev/deployment/self-host/windows-iis)

# Windows IIS

Windows IIS server is a part of any Windows Server operating system and is also available in the Windows Desktop business versions. This makes IIS a readily available static site server.

## [Prerequisites](https://docs.evidence.dev/deployment/self-host/windows-iis\#prerequisites)

- A Windows desktop or server operating system with the Internet Information Services feature enabled. The following sub-features are required:
  - Web Management Tools > IIS Management Console
  - World Wide Web Services > Common HTTP Features:
    - Default Document
    - Static Content
  - Performance Features > Static Content Compression
- A built Evidence project to copy to the IIS server

## [Deploy Evidence to IIS](https://docs.evidence.dev/deployment/self-host/windows-iis\#deploy-evidence-to-iis)

1. Open the IIS Manager
2. Add a new website
3. Copy the files from the Evidence build folder to the Physical Path of the new website
4. Check permissions
   - Make sure the permissions are set correctly on the Physical Path folder
   - Make sure the Application Pool is running under a user that has access to the Physical Path folder

## [Setting MIME-Types](https://docs.evidence.dev/deployment/self-host/windows-iis\#setting-mime-types)

Evidence uses .arrow files to load data into the static site. IIS does not know these file-types so we need to make it aware of them.

1. Click on your website
2. In the main window click on "MIME Types"
3. In the Action pane on the right click "Add" and add the following "MIME types"
   - Extension: .arrow
     - MIME Type: application/vnd.apache.arrow.file
   - Extension: .arrows (note the ' _s_' at the end)
     - MIME Type: application/vnd.apache.arrow.stream

## [Start IIS](https://docs.evidence.dev/deployment/self-host/windows-iis\#start-iis)

You should now be able to start IIS and browse to your website. You can update your site by copying the new build files to your website's Physical Path.

[Edit page on GitHub](https://github.com/evidence-dev/evidence/edit/next/sites/docs/pages/deployment/self-host/windows-iis/index.md)