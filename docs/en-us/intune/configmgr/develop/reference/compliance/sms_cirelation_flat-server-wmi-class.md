<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_cirelation_flat-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIRelation\_Flat Server WMI Class

The `SMS_CIRelation_Flat` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides a flat list of relationship information for directly or indirectly related configuration items.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIRelation_Flat : SMS_BaseClass
{
    UInt32 FromCIID;
    Boolean IsVersionSpecific;
    UInt32 Level;
    UInt32 RelationType;
    UInt32 ToCIID;
};
```

## Methods

The `SMS_CIRelation_Flat` class does not define any methods.

## Properties

`FromCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_CIRelation Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class)

`IsVersionSpecific` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

[SMS\_CIRelation Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class)

`Level` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Level represents the depth of the relationships between configuration items. A direct relationship to the configuration item is 1 and an indirect relationship can be 2 or higher.

`RelationType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

[SMS\_CIRelation Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class)

`ToCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

[SMS\_CIRelation Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class)

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
