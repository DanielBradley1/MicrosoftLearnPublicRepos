<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/troubleshooting -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Troubleshooting interactions with Microsoft 365 for the web

When integrating with Microsoft 365 for the web, it might be necessary to work with Microsoft engineers to diagnose problems. Following the steps here help both you and Microsoft diagnose problems more quickly.

## Before reporting issues

Before reporting any issues to Microsoft, ensure that you've done the following:

1. Check that the [WOPI Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator) tests are passing. Most common issues are easily diagnosed using the Validator, and passing tests are a pre-requisite for any investigations into issues you're encountering.

   Tip

   In cases where the Validator tests aren't consistent with the documentation, assume that the validator is correct. Also, [**file an issue**](https://github.com/Microsoft/Office-Online-Test-Tools-and-Documentation/issues) so we can address any gaps in the documentation.
2. Check the [Common implementation problems](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/common-issues) to see if you've made one of the more common mistakes in your WOPI implementation.
3. Check the [Known Issues](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/known-issues) to see if what you're encountering is already known. When possible, workarounds are provided in the issue notes.

## Fiddler traces

The most useful tool when troubleshooting Microsoft 365 for the web integration issues is [Fiddler](http://www.telerik.com/fiddler). When you run Fiddler while reproducing an issue, it will record all HTTP requests and responses. You can then save the Fiddler trace and share it with Microsoft engineers. Fiddler traces are an invaluable tool when troubleshooting problems because they provide a full record of the HTTP traffic between the browser and Microsoft 365 for the web. As a rule of thumb, hosts should always provide a Fiddler trace when reporting Microsoft 365 for the web integration issues to Microsoft.

### Enabling HTTPS decryption in Fiddler

Because Microsoft 365 for the web traffic is encrypted, Fiddler must be configured to decrypt the HTTPS traffic in order to be useful. In order to enable HTTPS encryption in Fiddler, do the following:

1. From Fiddler, click **Tools** > **Options…** to open the options dialog.
2. On the **HTTPS** tab, check the **Capture HTTPS CONNECTs** check box.
3. Check the **Decrypt HTTPS traffic** check box. When you do this, Fiddler displays a dialog asking if you want to trust the Fiddler Root certificate. Click **Yes**. You might also see some security warnings from the operating system asking if you want to install the certificate. Click **Yes** to all of these prompts.
4. In the drop-down, select **…from browsers only**.
5. Click **OK** in the options dialog.
6. Close Fiddler and restart it.

Fiddler is now configured to decrypt HTTPS traffic.

![Figure 9 Fiddler must be configured to decrypt HTTPS traffic in order to produce useful traces](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/fiddler-https.png)

***Figure 9 -** Fiddler must be configured to decrypt HTTPS traffic in order to produce useful traces*

### Using Fiddler to trace a session

Using Fiddler to trace HTTP activity is straightforward:

1. Open Fiddler.
2. If needed, begin capturing traffic. Select **File** > **Capture Traffic**. Fiddler starts in capture mode when it's opened, so this step might not be necessary.
3. Navigate to the host page URL while Fiddler is running, then reproduce the issue if needed.
4. Once the issue is reproduced, save the Fiddler session as an archive. Select **File** > **Save** > **All sessions…**. The resulting file should have the file extension `.saz`.

### Using Fiddler in Linux or OS X

Fiddler works well in Windows, but can also be used in Linux and OS X using Mono. For more information on installing and configuring it, see [http://fiddler.wikidot.com/mono](http://fiddler.wikidot.com/mono).

## Alternatives to Fiddler: HTTP Archives \(HAR\)

If you can't use Fiddler to get session traces, you can use the Chrome browser developer tools. These tools let you save HTTP Archive \(HAR\) files containing the HTTP requests made by the browser. Do the following.

1. Open the Chrome developer tools and select the **Network** tab.
2. Check the **Preserve log** check box if you want to retain the request log across multiple page navigations. This makes the network tracing behave more like Fiddler, and makes it less likely that you’ll lose your request log by accidentally refreshing the page or navigating away before you save the log. Office for the web applications are single-page applications, so you don’t *need* to check this if you're only planning to trace a single session.

   ![Figure 10 Network tab in the Chrome developer tools](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/chrome-network-tab.png)


   ***Figure 10 -** Network tab in the Chrome developer tools*

3. After you are done reproducing the issue, right-click in the network view and select the **Save as HAR with Content** option.

   ![Figure 11 Save as HAR with Content option in the Chrome developer tools](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/chrome-save-as-har.png)


   ***Figure 11 -** Save as HAR with Content option in the Chrome developer tools*

4. Zip the resulting HAR file, since they can be quite large and generally compress well.

Tip

Other browsers’ developer tools have similar capabilities to Chrome to save session HTTP requests as an HTTP Archive.

## Session IDs

Whenever an [action URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-urls) is navigated to, Microsoft 365 for the web creates a unique session ID. This session ID lets Microsoft engineers quickly retrieve all server logs related to that session, including information about the WOPI calls that were made to the host.

The session ID is passed back in the WOPI action URL HTTP response in the **X-UserSessionId** response header. It's also passed on every subsequent request made by the browser to Office for the web in the **X-UserSessionId** request header. And it's included in all PostMessages [sent from Microsoft 365 for the web to the host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage#listening-to-messages-from-the-microsoft-365-for-the-web-iframe) in the [wdUserSession](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage#wdusersession-string) value.

The easiest way to retrieve the session ID is to use Fiddler, as described previously. But you can also use the request tracking features in the Chrome and Internet Explorer developer tools to capture HTTP requests and determine the value of the **X-UserSessionId** response header.

![Figure 12 You can use the Chrome developer tools to retrieve a session ID.](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/chrome-session-id.png)

***Figure 12 -** You can use the Chrome developer tools to retrieve a session ID.*

![Figure 13 As can the Internet Explorer developer tools.](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/ie-session-id.png)

***Figure 13 -** As can the Internet Explorer developer tools.*

Full Fiddler traces are always preferred, but in cases where they’re not available, session IDs can still be used by Microsoft engineers to retrieve Office for the web server logs.

### Getting session IDs after an error has occurred

In some cases, you might not be running Fiddler or browser developer tools when your session encounters an error. In these cases, the Microsoft 365 for the web application displays an error either in a modal dialog or in a yellow bar at the top of the document below the ribbon.

Sometimes the error dialog includes the session ID in the dialog itself:

![An image of an error dialog in Word on the web that includes a session ID.](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/error-with-session-id-and-exit-button.png)

In such cases, you can copy the session ID from the error dialog.

Tip

**It's best if you don't simply send a screen shot of the error dialog**. Copy the session ID as text and send the session ID itself to Microsoft engineers. If you send a screen shot, the Microsoft engineer is forced to transcribe the session ID from the image, which is error-prone and tedious. Always provide the session ID as text.

In other cases, the session ID might not be available in the UI.

![An image of an error in Word on the web displayed in a yellow bar under the ribbon.](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/error-bizbar.png)

At this point, it's still often possible to get the session ID by using the following steps:

1. Before closing the browser, refreshing the page, or clicking any buttons in the dialog or notification bar, start Fiddler or open the browser developer tools.
2. Navigate away from the Microsoft 365 for the web application or click a button in the dialog or notification bar.
3. You should see a request to either WsaUpload.ashx or RemoteUls.ashx. The response to those requests should include the **X-UserSessionId** header with the session ID.

## Correlation IDs

Every WOPI request Office for the web makes to a host has an ID called the correlation ID. This ID is included in the WOPI request using the **X-WOPI-CorrelationId** request header. Hosts should log this ID for each incoming WOPI request. Logging the ID allows hosts to easily correlate their own logs with the Office for the web server logs.

There are other WOPI request headers that might be useful for hosts to log. See the [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers) for more information.

Tip

In many cases, a single correlation ID is all that’s needed for a Microsoft engineer to retrieve complete server logs on an Office for the web session for analysis. While hosts should provide Fiddler traces or session IDs whenever possible, a correlation ID often suffices if necessary.
