<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/updatevisibilityinepdashboard-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateVisibilityInEPDashBoard Method in Class SMS\_Collection

The `UpdateVisibilityInEPDashBoard` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that shows this collection in the Endpoint Protection dashboard.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 UpdateVisibilityInEPDashBoard
{
    [IN]    Boolean Visible
};
```

## Parameters

`Visible` Data type: `Boolean`

Qualifiers: \[id\("0"\), in\]

`true` if this collection should show in the Endpoint Protection dashboard.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
