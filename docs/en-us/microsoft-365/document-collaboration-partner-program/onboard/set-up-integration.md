<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-integration -->
<!-- Sitemap-Last-Modified: 2025-04-30 -->

# Integrate with the Microsoft 365 Document Collaboration Partner Program

The Microsoft 365 Document Collaboration Partner Program \(MDCPP\) enables your users to view and edit Excel, PowerPoint, and Word documents directly in your collaboration application. Use the following guidance to configure your Azure app and install the MDCPP SDK.

## Configure your Azure app

Ensure that your Azure application has at least the following permissions, set to Delegated.

| Microsoft service | Permission | Description | MDCPP scenario |
| --- | --- | --- | --- |
| SharePoint | AllSites.Read | Read items in all site collections. | Required for the Present, Collaborate, and Join experiences. |
| SharePoint | AllSites.Write | Read and write items in all site collections. | Required for the Office for the Web experience, or if supporting all experiences. |
| SharePoint | MyFiles.Read | Read user files. | Required for the Present, Collaborate, and Join experiences. |
| SharePoint | MyFiles.Write | Read and write user files. | Required for the Office for the Web experience, or if supporting all experiences. |
| Office | MDCPP.All | Access start pages for Excel, PowerPoint, and Word. | Required for the Start Page experience. |

## Install the SDK

To embed Microsoft 365 document collaboration experiences into your application, you'll need to download and install the MDCPP npm package [@microsoft/document-collaboration-sdk](https://aka.ms/MDCPP-npm-package).

To install the SDK, run the following command in your command line prompt.

```console
npm install @microsoft/document-collaboration-sdk --save
```

## Recommendations

To enable the user to choose a OneDrive for Business or SharePoint file, you can leverage the OneDrive File Picker. For more information, see the [OneDrive File Picker documentation](https://learn.microsoft.com/en-us/onedrive/developer/controls/file-pickers/?view=odsp-graph-online&preserve-view=true).

If you use this option, you'll get a post message when the user chooses a file. This callback will include some file properties. You can extract the following properties for use in the MDCPP APIs.

- `item.sharepointIds.siteUrl`: This is the siteUrl field in the documentInfo input.
- `item.listItemUniqueId`: This should be used in the sourceDoc field in the documentInfo input.

```javascript
const command = message.data.data;

switch (command.command) {
  case "pick":
    const ids = command.items[0].sharepointIds;
    const spoUrl = ids.siteUrl;
    const sourceDoc = ids.listItemUniqueId;
    ...
}
```
