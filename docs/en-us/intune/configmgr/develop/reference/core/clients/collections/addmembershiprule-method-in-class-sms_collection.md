<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/addmembershiprule-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddMembershipRule Method in Class SMS\_Collection

The `AddMembershipRule` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds a new rule to the `CollectionRules` property of the [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddMembershipRule(
     SMS_CollectionRule collectionRule,
     UInt32 QueryID
);
```

#### Parameters

`collectionRule` Data type: `SMS_CollectionRule`

Qualifiers: \[in\]

[SMS\_CollectionRule Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrule-server-wmi-class) object to add.

`QueryID` Data type: `UInt32`

Qualifiers: `[out]`

Configuration Manager-generated query ID if the rule is a query rule. If the rule is direct, this ID is 0. Use `QueryID` to modify or delete a query membership rule.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
