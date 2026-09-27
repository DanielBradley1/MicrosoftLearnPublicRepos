<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancemembership-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CategoryInstanceMembership Server WMI Class

The `SMS_CategoryInstanceMembership` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, which represents the relationship between categories and configuration item objects.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CategoryInstanceMembership
{
    UInt32 CategoryInstanceID;
    String ObjectKey;
    UInt32 ObjectTypeID;
};
```

## Methods

The `SMS_CategoryInstanceMembership` class does not define any methods.

## Properties

`CategoryInstanceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_CategoryInstanceBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstancebase-server-wmi-class)

`ObjectKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, sizelimit\]

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_ObjectContentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_objectcontentinfo-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
