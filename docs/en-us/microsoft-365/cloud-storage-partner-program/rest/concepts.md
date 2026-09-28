<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts -->
<!-- Sitemap-Last-Modified: 2025-02-10 -->

# Key concepts to understand for WOPI integration

The Web Application Open Platform Interface \(WOPI\) protocol is used by Microsoft 365 applications, such as Microsoft 365 for the web or Microsoft 365 for Mobile, to view and edit files that are stored in a cloud service. The following concepts are referred to throughout the Cloud Storage Partner Program documentation. Understanding these concepts is vital to understanding the requirements for integrating with WOPI clients.

## File ID

A File ID is a string that represents a file or folder being operated on by way of WOPI operations. A host must issue a unique ID for any file used by a WOPI client. The client will then include the file ID when making requests to the WOPI host. So, a host must be able to use the file ID to locate a particular file.

A file ID must:

- Represent a single file.
- Be a URL-safe string, because IDs are passed in URLs, principally via the [WOPISrc](#wopisrc) parameter.
- Remain the same when the file is edited.
- Remain the same when the file is moved or renamed.
- Remain the same when any ancestor container, including the parent container, is renamed.
- In the case of shared files, the ID for a given file must be the same for every user that accesses the file.

Note

The file ID isn't provided to a WOPI client directly. It's passed as part of the [**WOPISrc**](#wopisrc) value.

For more information on action URLs, see [Action URLs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-urls). For more information on how the file ID should be passed to Microsoft 365 for the web, see [WOPI\_SOURCE](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi_source).

## Access token

An access token is a string used by the host to determine the identity and permissions of the issuer of a WOPI request.

The WOPI host that stores the file has the information about user permissions, not the WOPI client. For this reason, the WOPI host must provide an access token that the client then passes back to it on subsequent WOPI requests. When the WOPI host receives the token, it either validates it, or responds with an appropriate HTTP status code if the token is invalid or unauthorized.

Tip

In Microsoft 365 for the web, an access token generates by the host and passes to the client using the `access_token` parameter before the first WOPI request. See [**Action URLs**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-urls) and for more information on how access tokens should be passed to Microsoft 365 for the web, see [**Passing access tokens securely**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage#passing-access-tokens-securely).

A WOPI client requires no understanding of the format or content of the token. The WOPI client just includes the token in WOPI requests and expects the host to validate it. But WOPI access tokens must adhere to the following guidelines:

- Access tokens must be scoped to a single user and resource combination. A WOPI client never assumes that an access token issued for a particular user and resource combination is valid for a different user and resource combination.
- Access tokens must be valid for the [user permissions](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#user-permissions-properties) that are provided by the host in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response. For example, if the `view` action is invoked, and the [UserCanWrite](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercanwrite) property is set to `true` in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response, the client might re-use that token when transitioning to edit mode. So, a WOPI client expects that any access token is valid for operations that the user has permissions to perform. If a host wishes to issue access tokens that are more narrowly scoped, the [user permissions properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#user-permissions-properties) in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response must reflect the permissions that the token provides.
- Access tokens should expire \(become invalid\) automatically after a period of time. Hosts can use the [access\_token\_ttl](#the-access_token_ttl-property) property to specify when an access token expires.

Important

WOPI clients expect that an access token remains valid until it expires \(as indicated by the [**access\_token\_ttl**](#the-access_token_ttl-property) value\). Hosts shouldn't revoke access tokens as a standard part of their operations. Tokens should only be revoked if a user’s permissions have changed or been revoked.

If hosts revoke access tokens regularly, users might experience strange behavior depending on the WOPI client. For example, in some cases, Microsoft 365 for the web will time out a user’s session and present them with a dialog asking if they’d like to refresh their session. If the access token isn't yet expired, based on the [**access\_token\_ttl**](#the-access_token_ttl-property), Microsoft 365 for the web will refresh the session using the existing access token, assuming it's still valid.

There are a number of cases like this, and WOPI clients regularly make such assumptions. For this reason, access tokens should remain valid until their expiry.

Important

WOPI clients aren't required to pass the [**access token**](#the-access_token_ttl-property) in the [**Authorization**](https://tools.ietf.org/html/rfc7235#section-4.2) header, but they must send it as a URL parameter in all WOPI operations. So, for maximum compatibility, WOPI hosts should either use the URL parameter in all cases, or fall back to it if the [**Authorization**](https://tools.ietf.org/html/rfc7235#section-4.2) header isn't included in the request.

### The access\_token\_ttl property

The access\_token\_ttl property tells a WOPI client when an access token expires, represented as the number of milliseconds since January 1, 1970 UTC \(the date epoch in JavaScript\). Despite its misleading name, it doesn't represent a time duration for which the access token is valid. The access\_token\_ttl is never used by itself; it's always attached to a specific access token.

Tip

To prevent data loss for users, Microsoft 365 for the web prompts users to save and refresh their sessions if the access token for their session is close to expiring. In order to do this, Microsoft 365 for the web needs to know when the access token expires, which it determines based on the access\_token\_ttl value.

We recommend using an access\_token\_ttl value that makes the access token valid for 10 hours. Hosts can also set the access\_token\_ttl value to `0`. This effectively tells the client that the token expiry is either infinite or unknown. In this case, clients might disable any UI prompting users to refresh their sessions. This can lead to unexpected data loss due to access token expiry. So, we strongly recommend specifying a value for access\_token\_ttl.

Note

Future updates to the WOPI protocol might include renaming this parameter so its name is less confusing.

## Lock

A lock is a conceptual construct that's associated with a file. Locks serve two purposes in WOPI:

- First, a lock prevents anyone that doesn't have a valid lock ID from making changes to a file. A WOPI client locks files prior to editing them to prevent other entities from changing the file while the client is also editing them.
- Two, a lock is also used to store a small bit of temporary data associated with a file. This metadata is called the lock ID and is a string with a maximum length of 1024 ASCII characters. For more information, see [note on lock ID lengths](#lock-length)\). WOPI clients can use this metadata for a variety of purposes, but hosts don't need any knowledge or understanding of the contents of the lock ID. Hosts must treat it as an opaque string.

Therefore, WOPI locks must:

- Be associated with a single file.
- Contain a lock ID of maximum length 1024 ASCII characters.
- Prevent all changes to that file unless a proper lock ID is provided.
- Expire after 30 minutes unless refreshed. For more information, see [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock).
- Not be associated with a particular user.

All WOPI operations that modify files, such as [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile), include a lock ID as a parameter in their request. Usually the expected lock ID is passed in the **X-WOPI-Lock** request header \(but not always. [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock) is an exception that uses **X-WOPI-OldLock** instead\).

WOPI requires that hosts compare the lock ID passed in a WOPI request with the lock ID currently on a file and respond appropriately when the lock IDs don't match. In particular, WOPI clients expect that when a lock ID does *not* match the current lock, the host sends back the current lock ID in the **X-WOPI-Lock** response header. This behavior is critical, because WOPI clients use the current lock ID in order to determine what further WOPI calls to make to the host.

### Lock length

It's important to understand that WOPI locks aren't user-owned. In other words, a WOPI client can execute lock-related operations using multiple access tokens. And hosts are expected to run those operations as long as they are valid, as described in this documentation. For example, a WOPI host might receive a [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) call with an access token that belongs to User A. The host might later receive an [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) call with an access token that belongs to User B. As long as User B has rights to edit the file, and the **X-WOPI-Lock** request header matches the lock ID, the [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) request should be honored.

WOPI locks must automatically expire after 30 minutes if not renewed by the WOPI client. This ensures that files don't stay locked indefinitely in error cases. Since locks are client-controlled from a protocol perspective \(that is, the WOPI client sets and manages the lock\) and clients can be unreliable, the WOPI host must expire the locks in such cases.

Tip

WOPI defines a [**GetLock**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getlock#getlock) operation. However, Microsoft 365 for the web doesn't use it in all cases, even if the host indicates support for the operation using the [**SupportsGetLock**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsgetlock) property in [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). Instead, Microsoft 365 for the web sometimes runs lock-related operations on files with missing or known incorrect lock IDs and expects the host to provide the current lock ID in its WOPI response. Typically, the [**Unlock**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) and [**RefreshLock**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock) operations serve this purpose, but other lock-related operations can be used.

The specific conditions for each response are covered in the documentation for each of the following lock-related WOPI operations:

- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock)
- [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock)
- [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock)
- [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock)
- [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)

Note

Lock ID lengths are currently less than 256 ASCII characters. But we anticipate needing longer lock IDs to support future WOPI integration scenarios. So, we've increased the limit to 1024 ASCII characters. Hosts must indicate that they support lock IDs of this length using the [**SupportsExtendedLockLength**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsextendedlocklength) property in [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).

## Share URL

A Share URL is a URL to a webpage that's suitable for viewing a shared WOPI file or container. The URL should be appropriate for launching in a web browser, but the experience is defined by the host. For example, the host might choose to have the URL navigate to the host’s browse experience or to a preview of the file using Microsoft 365 for the web or another file previewer.

A host might support different types of Share URLs that can be used for different purposes. For example, a particular Share URL type might not allow users to edit the file by using the Share URL. The list of possible types are defined under the [SupportedShareUrlTypes](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportedshareurltypes) property.

## WOPISrc

The WOPISrc \(*WOPI Source*\) is the URL that runs WOPI operations on a file. It's a combination of the Files endpoint URL for the host, along with a particular [file ID](#file-id). The WOPISrc doesn't include an [access token](#access-token).

For example, a WopiSrc might look like this:

`https://wopi.contoso.com/wopi/files/abcdef0123456789`

The WOPISrc is needed beyond just a file ID. It tells the WOPI client what URL to call back to when running WOPI operations on a file. In practice, the WOPISrc and a [file ID](#file-id) are synonymous, since the WOPI client typically works with the WOPISrc itself, not the raw [file ID](#file-id).

For more details on how the WOPISrc is passed to Microsoft 365 for the web, see [WOPI\_SOURCE](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi_source).
