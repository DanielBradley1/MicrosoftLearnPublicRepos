<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_collectionvariable-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionVariable Server WMI Class

The `SMS_CollectionVariable` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a collection variable that is accessible at the time of task execution.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionVariable
{
      Boolean IsMasked;
      String Name;
      String Value;
};
```

## Methods

The `SMS_CollectionVariable` class does not define any methods.

## Properties

`IsMasked` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

This value should be set to `true` if the collection variable contains a sensitive value such as a password. If the value is set to `true`, the SMS Provider treats this property as write-only and disallows reads. The default value is `false`.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Collection variable name. The default value is "".

`Value` Data type: `String`

Access type: Read/Write

Qualifiers: None

Collection variable value. The default value is "".

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Collection variables are associated with collections as collection extended properties.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CollectionSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class)
