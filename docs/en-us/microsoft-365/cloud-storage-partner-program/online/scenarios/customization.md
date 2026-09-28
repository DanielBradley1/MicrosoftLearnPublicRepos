<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Customize Microsoft 365 for the web with CheckFileInfo properties

You can customize the user interface and experience of Microsoft 365 for the web by using [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) properties and setting up the [PostMessage API](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage).

## CheckFileInfo properties

The `CheckFileInfo` properties follow.

### CloseUrl

When the `Close` UI is activated, Office for the web navigates the outer page \(`window.top.location`\) to the URI provided.

Hosts can also use the [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage) property to indicate a PostMessage should be sent when the `Close` UI is activated rather than navigate to a URL. Or set the [CloseButtonClosesWindow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) property to indicate that the `Close` UI should close the browser tab or window \(`window.top.close`\).

If the [CloseUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl), [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage), and [CloseButtonClosesWindow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) properties are omitted, the `Close` UI is hidden in Microsoft 365 for the web.

Note

The `Close` UI never displays when using the `embedview` action.

For more information, see \[**CloseUrl**\]\(~/rest/files/CheckFileInfo/ CheckFileInfo-Response.md#closeurl\) in the WOPI REST documentation.

### DownloadUrl

If a `DownloadUrl` isn't provided, Microsoft 365 for the web hides all UI to download the file.

If provided, Word and PowerPoint for the web display UI to download the file. When a user attempts to download the file, Word and PowerPoint ensure that the latest document content is saved back to the WOPI host before navigating the user to the `DownloadUrl` for downloading the file.

### Excel for the web

Excel for the web doesn't use the `DownloadUrl` when users click the **Download a Copy** button. Excel for the web always downloads the file directly from the Office for the web server. This has the following effects:

- Any content that Excel for the web doesn't currently support, such as diagrams, are stripped from the downloaded file.
- Excel for the web doesn't guarantee that the latest document content is saved back to the WOPI host before downloading the file.
- `Download a Copy` contains the most recent document edits, even when the `DownloadUrl` is implemented incorrectly and doesn't point to the latest version of the document.

For more information, see [**DownloadUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#downloadurl) in the WOPI REST documentation.

### FileSharingUrl

If provided, when the `Share` UI is activated, Office for the web opens a new browser window to the URI provided.

Hosts can also use the [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) property to indicate a PostMessage should be sent when the *Share* UI is activated rather than navigate to a URL.

If neither the [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) nor the [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) properties are set, the *Share* UI is hidden in Microsoft 365 for the web.

For more information, see [**FileSharingUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) in the WOPI REST documentation.

### HostEditUrl

This URL is used by Microsoft 365 for the web to navigate between view and edit mode.

For more information, see [**FileSharingUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) in the WOPI REST documentation.

### HostViewUrl

This URL is used by Microsoft 365 for the web to navigate between view and edit mode.

For more information, see [**HostViewUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostviewurl) in the WOPI REST documentation.

### SignoutUrl

If you don't provide this property, no sign out UI is shown in Microsoft 365 for the web.

For more information, see [**SignoutUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#signouturl) in the WOPI REST documentation.

### CloseButtonClosesWindow

If set to `true`, Microsoft 365 for the web closes the browser window or tab \(`window.top.close`\) when the *Close* UI in Microsoft 365 for the web is activated.

If Microsoft 365 for the web displays an error dialog when booting, dismissing the dialog is treated as a close button activation with respect to this property.

Hosts can also use the [CloseUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl) property to indicate that the outer frame should be navigated \(`window.top.location`\) when the `Close` UI is activated rather than closing the browser tab or window. Or set the [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage) property to indicate a PostMessage should be sent when the `Close` UI is activated.

If the [CloseUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl), [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage), and [CloseButtonClosesWindow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) properties are omitted, the *Close* UI is hidden in Office for the web.

Note

The `Close` UI never displays when using the `embedview` action.

For more information, see [**CloseButtonClosesWindow**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) in the WOPI REST documentation.

### Breadcrumb properties

Microsoft 365 for the web displays the [Breadcrumb properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#breadcrumb-properties) if they're provided.

## PostMessage properties

The PostMessage properties control the behavior of Microsoft 365 for the web with respect to incoming PostMessages. If you're using the `PostMessage` extensibility features, you must set the [PostMessageOrigin](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#postmessageorigin) property to ensure that Microsoft 365 for the web accepts messages from your outer frame. For more information about PostMessage integration, see [Using PostMessage to interact with the Microsoft 365 for the web application iframe](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage).

In cases where a PostMessage is triggered by the user activating some Microsoft 365 for the web UI, such as [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) or [EditModePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editmodepostmessage), Microsoft 365 for the web does nothing when the relevant UI is activated except send the appropriate PostMessage. Thus, hosts must accept and handle the relevant messages when the Microsoft 365 for the web UI is triggered. Otherwise, the Microsoft 365 for the web UI appears to do nothing when activated.

If the PostMessage API isn't supported \(for example, the user's browser doesn't support it, or the browser security settings prohibit it, and so on\), Microsoft 365 for the web UI that triggers a PostMessage is hidden.

### AppStateHistoryPostMessage

A **Boolean** value that, when set to `true`, indicates the host outer frame supports the use of [HTML5 Session History](https://www.w3.org/TR/2011/WD-html5-20110113/history.html). The outer frame should then expect to receive `App_PushState` PostMessages and propagate `onpopstate` events to Microsoft 365 for the web through the `App_PopState` PostMessage.

### OneNote Online

Note

This message is only used by OneNote for the web and isn't required to integrate with Microsoft 365 for the web or Microsoft 365 for mobile. It's included for completeness but doesn't need to be implemented.

OneNote for the web integration isn't included in the Microsoft 365 - Cloud Storage Partner Program.

### ClosePostMessage

A **Boolean** value that, when set to `true`, indicates the host expects to receive the `UI_Close` PostMessage when the `Close` UI in Microsoft 365 for the web is activated.

Hosts should use the [CloseUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl) property to indicate that the outer frame should be navigated \(`window.top.location`\) when the `Close` UI is activated rather than sending a PostMessage. Or to set the [CloseButtonClosesWindow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) property to indicate that the `Close` UI should close the browser tab or window \(`window.top.close`\).

If the [CloseUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl), [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage), and [CloseButtonClosesWindow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#closebuttoncloseswindow) properties are omitted, the `Close` UI is hidden in Office for the web.

Important

The [**CloseUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl) must always be provided in order for the `Close` UI to appear in Microsoft 365 for the web, even if [**ClosePostMessage**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage) is `true`.

Most PostMessage-related properties don't require that the corresponding URL property be provided in order to enable the relevant UI in Microsoft 365 for the web. [**CloseUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl) is an exception to this.

**See also**

[**Best practices when using PostMessage properties**](#best-practices-when-using-postmessage-properties)

Note

The `Close` UI never displays when using the `embedview` action.

### EditModePostMessage

A **Boolean** value that, when set to `true`, indicates the host expects to receive the UI\_Edit PostMessage when the `Edit` UI in Microsoft 365 for the web is activated.

If this property is not set to `true`, Microsoft 365 for the web navigates the inner iframe URL to an edit action URL when the `Edit` UI is activated.

### EditNotificationPostMessage

A **Boolean** value that, when set to `true`, indicates the host expects to receive the `Edit_Notification` PostMessage.

### FileEmbedCommandPostMessage

A **Boolean** value that, when set to `true`, indicates the host expects to receive the `UI_FileEmbed` PostMessage when the Embed UI in Microsoft 365 for the web is activated.

Hosts can also use the [FileEmbedCommandUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileembedcommandurl) property to indicate that a new browser window should be opened when the Embed UI is activated rather than sending a PostMessage. The [FileEmbedCommandUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileembedcommandurl) property is ignored completely if the `FileEmbedCommandPostMessage` property is set to `true`.

If neither the [FileEmbedCommandUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileembedcommandurl) nor the [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) properties are set, the Embed UI is hidden in Microsoft 365 for the web unless a [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl) is provided in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

### FileSharingPostMessage

A **Boolean** value that, when set to `true`, indicates the host expects to receive the UI\_Sharing PostMessage when the `Share` UI in Microsoft 365 for the web is activated.

Hosts can also use the [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) property to indicate that a new browser window should be opened when the `Share` UI is activated rather than sending a PostMessage. The [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) property is ignored completely if the `FileSharingPostMessage` property is set to `true`.

If neither the [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) nor the [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) properties are set, the `Share` UI is hidden in Microsoft 365 for the web.

### FileVersionPostMessage

A **Boolean** value that, when set to `true`, indicates the host expects to receive the `UI_FileVersions` PostMessage when the `Previous Versions` UI \(*File ‣ Info ‣ Previous Versions*\) in Microsoft 365 for the web is activated.

Hosts can also use the [FileVersionUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileversionurl) property to indicate that a new browser window should be opened when the Previous Versions UI is activated rather than sending a PostMessage. The [FileVersionUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileversionurl) property is ignored completely if the `FileVersionPostMessage` property is set to `true`.

If neither the [FileVersionUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileversionurl) nor the [FileVersionPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#fileversionpostmessage) properties are set, the `Previous Versions` UI is hidden in Microsoft 365 for the web.

### PostMessageOrigin

A **string** value indicating the domain that the [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page) is sending and receiving PostMessages to and from. Microsoft 365 for the web only sends outgoing PostMessages to this domain, and only listens to PostMessages from this domain.

Tip

This value is used as the *targetOrigin* when Microsoft 365 for the web uses the [HTML5 Web Messaging protocol](http://www.w3.org/TR/webmessaging/). So, it must include the scheme and host name. If you're serving your pages on a non-standard port, you must include the port as well. The literal string `*`, while supported in the PostMessage protocol, isn't allowed by Microsoft 365 for the web.

### WorkflowPostMessage

***! Pre-release property - not yet used by any WOPI client***

A **Boolean** value that, when set to `true`, indicates the host expects to receive the UI\_Workflow PostMessage when the `Workflow` UI in Microsoft 365 for the web is activated.

Hosts can also use the [WorkflowUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowurl) property to indicate that a new browser window should be opened when the `Workflow` UI is activated rather than sending a PostMessage. The [WorkflowUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowurl) property is ignored completely if the `WorkflowPostMessage` property is set to `true`.

If neither the [WorkflowUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowurl) nor the [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) properties are set, the `Workflow` UI is hidden in Microsoft 365 for the web.

Important

This value is ignored if [**WorkflowType**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowtype) isn't provided.

## Best practices when using PostMessage properties

The WOPI protocol is designed for a variety of scenarios and environments. While PostMessage is a useful integration technique for web-browser-based WOPI clients such as Microsoft 365 for the web, it's not usable in other WOPI clients, such as Microsoft 365 for mobile.

To provide maximum compatibility with all types of WOPI clients, hosts should set corresponding URL properties when using PostMessage properties. For example, when setting [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) to `true`, hosts should also provide a [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl). This enables a WOPI client that can't use PostMessage to navigate the user to a URL that does allow them to manage sharing the file.

While the primary reason to provide corresponding URL properties for PostMessage properties is for non-browser-based WOPI clients, there are legitimate reasons to do this for Microsoft 365 for the web as well. In particular, users might use browsers that don't support PostMessage. While all officially supported Microsoft 365 for the web browsers support PostMessage, when users are on unsupported browsers, Microsoft 365 for the web strives to give them the best possible experience. Providing the URL properties enables users to access Microsoft 365 for the web features even in browsers where PostMessage won't work.

## Customizing the Microsoft 365 for the web viewer UI using CheckFileInfo

The following table describes the available buttons and UI in the Microsoft 365 for the web viewer and what [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) properties can be used to remove them.

| Button | How to disable |
| --- | --- |
| Edit in Browser | Two options:  <br>  <br>1. **\(preferred\)** Set [UserCanWrite](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercanwrite) to `false` in the CheckFileInfo response \(or omit it since the default for all boolean properties in CheckFileInfo is `false`\)  <br>2. Omit the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) and [EditModePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editmodepostmessage) properties from the `CheckFileInfo` response |
| Share | Omit the [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) and [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) properties from the `CheckFileInfo` response |
| Download / Download as PDF | Omit the [DownloadUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#downloadurl) property from the `CheckFileInfo` response |
| Print | Set the [DisablePrint](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#disableprint) property to `true` in the `CheckFileInfo` response |
| Comments | Can’t be hidden |
| Find | Can’t be hidden |
| Translate | Can’t be hidden |
| Help | Can’t be hidden |
| Give Feedback | Can’t be hidden |
| Terms of Use | Can’t be hidden |
| Privacy and Cookies | Can’t be hidden |
| Accessibility Mode | Can’t be hidden |
| Start Slide Show | Can’t be hidden |
| Embed | Omit the [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl) and [HostEmbeddedEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#hostembeddedediturl) properties from the `CheckFileInfo` response |
| Refresh Selected Connection | Can’t be hidden |
| Refresh All Connections | Can’t be hidden |
| Calculate Workbook | Can’t be hidden |
| Save a Copy | Set the [UserCanNotWriteRelative](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercannotwriterelative) property to `true` in the `CheckFileInfo` response |
