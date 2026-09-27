<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_content-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Content Server WMI Class

The `SMS_Content` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides additional information about a `CI_Content` instance.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_Content : SMS_BaseClass
{
    String ContentDescription;
    UInt32 ContentFlags;
    String ContentHash;
    UInt32 ContentHashVersion;
    SInt32 ContentID;
    String ContentSource;
    UInt32 ContentType;
    String ContentUniqueID;
    UInt32 ContentVersion;
    UInt32 ObjectTypeID;
    String RelatedContentID;
    String SecurityKey;
};
```

## Methods

The following table lists the methods in the `SMS_Content` class.

| Method | Description |
| --- | --- |
| [IsOfficeContent Method in Class SMS\_Content](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/isofficecontent-method-in-class-sms_content) | Specifies whether content is Microsoft Office content. |

## Properties

`ContentDescription` Data type: `String`

Access type: Read/Write

Qualifiers: none

Description of the content.

`ContentFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

This specifies additional attributes for content instance.

| Value | Content flag |
| --- | --- |
| 8 | DOWNLOAD\_ON\_DEMAND\_FROM\_LOCAL\_DP |
| 12 | DOWNLOAD\_FROM\_LOCAL\_DISPPOINT |
| 13 | DOWNLOAD\_LOCAL\_PARTIALDOWNLOADTOLOCAL |
| 14 | DOWNLOAD\_FROM\_REMOTE\_DISPPOINT |
| 15 | DOWNLOAD\_REMOTE\_PARTIALDOWNLOADTOLOCAL |
| 16 | DOWNLOAD\_ENABLE\_PEER\_CACHING |
| 17 | DP\_NO\_FALLBACK\_UNPROTECTED |
| 24 | DO\_NOT\_DOWNLOAD |
| 25 | PERSIST\_IN\_CACHE |

`ContentHash` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Hash of the content.

`ContentHashVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

This specifies the hash version used to calculate the content hash.

`ContentID` Data type: `SInt32`

Access type: Read-only

Qualifiers: \[key, read\]

Identifier for the content.

`ContentSource` Data type: `String`

Access type: Read/Write

Qualifiers: none

This specifies the source location where content files are stored.

`ContentType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Type of the content.

`ContentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Unique identifier for the content.

`ContentVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Version of the content.

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The security type of the content.

`RelatedContentID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Specifies the related content associated with this content.

`SecurityKey` Data type: `String`

Access type: Read/Write

Qualifiers: none

The security key of the content. Content may be secured by application or package.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
