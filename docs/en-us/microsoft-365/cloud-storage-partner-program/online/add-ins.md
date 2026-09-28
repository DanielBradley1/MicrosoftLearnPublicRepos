<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/add-ins -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Enable Microsoft 365 Add-ins provided by a WOPI host

The WOPI Add-in user experience is different from that of a standard Microsoft 365 for the web session in three important ways:

- By default, Add-ins are not enabled for users connecting to Microsoft 365 through a WOPI host.
- If Add-ins are enabled, the Add-in button will be displayed in the Microsoft 365 ribbon. However, the Add-in store can not be used by a WOPI connected user. If the user clicks the Add-in button and attempts to sign in to the Add-in store, they will receive a message that the store has been disabled.
- Add-ins must be either preinstalled or sideloaded. See the Microsoft documentation for more information about [preinstalling](#preinstall-add-ins) and [sideloading](https://learn.microsoft.com/en-us/office/dev/Add-ins/testing/sideload-office-Add-ins-for-testing) Add-ins.

## Getting started with WOPI Add-ins

1. Join the Cloud Storage Partner Program \(CSPP\). Learn more about the program from [Cloud Storage Partner Progam Overview](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/) and complete the [Office Cloud Storage Partner Program Application](https://aka.ms/cspp-apply).
2. Use the [CSPP Enironment Change Request form](https://aka.ms/cspp-update) to request that your CSPP WOPI environment be updated to have Add-ins enabled.
3. Create your Add-in. See the [Add-in developer documentation](https://learn.microsoft.com/en-us/office/dev/add-ins/develop/develop-overview) for more information.
4. Be sure to enable the Add-in function using the [CheckFileInfo property 'AllowExternalMarkeplace'](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#allowexternalmarketplace). This is a Boolean value that must be set to true for WOPI Add-ins to be loaded
5. Complete the required security handshake with your host for Add-ins to run \(see the [Security requirements to host Add-ins](#security-requirements-to-host-add-ins) section\). This must be done for every Add-in.
6. Preinstall Add-ins to provide them for your users. Submit an array of one or more Add-ins as a Form field value as part of the POST request sent to Microsoft 365 for the web server \(see the [Preinstall Add-ins](#preinstall-add-ins) section\).

## Security requirements to host add-ins

Add-ins won’t activate in the Microsoft 365 document without completing the appropriate check. This ensures the host isn’t currently embedded in an unexpected environment. The check outlined below is completed as part of [PostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage).

The [App\_IsFrameTrusted message](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage#app_isframetrusted) is posted by Microsoft 365 on the web application frame to initiate the handshake flow. The host is expected to determine whether the top frame is trusted and post a [Host\_IsFrameTrusted message](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage#host_isframetrusted) back to the Microsoft 365 for the web application. The host first needs to append the query string `&sftc=1` to the URL of POST request sent to the Microsoft 365 on the web application. This message must be sent as a string.

## Preinstall Add-ins

WOPI hosts can allow their choice of Add-ins to be enabled. All of these Add-ins can be [sideloaded](https://learn.microsoft.com/en-us/office/dev/Add-ins/testing/sideload-office-Add-ins-for-testing), which is part of the development process. For an add-in to be preinstalled and ready for users to open, the Add-in must be in available in [AppSource](https://learn.microsoft.com/en-us/azure/marketplace/submit-to-appsource-via-partner-center).

Send the list of Add-ins the host page provides as a Form field value. This is done as part of the [POST request body sent to Microsoft 365 for the web server](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage). The data format of the Form is an encoded string version of the JSON. The Form data field name of data is `host_install_addins`.

The following code snippet shows the Form field name and value format of `host_install_addins`.

```HTML
<body>
    <form id="office_form" name="office_form" target="office_frame" action="<OFFICE_ACTION_URL>" method="post">
        <input name="access_token" value="<ACCESS_TOKEN_VALUE>" type="hidden" />
        <input name="access_token_ttl" value="<ACCESS_TOKEN_TTL_VALUE>" type="hidden" />
        <input name="host_install_addins" value="<JSON_OF_ADD-INS_LIST>" type="hidden" />
    </form>`
</body>
```

The value of `<JSON_OF_ADD-INS_LIST>` is a list of Add-ins reference data in the following stringified-JSON format. Note that you must use an [HTML-encoding tool](https://www.w3docs.com/tools/html-encoder/) to convert the JSON string. You cannot send the string without encoding it.

```JSON
[
    { addinId: "WA123456781", type: "TaskPaneApp"},
    { addinId: "WA123456782", type: "TaskPaneApp"},
    { addinId: "WA123456783", type: "TaskPaneApp"},
    { addinId: "WA123456784", type: "TaskPaneApp"}
]
```

## Add-in restrictions

Currently, only Add-ins with [Add-in commands](https://learn.microsoft.com/en-us/office/dev/add-ins/design/add-in-commands) are supported.

## Testing

To troubleshoot enabling or preinstalling Add-ins, use a tool that can intercept and display the HTTP Requests from, and Responses to, your WOPI host. Test the setup by mimicking the data payload of Add-ins sent by your WOPI host page before you implement it in your page. This section explains how to do that with [Fiddler](https://www.telerik.com/fiddler), but you should use whichever tool is familiar to you.

1. Get the ID for the Add-in from [AppSource](https://appsource.microsoft.com/marketplace). The ID is the unique part of the Add-in’s URL. For example, the [Emoji Keyboard Add-in](https://appsource.microsoft.com/product/office/WA104380121?tab=Overview&exp=ubp8) has the ID WA104380121.
2. Record the JSON as you would for the POST command with the ID from step 1. For example, `[{“addinId”:”WA104380121”,”type”:”TaskPaneApp”}]`. The type is always `TaskPaneApp`.
3. Use an [HTML-encoding tool](https://www.w3docs.com/tools/html-encoder/) to convert the JSON string from step 2. The previous example would end up like this: `%5B%7B%22addinId%22%3A%22WA104380121%22%2C%22type%22%3A%22TaskPaneApp%22%7D%5D`.
4. In Fiddler, add the following section to `FiddlerScript`, in the function `OnBeforeRequest`. The string appended to the request body is the encoded string from step 3.

   ```js
   if (oSession.PathAndQuery.StartsWith("/we/wordeditorframe.aspx?"))
   {
       oSession.utilSetRequestBody(
           oSession.GetRequestBodyAsString() +
           "&host_install_addins=%5B%7B%22addinId%22%3A%22WA104380121%22%2C%22type%22%3A%22TaskPaneApp%22%7D%5D");
   }
   ```

5. To test with Excel for the web, use the following condition instead.

   ```js
   if (oSession.PathAndQuery.StartsWith("/x/_layouts/xlviewerinternal.aspx?"))
   ```

## Troubleshooting

To troubleshoot any data format or encoding issue, examine the payload that Fiddler mimics in the Fiddler request panel. You can also check the `console.log` output in browser debugger console window.

## Support

For support specific to Microsoft 365 Add-ins integration, visit [Microsoft 365 Add-ins additional resources](https://learn.microsoft.com/en-us/office/dev/add-ins/resources/resources-links-help) to find the appropriate support channel.

## Frequently asked questions

### Why don't I see the Add-in button in the ribbon?

The Add-in button is only displayed if Add-ins have been enabled by the CSPP team for your WOPI host.

### Why can't I use an Add-in to insert another file into the current document in Microsoft 365 for the web - even though I can do that with the Microsoft 365 desktop apps?

In Excel, functionality was added to the Add-in platform at a different time and may require an update from the Add-in developer. In Word, this functionality is currently in preview and will be released after sufficient testing.

### Why don't Add-ins persist from one session to the next? For example, if I install an Add-in while writing a document, then close the document, when I open Word again the Add-in isn't there and I have to reload it.

When a developer creates an Add-in, they often use a setting to enable persistence between sessions. This isn’t something that occurs by default. Another reason would be that the Add-in being used was sideloaded by the end user, which is meant for developers to test their Add-ins. Finally, web browsers offer different settings for blocking information storage based on user privacy settings. What is stored in the browser cache has an impact on what Add-ins are available in Microsoft 365 on the web between sessions.

### Can I send information \(such as a user ID\) from the host page to the web Add-in?

Add-ins use the Microsoft 365 JavaScript APIs to interact with the Microsoft 365 host and the document. You can find additional information in the [Microsoft 365 JavaScript API reference documentation](https://learn.microsoft.com/en-us/javascript/api/overview).

### Do I need to register my Add-in with the CSPP Team if I am not hosting my Add-in in the Store?

Yes. Please note that preinstall functionality will not work for Add-ins that are not submitted to AppSource.

### Is there a way to stop my users from being prompted to trust Add-ins?

No. It is important for users to understand the activity happening in their Microsoft 365 session and the potential liabilities that come with web services.
