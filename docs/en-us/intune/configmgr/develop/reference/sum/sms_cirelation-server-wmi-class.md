<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cirelation-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIRelation Server WMI Class

The `SMS_CIRelation` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that defines the relationship between two configuration items, for example, the superseding of one item by another.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIRelation : SMS_BaseClass
{
    UInt32 FromCIID;
    Boolean IsBroken;
    Boolean IsVersionSpecific;
    UInt32 Priority;
    UInt32 RelationType;
    UInt32 ToCIID;
};
```

## Methods

The `SMS_CIRelation` class does not define any methods.

## Properties

`FromCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

The ID of one of the configuration items. The value of this property usually depends on the value of `ToCIID` in the context specified by `RelationType`. For example, this property can represent a child configuration item ID \(FROMCIID\) that is derived from a parent configuration item ID \(TOCIID\).

The ID of a configuration item is represented by the `CI_ID` property of [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, key\]

`true` if the relation is broken, otherwise the value will be false.

`IsVersionSpecific` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None.

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None.

One App to deployment type relation \(9\) has priority.

`RelationType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Type of relationship between configuration items. Possible values are:

| Value | Relationship type |
| --- | --- |
| 1 | Bundled |
| 2 | Required |
| 3 | Prohibited |
| 4 | Optional |
| 5 | Derived |
| 6 | Superseded |
| 7 | Self |
| 8 | Reference |
| 9 | AppToDTReference |
| 10 | AppDependence |
| 11 | Intention |
| 12 | Platform |
| 13 | GlobalConditionReference |
| 15 | ApplicationSuperSeded |
| 16 | ApplicationType |
| 17 | ApplicationHost |
| 18 | ApplicationInstaller |
| 19 | SupersedOrDependent |
| 20 | VirtualEnvironmentReference |
| 21 | AppDCMReference |
| 22 | DeploymentTypeToPolicyTemplateReference |
| 23 | CIInheritanceRelation |

`ToCIID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

The ID for the second configuration item that is related to the first item. The value of this property usually depends on the value of `FromCIID` in the context specified by `RelationType`. For example, this property can represent a parent configuration item ID \(TOCIID\) from which a child configuration item ID \(FROMCIID\) is derived.

The ID of a configuration item is represented by the `CI_ID` property of [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is applicable to all types of configuration items, not just software updates. For a discussion of configuration item types, see the `CIType_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments)
