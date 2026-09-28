<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/postmessage -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Using PostMessage to interact with the Microsoft 365 for the web application iframe

You can integrate your own UI into Microsoft 365 for the web applications. You can then use your UI for actions on Microsoft 365 documents, such as sharing.

To integrate with Microsoft 365 for the web in this way, set up the [HTML5 Web Messaging protocol](http://www.w3.org/TR/webmessaging/). The Web Messaging protocol, also known as PostMessage, lets Microsoft 365 for the web frame communicate with its parent [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#host-page), and vice-versa. The following example shows the general syntax for PostMessage. In this example, `otherWindow` is a reference to another window that `msg` posts to.

### otherWindow.postMessage\(msg, targetOrigin\)

### Arguments

- **msg** \(*string*\) – A string \(or JSON object\) that contains the message data.
- **targetOrigin** \(*string*\) – Specifies what the origin of `otherWindow` is for the event to be dispatched. This value is set to the [PostMessageOrigin](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#postmessageorigin) property provided in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). The literal string `*`, while supported in the PostMessage protocol, isn't allowed by Microsoft 365 for the web.

## Message format

All messages posted to and from the Microsoft 365 for the web application frame are posted using the `postMessage()` function. Each message \(the `msg` parameter in the `postMessage()` function\) is a JSON-formatted object of the form:

### message

### MessageId *\(string\)*

The name of the message being posted.

### SendTime *\(long\)*

The time the message was sent, expressed as milliseconds since midnight, January 1, 1970, UTC.

Tip

You can get this value in most modern browsers using the `Date.now()` method in JavaScript.

### Values *\(JSON-formatted object\)*

The data associated with the message. This varies per message.

The following example shows the msg parameter for the `Host_PerfTiming` message.

```json
{
    "MessageId": "Host_PerfTiming",
    "SendTime": 1329014075000,
    "Values": {
        "Click": 1329014074800,
        "Iframe": 1329014074950,
        "HostFrameFetchStart": 1329014074970,
        "RedirectCount": 1
    }
}
```

## Sending messages to the Microsoft 365 for the web iframe

To send messages to the Microsoft 365 for the web iframe, set the [PostMessageOrigin](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#postmessageorigin) property in your WOPI [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response to the URL of your host page. If you don't do this, Microsoft 365 for the web ignores any messages you send to its iframe.

You can send the following messages; all others are ignored:

- `App_PopState`
- `Blur_Focus`
- `CanEmbed`
- `Grab_Focus`
- `Host_PerfTiming`
- `Host_PostmessageReady`

### App\_PopState

### OneNote for the web

Note

This message is only used by OneNote for the web and isn't required to integrate with Microsoft 365 for the web or Microsoft 365 for mobile. It's included for completeness but doesn't need to be implemented.

OneNote for the web integration isn't included in the Microsoft 365 - Cloud Storage Partner Program.

The App\_PopState message signals the Microsoft 365 for the web application that state has been popped from the HTML5 History API to which the application should navigate using the URL. This message should be triggered from an `onpopstate` listener in the host page.

### Values

### Url *\(string\)*

The URL associated with the popped history state.

### State *\(JSON-formatted object\)*

The data associated with the state.

### Example message

```json
{
    "MessageId": "App_PopState",
    "SendTime": 1329014075000,
    "Values": {
        "Url": "https://www.contoso.com/abc123/contents?wdtarget=pagexyz",
        "State": {
            "Value": 0
        }
    }
}
```

### Blur\_Focus

The `Blur_Focus` message signals the Microsoft 365 for the web application to stop aggressively grabbing focus. Hosts should send this message whenever the host application UI is drawn over the Microsoft 365 for the web frame, so that the Microsoft 365 application doesn't interfere with the UI behavior of the host.

This message only affects Microsoft 365 for the web edit modes. It doesn't affect view modes.

Tip

When the host application displays UI over Microsoft 365 for the web, it should put a full-screen dimming effect over the Microsoft 365 for the web UI, so that it's clear that the Microsoft 365 application isn't interactive.

### Values

*Empty.*

### Example Message

```json
{
    "MessageId": "Blur_Focus",
    "SendTime": 1329014075000,
    "Values": { }
}
```

### CanEmbed

The `CanEmbed` message is sent by the host in response to a request to create a [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl) using the `UI_FileEmbed` message.

### Values

### HostEmbeddedViewUrl *\(string\)*

A URI to a web page that provides access to a viewing experience for the file that can be embedded in another HTML page. This string is equivalent to the [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl) in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

### Example message

```json
{
    "MessageId": "CanEmbed",
    "SendTime": 1329014075000,
    "Values": {
        "HostEmbeddedViewUrl": "https://www.contosodrive.com/documents/1234/embedded/"
    }
}
```

### Grab\_Focus

The `Grab_Focus` message signals the Microsoft 365 for the web application to resume aggressively grabbing focus. Hosts should send this message whenever the host application UI that's drawn over the Microsoft 365 for the web frame is closing. This lets the Microsoft 365 application resume functioning.

This message only affects Microsoft 365 for the web edit modes. It doesn't affect view modes.

### Values

*Empty.*

### Example message

```json
{
    "MessageId": "Grab_Focus",
    "SendTime": 1329014075000,
    "Values": { }
}
```

### Host\_IsFrameTrusted

The `Host_IsFrameTrusted` message is sent by the host in response to `App_IsFrameTrusted` message.

### Values

### isTopFrameTrusted *\(boolean\)*

A boolean value indicating whether the top frame is trusted.

### Example message

```json
{
    "MessageId": "Host_IsFrameTrusted",
    "SendTime": 1329014075000,
    "Values": {
        "isTopFrameTrusted": true
    }
}
```

### Host\_PerfTiming

Provides performance related timestamps from the host page. Hosts should send this message when the Microsoft 365 for the web frame is created so load performance can be more accurately tracked.

### Values

### Click *\(integer\)*

The timestamp, in ticks, when the user selected a link that launched the Microsoft 365 for the web application. For example, if the host exposed a link in its UI that launches an Microsoft 365 for the web application, this timestamp is the time the user originally selected that link.

### Iframe *\(integer\)*

The timestamp, in ticks, when the host created the Microsoft 365 for the web iframe at the time the user selected the link.

### HostFrameFetchStart *\(integer\)*

The result of the [PerformanceTiming.fetchStart](http://www.w3.org/TR/navigation-timing/#dom-performancetiming-fetchstart) attribute, if the browser supports the [W3C NavigationTiming API](http://www.w3.org/TR/navigation-timing/). If the NavigationTiming API isn't supported by the browser, this value must be 0.

### RedirectCount *\(integer\)*

The result of the [PerformanceNavigation.redirectCount](http://www.w3.org/TR/navigation-timing/#dom-performancenavigation-redirectcount) attribute, if the browser supports the [W3C NavigationTiming API](http://www.w3.org/TR/navigation-timing/). If the NavigationTiming API isn't supported by the browser, this value must be 0.

### Example message

```json
{
    "MessageId": "Host_PerfTiming",
    "SendTime": 1329014075000,
    "Values": {
        "Click": 1329014074800,
        "Iframe": 1329014074950,
        "HostFrameFetchStart": 1329014074970,
        "RedirectCount": 1
    }
}
```

### Host\_PostmessageReady

Microsoft 365 for the web delay-loads much of its JavaScript code, including most of its PostMessage senders and listeners. You might choose to follow this pattern in your WOPI host page. So, your outer host page and the Microsoft 365 for the web iframe must coordinate to ensure that each is ready to receive and respond to messages.

To enable this coordination, Microsoft 365 for the web sends the `App_LoadingStatus` message only after all its message senders and listeners are available. In addition, Microsoft 365 for the web listens for the `Host_PostmessageReady` message from the outer frame. Until it receives this message, some UI, such as the `Share` button, is disabled.

Until your host page receives the `App_LoadingStatus` message, the Microsoft 365 for the web frame cannot respond to any incoming messages except `Host_PostmessageReady`. Microsoft 365 for the web does not delay-load its `Host_PostmessageReady` listener; it is available almost immediately upon iframe load.

If you're delay-loading your PostMessage code, ensure that your `App_LoadingStatus` listener is not delay-loaded. This ensures that you can receive the `App_LoadingStatus` message even if your other PostMessage code hasn't yet loaded.

Following is the typical flow:

1. Host page begins loading.
2. Microsoft 365 for the web frame begins loading. Some UI elements are disabled, because `Host_PostmessageReady` hasn't yet been sent by the host page.
3. Host page finishes loading and sends `Host_PostmessageReady`. No other messages are sent because the host page hasn't received the `App_LoadingStatus` message from the Microsoft 365 for the web frame.
4. Microsoft 365 for the web frame receives `Host_PostmessageReady`.
5. Microsoft 365 for the web frame finishes loading and sends `App_LoadingStatus` to host page.
6. Host page and Microsoft 365 for the web communicate by using other PostMessage messages.

### Values

*Empty.*

### Example message

```json
{
    "MessageId": "Host_PostmessageReady",
    "SendTime": 1329014075000,
    "Values": { }
}
```

## Listening to messages from the Microsoft 365 for the web iframe

The Microsoft 365 for the web iframe sends messages to the host page. On the receiving end, the host page receives a MessageEvent. The origin property of the MessageEvent is the origin of the message, and the data property is the message being sent. The following code example shows how you might consume a message.

```javascript
function handlePostMessage(e) {
    // The actual message is contained in the data property of the event.
    var msg = JSON.parse(e.data);

    // The message ID is now a property of the message object.
    var msgId = msg.MessageId;

    // The message parameters themselves are in the Values
    // parameter on the message object.
    var msgData = msg.Values;

    // Do something with the message here.
}
window.addEventListener('message', handlePostMessage, false);
```

The host page receives the following messages, all others are ignored:

- `App_LoadingStatus`
- `App_PushState`
- `Edit_Notification`
- `File_Rename`
- `UI_Close`
- `UI_Edit`
- `UI_FileEmbed`
- `UI_FileVersions`
- `UI_Sharing`
- `UI_Workflow`

### Common values

In addition to message-specific values passed with each message, Microsoft 365 for the web sends the following common values with every outgoing PostMessage:

### ui-language *\(string\)*

The LCID of the language Microsoft 365 for the web was loaded in. This value won't match the value provided using the [UI\_LLCC](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#ui_llcc) placeholder. Instead, this value is the numeric LCID value \(as a string\) that corresponds to the language used. For mor einformation, see [What languages does Microsoft 365 for the web support?](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/languages).

This value might be needed in the event that Microsoft 365 for the web renders using a language different than the one requested by the host. This might occur if Microsoft 365 for the web isn't localized in the language requested. In that case, the host might choose to draw its own UI in the same language that Microsoft 365 for the web used.

### wdUserSession *\(string\)*

The ID of the Microsoft 365 for the web session. This value is logged by the host and used when [troubleshooting](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/troubleshooting) issues with Microsoft 365 for the web. For more information on this value, see [Session IDs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/troubleshooting#session-ids).

### App\_IsFrameTrusted

The `App_IsFrameTrusted` message posts by the Microsoft 365 for the web application frame to initiate handshake flow. The host is expected to check whether the top frame is trusted and post `Host_IsFrameTrusted` message back to Microsoft 365 for the web application. The host first needs to include a query string: `&sftc=1` to url of POST request sent to Microsoft 365 for the web application, to indicate to Microsoft 365 for the web application that the host supports frame trust post Message.

`sftc` stands for *SupportsFrameTrustedPostMessage*. Only when `&sftc` is included in the query string, will the `App_IsFrameTrusted` message be posted by Microsoft 365 for the web application frame to initiate handshake flow.

### Values

[Common values](#common-values) only.

### Example Message

```json
{
    "MessageId": "App_IsFrameTrusted",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### App\_LoadingStatus

The `App_LoadingStatus` message posts after the Microsoft 365 for the web application frame has loaded. Until the host receives this message, it must assume that the Microsoft 365 for the web frame can't react to any incoming messages except `Host_PostmessageReady`.

### Values

### DocumentLoadedTime *\(long\)*

The time that the frame was loaded.

### Example message

```json
{
    "MessageId": "App_LoadingStatus",
    "SendTime": 1329014075000,
    "Values": {
        "DocumentLoadedTime": 1329014074983,
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### App\_PushState

### OneNote for the web

Note

This message is only used by OneNote for the web and isn't required to integrate with Microsoft 365 for the web or Microsoft 365 for mobile. It's included for completeness but doesn't need to be implemented.

OneNote for the web integration isn't included in the Microsoft 365 - Cloud Storage Partner Program.

The `App_PushState` message posts when the user changes the state of Microsoft 365 for the web application in such a way as to return to it later, requesting to capture it in the HTML 5 History API. In receiving this message, the Host page should use `history.pushState` to capture the state for a potential later state pop.

To send this message, the [AppStateHistoryPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#appstatehistorypostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web doesn't send the message.

### Values

### Url *\(string\)*

The URL associated with the message.

### State *\(JSON-formatted object\)*

The data associated with the state.

### Example message

```json
{
    "MessageId": "App_PushState",
    "SendTime": 1329014075000,
    "Values": {
        "Url": "https://www.contoso.com/abc123/contents?wdtarget=pagexyz",
        "State": {
            "Value": 0
        },
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### Edit\_Notification

The `Edit_Notification` message posts when the user first makes an edit to a document, and every five minutes thereafter, if the user has made edits in the previous five minutes. Hosts can use this message to gauge whether users are interacting with Microsoft 365 for the web. In coauthoring sessions, hosts can't use the WOPI calls for this purpose.

To send this message, the [EditNotificationPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editnotificationpostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web won't send this message.

### Values

[Common values](#common-values) only.

### Example message

```json
{
    "MessageId": "Edit_Notification",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### File\_Rename

The `File_Rename` message posts when the user renames the current file in Microsoft 365 for the web. The host can use this message to optionally update the UI, such as the title of the page.

Note

If the host doesn't return the [**SupportsRename**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsrename) parameter in their [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response, the rename UI won't be available in Microsoft 365 for the web.

### Values

### NewName *\(string\)*

The new name of the file.

### Example message

```json
{
    "MessageId": "File_Rename",
    "SendTime": 1329014075000,
    "Values": {
        "NewName": "Renamed Document",
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### UI\_Close

The `UI_Close` message posts when the Microsoft 365 for the web application is closing, either due to an error or a user action. Typically, the URL specified in the [CloseUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#closeurl) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response is displayed. However, hosts can intercept this message instead and navigate in an appropriate way.

To send this message, the [ClosePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#closepostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web won't send this message.

### Values

[Common values](#common-values) only.

### Example message

```json
{
    "MessageId": "UI_Close",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### UI\_Edit

The `UI_Edit` message posts when the user activates the *Edit* UI in Microsoft 365 for the web. This UI is only visible when using the `view` action.

To send this message, the [EditModePostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#editmodepostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web won't send this message and redirects the inner iframe to an edit action URL instead.

Hosts can choose to use this message in cases where they want more control over the user’s transition to edit mode. For example, a host might wish to prompt the user for some additional host-specific information before navigating.

### Values

[Common values](#common-values) only.

### Example message

```json
{
    "MessageId": "UI_Edit",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### UI\_FileEmbed

The `UI_FileEmbed` message posts when the user activates the *Embed* UI in Microsoft 365 for the web. The host should use this message to trigger the creation of a [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl), which the host then passes back to the WOPI client using the `CanEmbed` message.

To send this message, the [FileEmbedCommandPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#fileembedcommandpostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`, and [FileEmbedCommandUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileembedcommandurl) must be provided. Otherwise, Microsoft 365 for the web won't send this message.

Also, Microsoft 365 for the web won't send the message if a [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl) is provided in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response. In this case, since a [HostEmbeddedViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostembeddedviewurl) is already provided, there's no need to retrieve it from the host via PostMessage.

### Values

[Common values](#common-values) only.

### Example message

```json
{
    "MessageId": "UI_FileEmbed",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "en-us"
    }
}
```

### UI\_FileVersions

The `UI_FileVersions` message posts when the user activates the *Previous Versions* UI in Microsoft 365 for the web. The host should use this message to trigger any custom file version history UI.

To send this message, the [FileVersionPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#fileversionpostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web won't send this message.

### Values

[Common values](#common-values) only.

### Example message

```json
{
    "MessageId": "UI_FileVersions",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### UI\_Sharing

The `UI_Sharing` message posts when the user activates the *Share* UI in Microsoft 365 for the web. The host should use this message to trigger any custom sharing UI.

To send this message, the [FileSharingPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#filesharingpostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web won't send this message.

### Values

[Common values](#common-values) only.

### Example message

```json
{
    "MessageId": "UI_Sharing",
    "SendTime": 1329014075000,
    "Values": {
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```

### UI\_Workflow

The UI\_Workflow message posts when the user activates the `Workflow` UI in Microsoft 365 for the web. The host should use this message to trigger any custom workflow UI.

To send this message, the [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response from the host must be set to `true`. Otherwise, Microsoft 365 for the web won't send this message.

### Values

### WorkflowType *\(string\)*

The [WorkflowType](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowtype) associated with the message. This matches one of the values provided by the host in the [WorkflowType](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#workflowtype) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

### Example message

```json
{
    "MessageId": "UI_Workflow",
    "SendTime": 1329014075000,
    "Values": {
        "WorkflowType": "Submit",
        "wdUserSession": "3692f636-2add-4b64-8180-42e9411c4984",
        "ui-language": "1033"
    }
}
```
