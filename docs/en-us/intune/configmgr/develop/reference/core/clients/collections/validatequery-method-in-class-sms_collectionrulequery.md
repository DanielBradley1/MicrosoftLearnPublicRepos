<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ValidateQuery Method in Class SMS\_CollectionRuleQuery

The `ValidateQuery` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, verifies that the query collection rule is a valid WQL or Extended WQL statement.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
Boolean ValidateQuery(
     String WQLQuery
);
```

#### Parameters

`WQLQuery` Data type: `String`

Qualifiers: \[in\]

Query statement to validate.

## Return Values

A `Boolean` data type that is `true` if the query is validated.

## Remarks

Your application calls this method before adding a query rule to a collection. An invalid query rule results in no members being added to the collection for that query. This can be misleading and hard to debug.

In addition to being syntactically correct, the query rule must specify resource class names in the FROM clause. For example, the FROM clause must specify [SMS\_R\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_system-server-wmi-class), [SMS\_R\_User Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_user-server-wmi-class), [SMS\_R\_UserGroup Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_r_usergroup-server-wmi-class), or a user-defined resource class name.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
