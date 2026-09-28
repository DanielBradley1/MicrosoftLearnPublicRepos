<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/ui-guidelines -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# CSPP UI Guidelines

Important

These CSPP UI Guidelines are not exhaustive. Hosts are expected to follow the terms of the [Microsoft Cloud Storage Partner Program Integration Terms](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/legal/cspp-terms) \(the “Terms”\) with respect to Microsoft 365 for the web integration. These UI Guidelines constitute required Branding Guidelines under the Terms. Microsoft 365 application names and logos are Microsoft Licensed Trademarks. For additional required Branding Guidelines, please refer to our [Microsoft Trademark and Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks).

## Requirements

The following requirements apply to an Microsoft 365 for the web integration.

1. **Don't display any UI on or around the Microsoft 365 editor.** The Microsoft 365 for the web editors must always be displayed 'edge-to-edge', with no surrounding UI. The editor cannot be 'light-boxed' or integrated as a component in host UI. The editor is a standalone application.  
     
   The Microsoft 365 for the web viewers can be 'light-boxed' or otherwise embedded in your web experience. However, if the user transitions to a Word, Excel, or PowerPoint editor, the editor must be edge-to-edge.  
     
   Embedding the Microsoft 365 for the web viewers or editors into native applications using a webview is not allowed.

Note

Refer to the support article titled [Which browsers work with Microsoft 365 for the web and Microsoft 365 Add-ins](https://support.microsoft.com/en-us/office/which-browsers-work-with-microsoft-365-for-the-web-and-microsoft-365-add-ins-ad1303e0-a318-47aa-b409-d3a5eb44e452) for more information on browser support for Microsoft 365 for the web across platforms.

2. **Use Microsoft-provided application and file type icons.** For more information, see [Application and file type icons](#application-and-file-type-icons).
3. **Provide favicons for the Microsoft 365 applications.** Whenever the editor or the viewer are displayed full-window or full-tab, respectively, the favicon for the page must be set to the appropriate favicon. The preferred method is to use the URLs provided in WOPI discovery. For more information, see [Favicon URLs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#favicon-urls).
4. **Use explicit Microsoft 365 application names in UI that opens Word, Excel, or PowerPoint.** For example, if you have a button that will open Microsoft Word for the web, the UI in your application must read, `Open in Microsoft Word for the web`.

   Note

   When a user selects the application link in the UI, the corresponding Microsoft 365 app must open immediately in a edge-to-edge browser tab or window. There should be no intermediate screens, dialogs, or experiences between the user action and the app display.
5. **Provide breadcrumb and breadcrumb URL values.** Breadcrumbs help users understand where their document is, as well as how to get back to where they were. For more information, see [Breadcrumbs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/ui-guidelines#breadcrumbs).

## Other recommendations

While the following guidelines are not required, Microsoft 365 for the web strongly recommends partners do the following:

1. **Provide support for sharing within Microsoft 365.** Microsoft 365 for the web provides a mechanism to share documents with other users directly within the Microsoft 365 for the web applications. You should take advantage of this capability so that users can access sharing controls directly within Microsoft 365 for the web. For more information,see [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) and [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl).
2. **Provide an in-app Edit in Browser button.** If you are using the Microsoft 365 for the web viewer and the current user has permissions to edit the document, you should provide a [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) so that the `Edit in Browser` button is always displayed. This helps provide a more seamless transition for users.

   Note

   You can also use the [**EditModePostMessage**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editmodepostmessage) property to receive a PostMessage when the `Edit in Browser` button is clicked, so you can handle the transition to edit mode yourself.
3. **Include the document name in the HTML title tag so it displays in the browser tab/window text.** This is especially important in cases where users may open multiple documents in different browser tabs/windows.

## Application and file type icons

Your solution represents Microsoft to your end users, and you are responsible for ensuring that the Microsoft brand is accurately and appropriately presented. A key aspect of this responsibility is the use of Microsoft-approved iconography for applications and file types. Because Microsoft periodically updates its product icons, you must ensure that your WOPI solution remains up to date with the latest approved assets at all times.

We strongly recommend implementing Microsoft Fluent UI. Fluent UI provides the iconography required for CSPP solutions to meet UI requirements and ensures consistent alignment with current Microsoft branding. By leveraging Fluent UI, your solution can easily stay up to date with the latest Microsoft-approved icons with a minimum of changes to your code. Visit [Fluent UI Iconography](https://fluent2.microsoft.design/iconography) for detailed information about using Fluent UI in your solution.

  


Important

You are responsible for ensuring your solution remains compliant with the latest UI requirements. Failure to maintain compliance—such as using outdated or non-approved UI elements—may result in removal from the CSPP.

  


Use the icons as follows:

1. When displaying an Microsoft file, either individually or as part of a list of files, use the file type icons. Don't use the application \(product\) icons for this purpose.
2. When displaying a button or other UI element that opens an Microsoft 365 for the web application, use the application icons. For example, if you display an `Open in Word on the web` button, use the Word application icon.

  


Important

If you re-size or otherwise modify the provided icons, you must use the vector source files to maintain the high image quality of the icons.

  


## Breadcrumbs

Breadcrumbs are an important navigational tool for users. They dramatically improve the user experience by providing helpful anchors so users can both understand where the document they're working on is located and more easily navigate in and out of the Microsoft 365 for the web applications.

WOPI supports [two levels of breadcrumbs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#breadcrumb-properties) only:

### BreadcrumbBrandName/BreadcrumbBrandUrl

Set these properties to the root of your navigational hierarchy. A basic rule of thumb is that clicking the breadcrumb takes the user to their logical *home* within your WOPI host.

In some cases, you might have several different siloed hierarchies within your application. In such cases, it might make more sense to set these properties to the root of the particular hierarchy in which the current document is located.

Ultimately, pick a location most appropriate for your users and application structure.

### BreadcrumbFolderName/BreadcrumbFolderUrl

Set these properties to the container in which the current document is located. A basic rule of thumb is that clicking this breadcrumb takes the user back to the same location they were in prior to opening the document.

Tip

If you support multiple paths to get to a file, you might wish to expose different breadcrumb properties depending on how the user navigated to the file. You can do this by using the [**session context**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#session_context) to customize your [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response.

### Example

Consider a logical hierarchy like this:

```text
Documents
├── Reviews
|   ├── Data
|   |   ├── Aggregate Data.xlsx
|   |   └── Raw Data.xlsx
|   └── Monthly Review.pptx
└── Deals
    ├── Integration Plans.docx
    └── Leads.xlsx
```

In this case, if the user opens `Aggregate Data.xlsx`, BreadcrumbBrandName/BreadcrumbBrandUrl should be set to `Documents`, while the BreadcrumbFolderName/BreadcrumbFolderUrl should be set to `Data`.

Similarly, if the user opens `Integration Plans.docx`, BreadcrumbBrandName/BreadcrumbBrandUrl should be set to `Documents`, while the BreadcrumbFolderName/BreadcrumbFolderUrl should be set to `Deals`.
