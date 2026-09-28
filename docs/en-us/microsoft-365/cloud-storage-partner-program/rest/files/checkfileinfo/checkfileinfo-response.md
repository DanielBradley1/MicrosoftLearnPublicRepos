<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response -->
<!-- Sitemap-Last-Modified: 2023-03-09 -->

# CheckFileInfo - Response properties

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The response to a `CheckFileInfo` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing a number of properties, most of which are optional.

All optional values default to the following values based on their type:

| Type | Default value |
| --- | --- |
| Boolean | `false` |
| String | The empty string |
| Integer/Long | Varies; see individual properties for details |
| Array | Empty array |

Important

No properties should be set to `null`. If you don't wish to set a property, omit it from the response and WOPI clients will use the default value.

## Required response properties

The following properties must be present in all `CheckFileInfo` responses:

#### BaseFileName

The **string** name of the file, including extension, without a path. Used for display in user interface \(UI\), and determining the extension of the file.

#### OwnerId

A **string** that uniquely identifies the owner of the file. In most cases, the user who uploaded or created the file is considered the owner.

Important

This ID is subject to uniqueness and consistency requirements. For more information, see [**Requirements for user identity properties**](#requirements-for-user-identity-properties).

#### Size

The size of the file in bytes, expressed as a **long**, a 64-bit signed integer.

#### UserId

A **string** value uniquely identifying the user currently accessing the file.

Important

This ID is subject to uniqueness and consistency requirements. See [**Requirements for user identity properties**](#requirements-for-user-identity-properties) for more information.

#### Version

The current version of the file based on the server's file version schema, as a **string**. This value must change when the file changes, and version values must never repeat for a given file.

Important

This value must be a **string**, even if numbers are used to represent versions.

### Requirements for user identity properties

Hosts use the [OwnerId](#ownerid) and [UserId](#userid) properties to provide user ID data to WOPI clients. User identity properties are intended for telemetry purposes, and thus should not be shown in any WOPI client UI. These properties must meet the following requirements:

- Unique to a single user.
- Consistent over time. For example, if a particular user uses a WOPI client to view a document on Monday, then returns and views another document on Tuesday, the value of the user identity properties should match.

Important

Hosts must only use alphanumeric \(A-Z, a-z, and 0-9\) characters in user identity properties.

## WOPI host capabilities properties

The WOPI host capabilities properties indicate to the WOPI client what WOPI capabilities that the host supports for a file. All of these properties are optional and thus default to `false`; hosts should set them to `true` if their WOPI implementation meets the requirements for a particular property.

Important

If a WOPI server sets any capabilities properties to `true`, WOPI clients assume that all of the operations represented by that capability property are supported. So, a WOPI host must implement all operations represented by that capability property if they set the property to `true`.

#### SupportedShareUrlTypes

An **array** of strings containing the [Share URL](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#share-url) types supported by the host.

These types are passed in the **X-WOPI-UrlType** request header to signify which Share URL type to return for the [GetShareUrl \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getshareurl#getshareurl-files) operation.

| ***Possible Values*** | ***Description*** |
| --- | --- |
| **ReadOnly** | This type of Share URL allows users to view the file using the URL, but does not give them permission to edit the file. |
| **ReadWrite** | This type of Share URL allows users to both view and edit the file using the URL. |

#### SupportsCobalt

A **Boolean** value that indicates that the host supports the following WOPI operations:

- [ExecuteCellStorageRequest](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/onenote)
- [ExecuteCellStorageRelativeRequest](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/onenote)

#### SupportsContainers

A **Boolean** value that indicates that the host supports the following WOPI operations:

- [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo)
- [CreateChildContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildcontainer)
- [CreateChildFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildfile#createchildfile)
- [DeleteContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/deletecontainer#deletecontainer)
- [DeleteFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/deletefile)
- [EnumerateAncestors \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumerateancestors)
- [EnumerateAncestors \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/enumerateancestors#enumerateancestors-files)
- [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren)
- [GetEcosystem \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getecosystem#getecosystem-containers)
- [RenameContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/renamecontainer#renamecontainer)

Tip

SupportsContainers is a superset of [**SupportsDeleteFile**](#supportsdeletefile). However, WOPI hosts should explicitly return `true` for both properties if SupportsContainers is `true`.

#### SupportsDeleteFile

A **Boolean** value that indicates that the host supports the [DeleteFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/deletefile) operation.

#### SupportsEcosystem

A **Boolean** value that indicates that the host supports the following WOPI operations:

- [CheckEcosystem](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/checkecosystem)
- [GetEcosystem \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getecosystem#getecosystem-containers)
- [GetEcosystem \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getecosystem)
- [GetRootContainer \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer)

#### SupportsExtendedLockLength

A **Boolean** value that indicates that the host supports lock IDs up to 1024 ASCII characters long. If not provided, WOPI clients will assume that lock IDs are limited to 256 ASCII characters.

Important

While the 256 ASCII character lock length is currently sufficient, longer lock IDs will likely be required to support future scenarios, so we recommend hosts support extended lock lengths as soon as possible. See [**lock ID lengths**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#lock-length) for more information.

#### SupportsFolders

A **Boolean** value that indicates that the host supports the following WOPI operations:

- [CheckFolderInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/onenote),
- [EnumerateChildren \(folders\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/onenote)
- [DeleteFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/deletefile)

#### SupportsGetFileWopiSrc

A **Boolean** value that indicates that the host supports the [🚧 GetFileWopiSrc \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getfilewopisrc) operation.

#### SupportsGetLock

A **Boolean** value that indicates that the host supports the [GetLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getlock#getlock) operation.

#### SupportsLocks

A **Boolean** value that indicates that the host supports the following WOPI operations:

- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock),
- [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock)
- [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock)
- [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock) operations for this file.

#### SupportsRename

A **Boolean** value that indicates that the host supports the [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile) operation.

#### SupportsUpdate

A **Boolean** value that indicates that the host supports the following WOPI operations:

- [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)
- [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile)

#### SupportsUserInfo

A **Boolean** value that indicates that the host supports the [PutUserInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putuserinfo#putuserinfo) operation.

## User metadata properties

The following properties are used to provide additional information about users.

#### IsAnonymousUser

A **Boolean** value indicating whether the user is authenticated with the host or not. Hosts should always set this to `true` for unauthenticated users, so that clients are aware that the user is anonymous.

When setting this to `true`, hosts can choose to omit the [UserId](#userid) property, but must still set the [OwnerId](#ownerid) property.

#### IsEduUser

A **Boolean** value indicating whether the user is an education user or not.

#### LicenseCheckForEditIsEnabled

A **Boolean** value indicating whether the user is a business user or not.

Note

For information about supporting document editing for business users, visit [Managing Microsoft 365 user licenses](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business).

#### UserFriendlyName

A **string** that is the name of the user, suitable for displaying in UI.

#### UserInfo

A **string** value containing information about the user. This string can be passed from a WOPI client to the host by means of a [PutUserInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putuserinfo#putuserinfo) operation. If the host has a UserInfo string for the user, they must include it in this property. See the [PutUserInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putuserinfo#putuserinfo) documentation for more details.

## User permissions properties

A WOPI client must always assume that users have limited permissions to documents. If a host does not set the appropriate user permissions properties, users will not be able to perform operations such as editing documents using a WOPI client.

Ultimately, the host has final control over whether WOPI operations attempted by the client should succeed or fail based on the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) provided in the WOPI request. Thus, these properties do not act as an authorization mechanism. Rather, these properties help WOPI clients tailor their UI and behavior to the specific permissions a user has. For example, a WOPI client can hide file renaming UI if the [UserCanRename](#usercanrename) property is `false`.

However, a WOPI client expects that even if that UI were somehow made available to a user without appropriate permissions, the WOPI [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile) request would fail since the host would determine the action was not permissible based on the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) passed in the request.

Note that there is no property that indicates the user has permission to read/view a file. This is because WOPI requires the host to respond to any WOPI request, including CheckFileInfo, with a [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) or [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) if the access token is invalid or expired.

#### ReadOnly

A **Boolean** value that indicates that, for this user, the file cannot be changed.

#### RestrictedWebViewOnly

A **Boolean** value that indicates that the WOPI client should restrict what actions the user can perform on the file. The behavior of this property is dependent on the WOPI client.

#### UserCanAttend

A **Boolean** value that indicates that the user has permission to view a [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) of this file.

#### UserCanNotWriteRelative

A **Boolean** value that indicates the user does not have sufficient permission to create new files on the WOPI server. Setting this to `true` tells the WOPI client that calls to [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) will fail for this user on the current file.

#### UserCanPresent

A **Boolean** value that indicates that the user has permission to [broadcast](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#broadcast) this file to a set of users who have permission to broadcast or view a broadcast of the current file.

#### UserCanRename

A **Boolean** value that indicates the user has permission to rename the current file.

#### UserCanWrite

A **Boolean** value that indicates that the user has permission to alter the file. Setting this to `true` tells the WOPI client that it can call [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) on behalf of the user.

## File URL properties

Hosts can return a number of URLs for the file that WOPI clients may navigate to in various scenarios.

Tip

These properties can be used to customize the user experience of the Office for the web applications. See [Customize Microsoft 365 for the web with CheckFileInfo properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#customize-microsoft-365-for-the-web-with-checkfileinfo-properties) for more information about how each property is used in Microsoft 365 for the web.

#### CloseUrl

A URI to a web page that the WOPI client should navigate to when the application closes, or in the event of an unrecoverable error.

#### DownloadUrl

A user-accessible URI to the file intended to allow the user to download a copy of the file.

Important

This URI should directly download the file. In other words, WOPI clients expect that when directing users to this URL, the file will be immediately downloaded. This URL should not direct the user to some separate UI to download the file.

Important

This URI should always provide the most recent version of the file.

#### FileEmbedCommandUrl

A URI to a location that allows the user to create an embeddable URI to the file.

#### FileSharingUrl

A URI to a location that allows the user to share the file.

#### FileUrl

A URI to the file location that the WOPI client uses to get the file. If this is provided, the WOPI client may use this URI to get the file instead of a [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile) request. A host might set this property if it is easier or provides better performance to serve files from a different domain than the one handling standard WOPI requests. WOPI clients must not add or remove parameters from the URL; no other parameters, including the [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token), should be appended to the FileUrl before it is used.

Important

The FileUrl is meant as a performance enhancement. The [**GetFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile) operation must still be supported for the file even when the FileUrl property is provided.

Note

Requests to the [**FileUrl**](#fileurl) can not be signed using [**proof keys**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys). The FileUrl is used exactly as provided by the host, so it does not necessarily include the access token, which is required to construct the expected proof.

#### FileVersionUrl

A URI to a location that lets the user view the version history for the file.

#### HostEditUrl

A URI to a [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#wopi-host--wopi-server) that loads the `edit` WOPI action.

#### HostEmbeddedViewUrl

A URI to a web page that provides access to a viewing experience for the file that can be embedded in another HTML page. This is typically a URI to a [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#wopi-host--wopi-server) that loads the `embedview` WOPI action.

#### HostViewUrl

A URI to a [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#wopi-host--wopi-server) that loads the view WOPI action. This URL is used by Office for the web to navigate between view and edit mode.

#### SignoutUrl

A URI that signs the current user out of the host’s authentication system.

Note

See also [**SignInUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#signinurl)
