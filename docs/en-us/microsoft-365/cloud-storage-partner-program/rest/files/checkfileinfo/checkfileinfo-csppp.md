<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp -->
<!-- Sitemap-Last-Modified: 2024-08-21 -->

# Additional CheckFileInfo properties for CSPP Plus hosts

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

To enable the WOPI coauthoring extensions for CSPP Plus, you must set the following existing optional properties and new properties.

If any of the required properties are set to their default value \(`0` for int, `false` for Boolean, `String.Empty` or null for strings\), the client must act as if the coauthoring extensions aren't available, effectively behaving as if `SupportsCoauth` is set to `false`. The exception is `AccessTokenExpiry`, for which `0` is a valid value.

## New optional properties

For the WOPI coauthoring extensions to be enabled, the following new optional properties are *required* to be set to valid values:

- `SupportsCoauth`
- `SequenceNumber`
- `OfficeCollaborationServiceEndpointUrl`
- `RealTimeChannelEndpointUrl`
- `AccessTokenExpiry`
- `ServerTime`
- `SharingStatus`
- `FileGeoLocationCode`

### SupportsCoauth

A *Boolean* value that indicates that the host provides the support for multiple WOPI clients to participate in document content modification in an overlapping manner. In addition to promising a non-default value for the following properties, it also indicates implementation of the following WOPI operations:

- `GetCoauthLock`
- `RefreshCoauthLock`
- `UnlockCoauthLock`
- `GetCoauthTable`
- `GetChunkedFile`
- `PutChunkedFile`
- `GetSequenceNumber`

### SequenceNumber

An *int* value that indicates the current sequence number of the file's contents. The value controls the document coherency semantic for the update. For more information, see [GetSequenceNumber](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-sequence-number).

### OfficeCollaborationServiceEndpointUrl

A *string* value that is a URI to the Collaboration Service endpoint that the WOPI client can use for collaboration. The value is the URL associated with the "collab" action provided in WOPI discovery.

### RealTimeChannelEndpointUrl

A *string* value that is a URI to the Real Time Channel Service endpoint that the WOPI client can use for real-time updates. The value is the URL associated with the "rtc" action provided in WOPI discovery.

### AccessTokenExpiry

A *long* value that indicates the time of access token expiry, represented as the number of milliseconds since January 1, 1970 UTC \(the date epoch in JavaScript\). For more information, see [access\_token\_ttl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts?#the-access_token_ttl-property).

### ServerTime

A *long* value that indicates the time on the server when responding to the request, represented as the number of milliseconds since January 1, 1970 UTC \(the date epoch in JavaScript\).

### SharingStatus

Note

`SharingStatus` is an existing property marked as “\(Pre-release property - not yet used by any WOPI client\)” in the currently available public documentation. The property is applicable for coauthoring extensions.

A *string* value that indicates whether the current document is shared with other users. The value can change when you add or remove permissions to other users. Clients might use this value to help choose how active to be in checking to see whether multiple clients are simultaneously working with the file. For more information, see [SharingStatus](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#sharingstatus).

Possible values:

- **Private**. Only the document owner has permission to the file.
- **Shared**. At least one other user has access to the file via direct permissions or a sharing link.

The following *new* optional properties are *not required* for the coauthoring extensions to be enabled.

### ComplianceDomainPrefix

A *string* value that is the regional compliance domain for this file, and which specifies that traffic should remain in a specific country or region. Don't return the property if there are no regional compliance requirements. Please contact CSPP Plus team for the supported values.

### FileGeoLocationCode

A *string* value that indicates the geographical location where the file is hosted. If the `ComplianceDomainPrefix` property is returned, WOPI clients use that property to infer the file’s location.  
Please contact CSPP Plus team for the supported values.

## Existing optional properties

To enable the coauthoring extensions, these *existing* optional properties are *required* to be set to valid values:

- `SupportsLocks`
- `SupportsUpdate`
- `SupportsUserInfo`

### SupportsLocks

An existing *Boolean* property that must be `true`, indicating that the associated WOPI locking methods are supported.

### SupportsUpdate

An existing *Boolean* property that must be `true`, indicating that the associated WOPI file-updating methods are supported.

### SupportsUserInfo

An existing *Boolean* property that must be `true`, indicating that the associated WOPI method is supported.
