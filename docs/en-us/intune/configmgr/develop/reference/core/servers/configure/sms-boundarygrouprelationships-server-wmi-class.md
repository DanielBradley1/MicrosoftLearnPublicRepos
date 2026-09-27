<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms-boundarygrouprelationships-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_BoundaryGroupRelationships Server WMI Class

The `SMS_BoundaryGroupRelationships` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents fallback relationships for boundary groups.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroupRelationships : SMS_BaseClass
{
    UInt32 DestinationGroupID;
    String DestinationGroupName;
    UInt32 SourceGroupID;
    String SourceGroupName;
};
```

## Methods

The following table shows the methods in `SMS_BoundaryGroupRelationships`.

| Method | Description |
| --- | --- |
| [FallbackDP Method in Class SMS\_BoundaryGroupRelationships](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/fallbackdp-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a distribution point \(DP\). |
| [FallbackMP Method in Class SMS\_BoundaryGroupRelationships](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/fallbackmp-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a management point \(MP\). |
| [FallbackSMP Method in Class SMS\_BoundaryGroupRelationships](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/fallbacksmp-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a state migration point \(SMP\). |
| [FallbackSUP Method in Class SMS\_BoundaryGroupRelationships](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/fallbacksup-method-in-class-sms-boundarygrouprelationships) | Sets the fallback time for a software update point \(SUP\). |

## Properties

`DestinationGroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID of the destination boundary group.

`DestinationGroupName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the destination boundary group.

`SourceGroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID of the source boundary group.

`SourceGroupName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the source boundary group.

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BoundaryGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroup-server-wmi-class)

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes)
