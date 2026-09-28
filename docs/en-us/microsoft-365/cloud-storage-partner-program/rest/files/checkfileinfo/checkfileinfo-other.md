<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other -->
<!-- Sitemap-Last-Modified: 2023-03-09 -->

# CheckFileInfo - Other properties

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

## Miscellaneous Properties

#### AllowAdditionalMicrosoftServices

A **Boolean** value that indicates a WOPI client may connect to Microsoft services to provide end-user functionality.

In Office for the web, setting this property to `true` enables the following features:

- Bing spelling and proofing - Office for the web will use the [Bing Spell Check API](https://www.microsoft.com/cognitive-services/en-us/bing-spell-check-api) to provide better spelling and proofing suggestions for supported languages.
- Smart Lookup - Office for the web will use Bing to power the [Smart Lookup](https://support.office.microsoft.com/article/Get-insights-into-what-you-re-working-on-with-Smart-Lookup-debf2083-5ac0-4739-8667-ae2467bec044) feature, which provides quick access to definitions, Wiki articles, and top related searches from the web.

Additional features might be added in the future.

#### AllowErrorReportPrompt

A **Boolean** value that indicates that in the event of an error, the WOPI client is permitted to prompt the user for permission to collect a detailed report about their specific error. The information gathered could include the user’s file and other session-specific state.

Tip

This value should be omitted \(or explicitly set to `false`\) if no additional collection should be done on errors, or if the user has opted out of telemetry collection.

#### AllowExternalMarketplace

A **Boolean** value that indicates a WOPI client may allow connections to external services referenced in the file \(for example, a marketplace of embeddable JavaScript apps\).

#### ClientThrottlingProtection

A **string** value offering guidance to the WOPI client as to how to differentiate client throttling behaviors between the user and documents combinations from the WOPI host. Under times of stress, the WOPI client may choose to make use of this field to vary the level of impact of client side throttling behaviors within the set of active host documents. If the WOPI client chooses to differentiate throttling of client behaviors that are not necessarily tied to WOPI calls to the host, it may apply the most reduced quality of service to the LeastProtected document/users and the least reduced quality of service to the MostProtected documents/users. As in the case of [RequestedCallThrottling](#requestedcallthrottling), it is advised that hosts sharing this value between responses for distinct users of the same document at any given time may yield more deterministic results from the clients.  
  


| ***Possible Values*** | ***Description*** |
| --- | --- |
| **MostProtected** | The most protected documents/users. |
| **Protected** | The documents/users that should be protected more than the average ones. |
| **Normal** | The documents/users with the standard level of protection from throttling. |
| **LessProtected** | The documents/users that can be throttled more heavily than a typical than the average ones. |
| **LeastProtected** | The least protected documents/users. |

If no value is specified, or an invalid value is provided, the default behavior is to assume the WOPI host intended the value of None.

#### CloseButtonClosesWindow

A **Boolean** value that indicates the WOPI client should close the window or tab when the user activates any `Close` UI in the WOPI client.

Tip

This property may not behave as expected in Office for the web.

Note

[**Why should I avoid using the CloseButtonClosesWindow property in Office for the web?**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/close-button-closes-window)

#### CopyPasteRestrictions

Note

Pre-release property - not yet used by any WOPI client

A **string** value indicating whether the WOPI client should disable Copy and Paste functionality within the application. The default is to permit all Copy and Paste functionality, i.e. the setting has no effect.  
  


| ***Possible Values*** | ***Description*** |
| --- | --- |
| **BlockAll** | Copy and Paste are completely disabled within the application. |
| **CurrentDocumentOnly** | Copy and Paste are enabled but content can only be copied and pasted within the file currently open in the application. |

Any values other than those listed above must be ignored by the WOPI client.

Tip

This property is only respected by Excel for the web. It has no effect in PowerPoint for the web or Word for the web.

#### DisablePrint

A **Boolean** value that indicates the WOPI client should disable all print functionality.

#### DisableTranslation

A **Boolean** value that indicates the WOPI client should disable all machine translation functionality.

#### FileExtension

A **string** value representing the file extension for the file. This value must begin with a .. If provided, WOPI clients will use this value as the file extension. Otherwise the extension will be parsed from the [BaseFileName](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#basefilename).

Tip

While this property is not required, hosts should set it rather than relying on the [**BaseFileName**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#basefilename) parsing.

#### FileNameMaxLength

An **integer** value that indicates the maximum length for file names that the WOPI host supports, excluding the file extension. The default value is 250. Note that WOPI clients will use this default value if the property is omitted or if it is explicitly set to 0.

Tip

This property is optional; however, hosts wishing to enable file renaming within Office for the web should verify that the default value is appropriate and set it accordingly if not. See the [**RenameFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile) operation for more details.

#### LastModifiedTime

A **string** that represents the last time that the file was modified. This time must always be a must be a UTC time, and must be formatted in ISO 8601 round-trip format. For example, `"2009-06-15T13:45:30.0000000Z"`.

#### RequestedCallThrottling

A **string** value indicating whether the WOPI host is experiencing capacity problems and would like to reduce the frequency at which the WOPI clients make calls to the host. Each WOPI application may choose how best to respect the expressed desire from the host. WOPI applications may respond in manners such as reducing the frequency of CheckFileInfo calls and extending the window between when a user makes a change and the updated document gets saved back to the WOPI host. It is advised that hosts sharing this value between responses for distinct users of the same document at any given time may yield more deterministic results from the clients.  
  


| ***Possible Values*** | ***Description*** |
| --- | --- |
| **Normal** | The WOPI host is healthy and does not want any additional request throttling. |
| **Minor** | The WOPI host is requesting a small amount of throttling from the WOPI client. |
| **Medium** | The WOPI host is requesting a medium amount of throttling from the WOPI client. |
| **Major** | The WOPI host is requesting a large amount of throttling from the WOPI client. |
| **Critical** | The WOPI host is requesting the WOPI client to apply the largest amount of throttling possible. |

If no value is specified, or an invalid value is provided, the default behavior is to assume the WOPI host intended the value of None.

#### SHA256

A 256 bit SHA-2-encoded \[[FIPS 180-2](http://csrc.nist.gov/publications/fips/fips180-2/fips180-2.pdf)\] hash of the file contents, as a Base64-encoded string. Used for caching purposes in WOPI clients.

Tip

See [**Optimizing document viewing for high volume**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/performance) for more details on how this property is used in Office for the web.

#### SharingStatus

Note

Pre-release property - not yet used by any WOPI client

A **string** value indicating whether the current document is shared with other users. The value can change upon adding or removing permissions to other users. Clients should use this value to help decide when to enable collaboration features as a document must be Shared in order to multi-user collaboration on the document.  
  


| ***Possible Values*** | ***Description*** |
| --- | --- |
| **Private** | Only the document owner has permission to the file. |
| **Shared** | At least one other user has access to the file via direct permissions or a sharing link. |

If no value is specified, or an invalid value is provided, the default behavior is to assume the WOPI host intended the value of None.

#### TemporarilyNotWritable

A **Boolean** value that indicates that if host is temporarily unable to process writes on a file

#### UniqueContentId

🔒 `Not supported in CSPP`

In special cases, a host may choose to not provide a [SHA256](#sha256), but still have some mechanism for identifying that two different files contain the same content in the same manner as the [SHA256](#sha256) is used.

This string value can be provided rather than a [SHA256](#sha256) value if and only if the host can guarantee that two different files with the same content will have the same UniqueContentId value.

Tip

See [**Optimizing document viewing for high volume**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/performance) for more details on how this property is used in Office for the web.

## Unused and future properties

The following properties are defined as valid CheckFileInfo response properties. However, they are not used, either because they are pending deprecation or they are designated for future features of WOPI clients and WOPI servers.

#### ClientUrl

A user-accessible URI directly to the file intended for opening the file through a client. Can be a DAV URL \([RFC 5323](https://tools.ietf.org/html/rfc5323.html)\), but may be any URL that can be handled by a client that can open a file of the given type.

#### CobaltCapabilities

A **array of strings** that contains the Cobalt capabilities supported by the host. If [SupportsCobalt](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportscobalt) is set to `false`, this property must be ignored by the WOPI client. Any value other than the possible values listed below must be ignored by the WOPI client.  
  


| ***Possible Values*** | ***Description*** |
| --- | --- |
| **DownloadStreaming** | This type of CobaltCapabilities indicates the host supports Cobalt streaming for download at the moment it handles the request. |

#### DisableBrowserCachingOfUserContent

A **Boolean** value that indicates that the WOPI client should disable caching of file contents in the browser cache. Note that this has important performance implications for web browser-based WOPI clients.

#### EditAndReplyUrl

Not yet documented.

#### HostAuthenticationId

A **string** value uniquely identifying the user currently accessing the file.

Warning

This property should not be used. Hosts should use the [UserId](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#userid) property instead.

#### HostEmbeddedEditUrl

A URI to a web page that provides access to an editing experience for the file that can be embedded in another HTML page. For example, a page that provides an HTML snippet that can be inserted into the HTML of a blog.

#### HostNotes

A **string** that is used by the host to pass arbitrary information to the WOPI client. The client must ignore this string if it does not recognize its contents. A host must not require that a client understand the contents of this string to operate.

#### HostRestUrl

A URI that is the base URI for REST operations for the file.

#### IrmPolicyDescription

A **string** that the WOPI client should display to the user indicating the IRM policy for the file. This value should be combined with [IrmPolicyTitle](#irmpolicytitle).

#### IrmPolicyTitle

A **string** that the WOPI client should display to the user indicating the IRM policy for the file. This value should be combined with [IrmPolicyDescription](#irmpolicydescription).

#### PresenceProvider

A **string** that identifies the provider of information that a WOPI client may use to discover information about the user’s online status \(for example, whether a user is available via instant messenger\).

#### PresenceUserId

A **string** that identifies the user in the context of the [PresenceProvider](#presenceprovider).

#### ProtectInClient

A **Boolean** value that indicates that the WOPI client should take measures to prevent copying and printing of the file. This is intended to help enforce IRM.

#### SignInUrl

A URI that will allow the user to sign in using the host’s authentication system. This property can be used when supporting anonymous users. If this property is not provided, no sign in UI will be shown in Office for the web.

#### SignoutUrl

A URI that will sign the current user out of the host’s authentication system.

#### SupportsFileCreation

A **Boolean** value that indicates that the host supports creating new files using the WOPI client.

#### SupportsScenarioLinks

A **Boolean** value that indicates that the host supports scenarios where users can operate on files in limited ways via restricted URLs.

#### SupportsSecureStore

A **Boolean** value that indicates that the host supports calls to a secure data store utilizing credentials stored in the file.

#### TenantId

A **string** value uniquely identifying the user’s ‘tenant,’ or group/organization to which they belong.

Caution

The presence of this property does not remove the uniqueness and consistency requirements listed above. User properties are expected to be unique per user and consistent over time regardless of the presence of a [TenantId](#tenantid).

#### TimeZone

A **string** that is used to pass time zone information to a WOPI client. The format of this value is determined by the host.

#### UserPrincipalName

A **string** value uniquely identifying the user currently accessing the file.

#### WebEditingDisabled

A **Boolean** value that indicates that the WOPI client must not allow the user to edit the file.

Note

This does not mean that the user doesn’t have rights to edit the file. Hosts should use the [**UserCanWrite**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercanwrite) property for that purpose.

## Breadcrumb properties

**Breadcrumb** properties are used by some WOPI clients to display breadcrumb-style navigation elements within the WOPI client UI.

#### BreadcrumbBrandName

A **string** that indicates the brand name of the host.

#### BreadcrumbBrandUrl

A URI to a web page that the WOPI client should navigate to when the user clicks on UI that displays [BreadcrumbBrandName](#breadcrumbbrandname).

#### BreadcrumbDocName

A **string** that indicates the name of the file. If this is not provided, WOPI clients may use the [BaseFileName](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#basefilename) value.

#### BreadcrumbFolderName

A **string** that indicates the name of the container that contains the file.

#### BreadcrumbFolderUrl

A URI to a web page that the WOPI client should navigate to when the user clicks on UI that displays [BreadcrumbFolderName](#breadcrumbfoldername).

## Workflow properties

Warning

This documentation is for an upcoming feature and may undergo dramatic changes prior to final release. Pre-release features are available in the [Test environment](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/environments#test-environment) only.

#### WorkflowType

Note

Pre-release property - not yet used by any WOPI client

An **array of strings** containing the workflow types available for the document. Possible values are:

- `Assign`
- `Submit`

This property must always be specified if [WorkflowUrl](#workflowurl) or [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) are provided. If this property is not supplied, then both [WorkflowUrl](#workflowurl) and [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) must be ignored by the WOPI client.

Conversely, if the WorkflowType property is provided but neither [WorkflowUrl](#workflowurl) nor [WorkflowPostMessage](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#workflowpostmessage) are provided, then the WorkflowType value must be ignored by the WOPI client.

Important

While this property is an array of strings, note that specific values of WorkflowType may be mutually exclusive depending on the WOPI client. WOPI clients must use the following guidelines when handling values in the WorkflowType array:

- If no supported values are provided, the WOPI client must behave as though the WorkflowType property was not provided.
- If multiple values are provided and the WOPI client does not support multiple values, the client may use the first supported value provided in the array or behave as though the WorkflowType property was not provided.

#### WorkflowUrl

Note

Pre-release property - not yet used by any WOPI client

A URI to a location that allows the user to participate in a workflow for the file.

Important

This value will be ignored if [**WorkflowType**](#workflowtype) is not provided.

## Deprecated properties

The following properties are deprecated and should no longer be used by WOPI clients or servers.

| Property | Deprecated since version |
| --- | --- |
| **BreadcrumbDocUrl** | 2014.06.01 |
| **EditingCannotSave** | 2014.06.01 |
| **HostName** | 2016.01.12 |
| **PrivacyUrl** | 2015.06.01 |
| **TermsOfUseUrl** | 2015.06.01 |
