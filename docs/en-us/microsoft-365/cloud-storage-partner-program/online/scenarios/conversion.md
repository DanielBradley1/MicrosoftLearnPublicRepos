<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/conversion -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Edit legacy binary document formats

Microsoft 365 for the web doesn't support editing files in binary formats such as `doc`, `ppt`, and `xls`, directly. However, Microsoft 365 for the web can convert documents in the legacy formats to modern formats like `docx`, `pptx`, and `xlsx`, to let users edit the content in Microsoft 365 for the web.

Important

Conversion is almost always a lossless process, and there are typically very few, if any, user-visible changes to the layout and formatting of the document during conversion. However, this isn't always the case. Hosts should be aware that users might wish to revert to the previous binary version of the document after it's been converted.

The conversion capability is exposed in WOPI discovery as the `convert` action. To support editing binary file formats, hosts must support the [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) WOPI operation. The conversion process is started byrunning the `convert` action on the binary file. Following is the high-level process:

1. The host runs the `convert` action on a binary file.
2. Microsoft 365 for the web retrieves the file from the host and converts it.
3. Microsoft 365 for the web sends the converted document back to the host by issuing a [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) request against the original file ID.
4. Hosts use the **X-WOPI-FileConversion** header on the [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) request to determine that the request is being made in the context of a file conversion. Hosts can then treat these requests differently than other `PutRelativeFile` requests.
5. After the document is successfully converted, Microsoft 365 for the web redirects the user to the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) that's returned in the `PutRelativeFile` response. Microsoft 365 for the web always redirects the topmost window \(`window.top`\).

## Enabling convert and edit from within the Microsoft 365 for the web viewer

In the basic conversion flow described earlier, a user runs the `convert` action using some UI on the host. But hosts might wish to open a document first in the Microsoft 365 for the web viewer and use the Microsoft 365 for the web in-application `Edit` button to convert and edit the document, as is done with documents in editable formats.

Hosts can support this process in the same way that view -> edit transitions are typically supported. Hosts must do the following when opening binary documents using the `view` action:

1. Set the [UserCanWrite](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercanwrite) property to `true`.
2. Set the [UserCanNotWriteRelative](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercannotwriterelative) property to `false` \(or simply omit it\).
3. Set the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) property to a host URL that runs the `convert` action when loaded.

Following these steps ensures that the in-application `Edit` button displays. When clicked, this button navigates the user to the `HostEditUrl` provided for the binary file, which starts the conversion process and eventually redirects the user to the `HostEditUrl` for the newly converted document.

Hosts might optionally handle the in-application `Edit` button themselves by setting the [EditModePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editmodepostmessage) property to `true` and handling the `UI_Edit` PostMessage.

## Customizing the conversion process

In the basic conversion process, Microsoft 365 for the web creates a new file each time a user attempts to edit a file in a binary file format. For example, consider this scenario:

1. A user opens a binary file named `File.doc` in the Microsoft 365 for the web viewer.
2. The user clicks the `Edit` button in the Microsoft 365 for the web viewer.
3. The conversion process starts, and Microsoft 365 for the web calls [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) on the host, creating a newly converted file, `File.docx`.
4. The user edits the newly converted document, then ends the editing session.
5. Later, the user returns and opens the original binary file, `File.doc`, in the Microsoft 365 for the web viewer.

At this point, the user Might be confused as to why the changes made earlier aren't in the document. If the user attempts to edit the file again, Microsoft 365 for the web again converts it and creates a *second* converted file, for example `File1.docx`.

This can be confusing for users depending on how the host UI user experience is designed. Thus, it's important to consider how to manage user confusion around converted documents. There are three basic customization options that hosts can employ to help manage this.

First, the host can choose to display some UI to the user prior to beginning the conversion process. Because hosts ultimately control when the `convert` action is invoked, a host could choose to display a notification message when a user attempts to edit a binary document, informing them that the document will be converted. This can also apply to the in-application `Edit` button by setting the [EditModePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editmodepostmessage) property to `true` and handling the `UI_Edit` PostMessage.

Second, the host can choose to handle converted documents in a unique way, by handling the [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) operation differently when called from the conversion flow. The **X-WOPI-FileConversion** header tells hosts when the operation is being called from the conversion flow, so the host can choose how best to handle those requests.

Finally, the host can control where the user is navigated after conversion is complete. Microsoft 365 for the web navigates to the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) that's returned in the `PutRelativeFile` response, which the host controls. So, hosts can customize where the user lands after the conversion is finished. This let hosts opt not to send the user directly to the Microsoft 365 for the web editor, but to any URL they wish. For example, a host might redirect the user to an interstitial page that informs them their document has been converted.

The following are some examples illustrating how these options can be used by hosts to change the user experience around file conversion. These examples are not meant to be exhaustive. Hosts can opt to customize the conversion process and flow in ways not described here.

### Example 1

In the following example, the host helps the user understand the conversion process by naming the converted file so it's clear that the file was converted from a binary file.

1. A user selects a binary file in the host UI and chooses to edit it using Microsoft 365 for the web.
2. The conversion process starts, and Microsoft 365 for the web calls [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) with the converted document content.
3. The host creates a new file as part of the `PutRelativeFile` request and appends `(Editable)` to the name of the file.
4. The user is navigated to a page that lets them edit the newly converted file in Microsoft 365 for the web.

### Example 2

In the following example, the host wishes to hide the conversion process from the user to provide the most frictionless experience possible.

1. A user selects a binary file in the host UI and chooses to edit it using Microsoft 365 for the web.
2. The conversion process starts, and Microsoft 365 for the web calls [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) with the converted document content.
3. Rather than create a new file, the host chooses to add the converted file as a new version to the existing binary file.
4. The user is navigated to a page that lets them edit the newly converted file in Microsoft 365 for the web.
5. The user can restore the binary version of the file by using the version history features within the host.

Note

This approach might not be feasible for all hosts, depending on how file metadata and versions are handled within their system. However, it does offer the following benefits:

- The user only ever sees a single document both before and after the document is converted.
- Since there is always only a single document, the user always finds the *right* document. That is, if the user edited the file - which is likely since they invoked the conversion process by attempting to edit a binary document - then when they open the file a second time, their previous edits are there, just as they expect.

### Example 3

In the following example, the host deems it important to inform users explicitly about the conversion process and its possible side effects.

1. A user selects a binary file in the host UI and chooses to edit it using Microsoft 365 for the web.
2. The host displays a notification message with the following text:

   In order to edit **File.doc**, it must be converted to a modern file format. If the document doesn’t look the same after it’s converted, don’t worry - you can always get the original file back if you need to.

   ![Figure 16 Example conversion notification message](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/conversion-warning-dialog.png)


   ***Figure 16 -** Example conversion notification message*


   The user can cancel the conversion operation or choose to continue with it.

3. If the user chooses to continue, the host navigates them to a page that runs the `convert` action on the file.
4. The conversion process starts, and Microsoft 365 for the web calls [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) with the converted document content.
5. The host returns a special URL in the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) property in the `PutRelativeFile` response. Microsoft 365 for the web navigates the user to that URL once the conversion completes.
6. The user lands on the URL specified by the host, and sees the following message:

   Your file, **File.doc**, has been converted to a new file, **File.docx**. The new file is in a modern file format, and the file extension has changed. If you don’t need the original file any more, you can delete it.

   ![Figure 17 Example conversion completed message](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/conversion-completed-dialog.png)


   ***Figure 17 -** Example conversion completed message*


   The message includes a button that the user can use to delete the original file immediately if they wish.

7. Once the user clicks `OK`, they’re navigated to a page that invokes the `edit` action on the converted file.

### Variant 3.1: Display post-conversion message in the Microsoft 365 for the web UI

In steps 5 and 6, rather than navigating the user to an interstitial page, the host can choose to append some parameters to the standard `HostEditUrl`. Then, when that `HostEditUrl` is navigated to, the host page uses the parameters that were added to the URL to determine that the dialog described in step 6 should be displayed. The host can display that notification above the Microsoft 365 for the web editor frame. This is similar to what hosts do when handling the `UI_Sharing` PostMessage.

Tip

Hosts must ensure that they properly use the `Blur_Focus` and `Grab_Focus` messages when drawing UI over the Microsoft 365 for the web frame.
