<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aimlsparser-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AIMLSParser Server WMI Class

The `SMS_AIMLSParser` Windows Management Instrumentation \(WMI\) class in Configuration Manager imports license data.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AIMLSParser : SMS_BaseClass ();
```

## Methods

The following table lists the methods in the `SMS_AIMLSParser` class.

| Method | Description |
| --- | --- |
| [GetStatus Method in Class SMS\_AIMLSParser](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getstatus-method-in-class-sms_aimlsparser) | Monitors the status of a previous call to the `Import` method. The returned values of the `Status` parameter are:  <br>  <br>0 - Successful completion |
| [GetSummary Method in Class SMS\_AIMLSParser](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getsummary-method-in-class-sms_aimlsparser) | Retrieves the counts of imported Microsoft license count and non-Microsoft license count. |
| [Import Method in Class SMS\_AIMLSParser](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/import-method-in-class-sms_aimlsparser) | Imports the MLS statement as specified by the `MLSFilepath` parameter \(in UNC format\) into the Configuration Manager database. |

## Properties

The `SMS_AIMLSParser` class does not define any properties.

## Remarks

Class qualifiers for this class include:

- DisplayName\("AI Hinv Classes List"\)
- Dynamic
- Provider\("ExtnProv"\)
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Initiate Asset Intelligence synchronization](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization)
