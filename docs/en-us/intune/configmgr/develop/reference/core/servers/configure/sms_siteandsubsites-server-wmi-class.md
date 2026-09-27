<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteandsubsites-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SiteAndSubsites Server WMI Class

The `SMS_SiteAndSubsites` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that reads the current site and child site information.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteAndSubsites : SMS_BaseClass
{
    String ServerName;
    String SiteCode;
    String SiteName;
    String Version;
};
```

## Methods

The `SMS_SiteAndSubsites` class does not define any methods.

## Properties

`ServerName` Data type: `String`

Access type: Read

Qualifiers: \[none\]

The server name of the site Configuration Manager is installed on.

`SiteCode` Data type: `String`

Access type: Read

Qualifiers: \[key, sizelimit\("3"\)\]

The three letter site code for the site.

`SiteName` Data type: `String`

Access type: Read

Qualifiers: \[none\]

The name of the site.

`Version` Data type: `String`

Access type: Read

Qualifiers: \[none\]

The Configuration Manager version of the current site.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
