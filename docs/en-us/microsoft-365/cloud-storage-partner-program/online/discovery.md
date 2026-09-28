<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# WOPI discovery

WOPI discovery is the process where a WOPI host identifies Microsoft 365 for the web capabilities and how to set up Microsoft 365 for the web applications within a site. WOPI hosts use the discovery XML to determine how to interact with Microsoft 365 for the web. The WOPI host should cache the data in the discovery XML. Although this XML doesn't change often, we recommend that you issue a request for the XML periodically to ensure you always have the latest version. 12-24 hours is a good cadence to refresh, although in practice it's updated much less frequently.

A more dynamic option is to re-run discovery when [proof key validation](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys) fails, or when it succeeds using the old key. That implies that the keys have been rotated, so discovery should definitely be re-run to get the new public key.

Lastly, another option is to run discovery whenever one of your machines restart. All these approaches, as well as combinations of them, have been used by hosts in the past. Whichever approach makes the most sense depends on your infrastructure.

Important

Hosts shouldn't rely on the [**Expires**](https://tools.ietf.org/html/rfc7234#section-5.3) HTTP header on the WOPI discovery URL to know when to re-run WOPI discovery. While this might change in the future, currently, the value in the [**Expires**](https://tools.ietf.org/html/rfc7234#section-5.3) header isn't appropriate for this purpose.

Tip

For more information on the URLs to retrieve discovery XML for Microsoft 365 for the web test and production environments, see [**WOPI discovery URLs**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#wopi-discovery-urls).

## WOPI discovery actions

The **action** element and its attributes in the discovery XML provides some important information about Microsoft 365 for the web.

| Element or attribute | Description |
| --- | --- |
| **action** element | Represents:  <br>  <br>• Operations that you can do on an Microsoft 365 document.  <br>• The file formats \(in the form of file extensions\) that are supported for the action. |
| **requires** attribute | The WOPI REST endpoints that are required to use the actions. |
| **urlsrc** attribute | The URI that you use to invoke the action on a particular file. |

The following example shows an **action** element in the Microsoft 365 for the web discovery XML:

```xml
<action name="edit" ext="docx" requires="locks,update"
        urlsrc="https://word-edit.officeapps.live.com/we/wordeditorframe.aspx?
        <ui=UI_LLCC&><rs=DC_LLCC&><showpagestats=PERFSTATS&>"/>
```

This example defines an action called `edit` that's supported for `docx` files. The edit action requires the `locks` and `update` capabilities. To invoke the edit action on a file, navigate to the URI included in the **urlsrc** attribute. You must parse the **urlsrc** value and add some parameters. For a full description of this process, see [Action URLs](#action-urls).

Note

Some actions aren't supported within the Microsoft 365 - Cloud Storage Partner Program. These operations are marked 🔒 `Not supported in the CSPP`.

## WOPI actions

All WOPI actions require hosts to implement [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [**GetFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile).

### view

An action that renders a non-editable view of a document.

### edit

An action that lets users edit a document.

Requires: `update`, `locks`

### editnew

An action that creates a new document using a blank file template appropriate to the file type, then opens that file for editing in Microsoft 365 for the web.

Requires: `update`, `locks`

### convert

An action that converts a document in a binary format, such as `doc`, into a modern format, like `docx`, so that it can be edited in Microsoft 365 for the web. For more information about this action, see [Editing binary document formats](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/conversion).

Requires: `update`, `locks`

### getinfo

An action that returns a set of URLs for running automated test cases. This action is only used by the [WOPI Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator) and is meant to be used in an [automated fashion](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator#automated-wopi-validation).

### interactivepreview

🔒 `Not supported in the CSPP`

An action that provides an interactive preview of the file type.

### mobileView

An action that renders a non-editable view of a document that's optimized for viewing on mobile devices such as smartphones.

Tip

Microsoft 365 for the web automatically redirects `view` to `mobileView` when needed, so typically hosts don't need to use this action directly.

### embedview

An action that renders a non-editable view of a document that's optimized for embedding in a web page.

### imagepreview\(\)

🔒 `Not supported in the CSPP`

An action that provides a static image preview of the file type.

### formsubmit

An action that supports accepting changes to the file type via a form-style interface. For example, a user might be able to use this action to change the content of a workbook even if they didn't have permission to use the `edit` action.

### formedit

An action that supports editing the file type in a mode better suited to working with files that have been used to collect form data via the `formsubmit` action.

### rest

An action that supports interacting with the file type via additional URL parameters that are specific to the file type in question.

### present

🔒 `Not supported in the CSPP`

An action that presents a [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) of a document.

### presentservice

🔒 `Not supported in the CSPP`

This action provides the location of a [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) endpoint for broadcast presenters. Interaction with the endpoint is described in [\[MS-OBPRS\]](https://msdn.microsoft.com/library/hh623172\(v=office.12\).aspx).

### attend

🔒 `Not supported in the CSPP`

An action that attends a [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) of a document.

### attendservice

🔒 `Not supported in the CSPP`

This action provides the location of a [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) endpoint for broadcast attendees. Interaction with the endpoint is described in [\[MS-OBPAS\]](https://msdn.microsoft.com/library/hh642267\(v=office.12\).aspx).

### preloadedit

An action to [preload static content](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/performance#preload-static-content) for Microsoft 365 for the web edit applications.

### preloadview

An action to [preload static content](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/performance#preload-static-content) for Microsoft 365 for the web view applications.

### syndicate

🔒 `Not supported in the CSPP`

### legacywebservice

🔒 `Not supported in the CSPP`

### rtc

🔒 `Not supported in the CSPP`

### collab

🔒 `Not supported in the CSPP`

### documentchat

🔒 `Not supported in the CSPP`

## Action requirements

The WOPI protocol exposes a number of different REST endpoints and operations that you can perform via those endpoints. You don’t have to implement all of these for all actions. Actions define their requirements as part of the discovery XML. The requirements themselves are groups of WOPI operations that must be supported in order for the action to work.

### update

Requires: [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile), [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile)

### locks

Requires: [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock), [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock), [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock), [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock)

## Action URLs

The URI values provided in the **urlsrc** attribute in the discovery XML aren't in a valid format. Simply navigating to them results in errors. A WOPI host must transform the URIs provided in order to make them valid action URLs that you can use to invoke actions on a file. To transform the **urlsrc** attribute into a proper action URL, the host must parse and replace [Placeholder values](#placeholder-values) with appropriate values or discard them completely.

After the URL is transformed, it's a valid URL. When the URL is opened, the action invokes against the file indicated by the [WOPISrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc).

### Transforming the urlsrc parameter

Some WOPI actions expose parameters that hosts can use to customize the behavior of the Microsoft 365 for the web application. For example, most actions support optional query string parameters that tell Microsoft 365 for the web what language to render the application UI in.

These parameters are exposed in the **urlsrc** attribute in the discovery XML. Each of these optional parameters are contained within angle brackets \(`<` and `>`\), and conform to the pattern `<name=PLACEHOLDER_VALUE[&]>`, where `name` is the name of the query string parameter and `PLACEHOLDER_VALUE` is a value that can be replaced by the host. By convention all placeholder values in Office for the web action URIs are capitalized.

The list of all placeholder values used by Microsoft 365 for the web and what values are valid replacements for each placeholder are listed in the [Placeholder values](#placeholder-values) section.

The placeholders are replaced as follows:

- If the `PLACEHOLDER_VALUE` is unknown to the host, the entire parameter, including the angle brackets, is removed.
- Similarly, if the `PLACEHOLDER_VALUE` is known but the host wishes to ignore it or use the default value for that parameter, you should remove the entire parameter, including the angle brackets.
- If the `PLACEHOLDER_VALUE` is known, the angle brackets are removed, the `name` value is left intact, and the `PLACEHOLDER_VALUE` string is replaced with an appropriate value. If present, you must keep the optional `&`.

The following section contains a list of all current placeholder values that Microsoft 365 for the web exposes in its discovery XML.

Note

Office for the web can add new placeholders and actions at any time. Hosts must ignore - and thus remove from the URL per the instructions above - any placeholder values they don’t explicitly understand.

### Placeholder values

The following are the placeholder values.

#### BUSINESS\_USER

You can set this value to `1` to indicate that the current user is a business user. This placeholder value must be used by hosts that support the business user flow. For more information, see [Managing Microsoft 365 user licenses](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business).

#### DC\_LLCC

This value represents the language that Microsoft 365 for the web should use for the purposes of data calculation. For a list of currently supported languages, see [What languages does Office for the web support?](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/languages)

In addition to the values provided in the Locale ID column, you can supply any language, provided it's in the format described in [**RFC 1766**](https://tools.ietf.org/html/rfc1766.html). Typically, this value is the same as the value provided for [UI\_LLCC](#ui_llcc), and defaults to that value if not provided.

#### DISABLE\_ASYNC

Note

This value is used in the `attend` action only.

You can set this value to `true` to prevent a [**broadcast**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) attendee from navigating a file independently.

#### DISABLE\_BROADCAST

Note

This value is used in [**broadcast**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast)-related actions only.

You can set this value to `true` to load a view of a document that doesn't start or join a [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) session. This view looks and behaves like a regular broadcast frame.

#### DISABLE\_CHAT

You can set this value to `1` to disable in-document chat functionality.

#### EMBEDDED

Note

This value is used in [**broadcast**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast)-related actions only.

You can set this value to `true` to indicate that the output of the action is embedded in a web page.

#### FULLSCREEN

Note

This value is used in [**broadcast**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast)-related actions only.

You can set this value to `true` to load the file type in full-screen mode.

#### HOST\_SESSION\_ID

This value is passed by hosts to associate an Microsoft 365 for the web session with a host session identifier. This helps Microsoft 365 for the web engineers more quickly find logs for troubleshooting purposes based on a host-specific session identifier.

#### RECORDING

Note

This value is used in [**broadcast**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast)-related actions only.

You can set this value to `true` to load the file type with a minimal user interface.

#### SESSION\_CONTEXT

You can replace this placeholder by any string value. If provided, this value is passed back to the host in subsequent [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [CheckFolderInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/onenote) calls in the **X-WOPI-SessionContext** request header. There is no defined limit for the length of this string; however, since it's passed on the query string, it's subject to the overall Microsoft 365 for the web URL length limit of 2048 bytes.

***New in version 2018.12.15:*** Prior to this version, session context was supported but hosts were required to add it to the action URL manually using the sc query parameter. This placeholder enables hosts to handle session context in the same way as other URL parameters.

#### THEME\_ID

Note

This value is used in [**broadcast**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast)-related actions only.

You can set this value to either `1` or `2` to designate a specific user interface appearance. `1` denotes a light-colored theme and `2` denotes a darker theme.

#### UI\_LLCC

This value represents the language the Microsoft 365 for the web application UI should use. Microsoft 365 for the web doesn't support all languages, and might use a substitute language if the language requested isn't supported. For a list of currently supported languages, see [What languages does Office for the web support?](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/languages).

In addition to the values provided in the Locale ID column, you can supply any language, provided it's in the format described in [**RFC 1766**](https://tools.ietf.org/html/rfc1766.html). If you don't set a value for this placeholder, Office for the web tries to use the browser language setting \(`navigator.language`\). If no valid language can be determined, Office for the web defaults to `en-US` \(US English\).

#### VALIDATOR\_TEST\_CATEGORY

Note

This value runs the [**WOPI Validator**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator) in different modes.

You can set this value to `All`, `OfficeOnline` or `OfficeNativeClient` to activate the tests specific to Office for the web and Microsoft 365 for mobile. If omitted, the default value is `All`.

`All`: activates all [WOPI Validator](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/validator) tests.

`OfficeOnline`: activates all tests necessary for Office for the web integration.

`OfficeNativeClient`: activates all tests necessary for Microsoft 365 for mobile integration.

#### WOPI\_SOURCE

This placeholder must be replaced by a [WopiSrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) value.

Important

Unlike other placeholders, replacing this placeholder is required.

***New in version 2018.12.15:*** Prior to this version, hosts were required to add the [WopiSrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) to the action URL for most \(but not all\) actions. This placeholder enables hosts to handle the [WopiSrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) in the same way as other URL parameters.

### Additional notes

Depending on the specific scenario where action URLs are invoked, there are additional relevant components to action URLs. Since action URLs are typically invoked from the host page, these are covered in the [Building a host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage) section.

## Favicon URLs

The discovery XML includes a URL to an appropriate [favicon](https://en.wikipedia.org/wiki/Favicon) for all Microsoft 365 for the web applications in the `favIconUrl` attribute of the `app` element. For example:

```xml
<app name="Excel"
     favIconUrl="https://excel.officeapps.live.com/x/_layouts/resources/FavIcon_Excel.ico"
     checkLicense="true">
    ...
</app>
```

Hosts should use this URL as the favicon for their host page, so that the appropriate application icon appears when Microsoft 365 for the web is used.
