<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_SummarizerSiteStatus Server WMI Class

The `SMS_SummarizerSiteStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a summarizer for the overall health of each site.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SummarizerSiteStatus : SMS_BaseClass
{
     String SiteCode;
    UInt32 Status;
};
```

## Methods

The `SMS_SummarizerSiteStatus` class doesn't define any methods.

## Properties

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: \[key\]

Site code of the Configuration Manager site.

`Status` Data type: `UInt32`

Access type: Read

Qualifiers: None

Value indicating the overall health of the site. Possible values are listed below. Determining the overall status for the site hierarchy is based on the status of Configuration Manager components and storage objects.

| Value | Status |
| --- | --- |
| GREEN\(0\) | OK. There are no warning or error messages. |
| YELLOW\(1\) | Warning. Warning messages were generated, but error messages weren't generated. This status also indicates that the storage objects are approaching their threshold. |
| RED\(2\) | Critical. There are error messages, or the storage objects have exceeded their thresholds. |

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
