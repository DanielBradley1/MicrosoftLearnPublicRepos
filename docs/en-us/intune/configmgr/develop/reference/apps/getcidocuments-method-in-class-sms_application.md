<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/getcidocuments-method-in-class-sms_application -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetCIDocuments Method in Class SMS\_Application

The `GetCIDocuments` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets all of the configuration item documents for the application installation.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 GetCIDocuments (
     uint32  DocCIID[],
     string DocumentID[],
     string DocumentType[]
);
```

#### Parameters

`DocCIID` Data type: `UInt32` Array

Qualifiers: \[out\]

Configuration item ID of the documents.

`DocumentID` Data type: `String` Array

Qualifiers: \[out\]

Document ID list.

`DocumentType` Data type: `String` Array

Qualifiers: \[out\]

Type of document. Possible values are:

| Value | Type of document |
| --- | --- |
| 1 | Represent a manifest document. |
| 2 | Represents a properties document. |
| 3 | Represents a policy document that is the latest version configuration item. |
| -3 | Represents a policy document that is not the latest version configuration item. |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
