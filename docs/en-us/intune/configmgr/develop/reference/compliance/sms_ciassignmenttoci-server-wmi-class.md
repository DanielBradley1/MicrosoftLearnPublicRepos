<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_ciassignmenttoci-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIAssignmentToCI Server WMI Class

The `SMS_CIAssignmentToCI` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a relationship between a configuration baseline and its assignments.

## Syntax

```
Class SMS_CIAssignmentToCI : SMS_BaseClass
{
      UInt32 AssignmentID;
      UInt32 CI_ID;
};
```

## Methods

The `SMS_CIAssignmentToCI` class does not define any methods.

## Properties

`AssignmentID` Data type: `UInt32`

Access type: Read-only.

Qualifiers: \[key\]

Unique ID of the assignment.

`CI_ID` Data type: `UInt32`

Access type: Read-only.

Qualifiers: \[key\]

The unique ID of the configuration item. This ID is unique only for the site.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class)
