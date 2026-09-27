<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_OSExpressionGroup Server WMI Class

The `SMS_TaskSequence_OSExpressionGroup` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an evaluation of a single operating system platform in a task sequence. An object of this type is always contained by an [SMS\_TaskSequence\_OSConditionGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osconditiongroup-server-wmi-class) object.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_OSExpressionGroup : SMS_TaskSequence_ConditionOperator
{
      String Name;
      SMS_TaskSequence_WMIConditionExpression Operands[];
      String OperatorType;
      String PlatformArchKey;
      String PlatformMaxVerKey;
      String PlatformMinVerKey;
      String PlatformTypeKey;
};
```

## Methods

The `SMS_TaskSequence_OSExpressionGroup` class does not define any methods.

## Properties

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Optional. The name of an operating system, for example, "Windows XP SP2". The default value is "". See the `DisplayText` property for `SMS_SupportedPlatforms`.

`Operands` Data type: `SMS_TaskSequence_WMIConditionExpression`Array

Access type: Read/Write

Qualifiers: \[Not\_NULL\]

See [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class).

Each element of this property is an [SMS\_TaskSequence\_WMIConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class) object that matches the WQL query for the `SMS_SupportedPlatforms` Server WMI Class object indexed by the platform keys. The expressions are typically built from the WQL query stored in the `Condition` property of `SMS_SupportedPlatforms`. There must be at least one [SMS\_TaskSequence\_WMIConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class) contained by the [SMS\_TaskSequence\_OSExpressionGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_osexpressiongroup-server-wmi-class).

`OperatorType` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_NULL\]

See [SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class).

The only operator type supported by this class is "and".

`PlatformArchKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Platform key that maps to the `OSPlatform` property for `SMS_SupportedPlatforms` objects. For more information, see the Remarks section later in this topic.

`PlatformMaxVerKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Platform key that maps to the `OSMaxVersion` property for `SMS_SupportedPlatforms` objects. For more information, see the Remarks section later in this topic.

`PlatformMinVerKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Platform key that maps to the `OSMinVersion` property for SMS\_SupportedPlatforms objects. For more information, see the Remarks section later in this topic.

`PlatformTypeKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_Null\]

Platform key that maps to the `OSName` property for `SMS_SupportedPlatforms` objects. For more information, see the Remarks section later in this topic.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

The platform strings specified by `PlatformArchKey`, `PlatformMaxVerKey`, `PlatformMinVerKey`, and `PlatformTypeKey` are used to index the corresponding `SMS_SupportedPlatforms` object instance for the expression.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_TaskSequence\_ConditionOperator Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_conditionoperator-server-wmi-class) [SMS\_SupportedPlatforms Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_supportedplatforms-server-wmi-class) [SMS\_TaskSequence\_WMIConditionExpression Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_wmiconditionexpression-server-wmi-class)
