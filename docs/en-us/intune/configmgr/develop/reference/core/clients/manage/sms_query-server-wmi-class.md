<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Query Server WMI Class

The `SMS_Query` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that serves as a container for predefined queries.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_Query : SMS_BaseClass
{
   String Comments;
   String Expression;
   String LimitToCollectionID;
   String LocalizedCategoryInstanceNames[];
   String Name;
   String QueryID;
   String ResultAliasNames[];
   String ResultColumnsNames[];
   String TargetClassName;
};
```

## Methods

The following table lists the methods in `SMS_Query`.

| Method | Description |
| --- | --- |
| [CreateCCRs Method in Class SMS\_Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/createccrs-method-in-class-sms_query) | Generates client configuration requests \(CCRs\) for the query. |
| [FindResourceSite Method in Class SMS\_Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/findresourcesite-method-in-class-sms_query) | Gets site code information for resources from SQL. |

## Properties

`Comments` Data type: **String**

Access type: Read/Write

Qualifiers: None

Comments to document the query. The default value is "".

`Expression` Data type: **String**

Access type: Read/Write

Qualifiers: None

WMI Query Language \(WQL\) text for the query. The default value is "".

`LimitToCollectionID` Data type: **String**

Access type: Read/Write

Qualifiers: None

ID of a collection. This ID is used to limit the query results to resources that are members of the collection.

`LocalizedCategoryInstanceNames` Data type: **String** Array

Access type: Read

Qualifiers: None

Localized names of the categories to which the resource belongs.

`Name` Data type: **String**

Access type: Read/Write

Qualifiers: None

Name of the query as shown in the Configuration Manager console. The default value is "".

`QueryID` Data type: **String**

Access type: Read-only

Qualifiers: \[read, key\]

Unique auto-generated ID for the query.

`ResultAliasNames` Data type: **String** Array

Access type: Read-only

Qualifiers: None

If you specify an alias in the query expression, this array will be filled with the aliases.

`ResultColumnsNames` Data type: **String** Array

Access type: Read-only

Qualifiers: None

If you specify an alias in the query expression, this array will be filled with the resulting alias columns names.

`TargetClassName` Data type: **String**

Access type: Read/Write

Qualifiers: None

Name of the target class, found in the FROM clause of the query. The default value is "".

This name is arbitrary for queries that perform a JOIN operation. The Configuration Manager console uses this property for display purposes to give the user an idea of the data that the query retrieves.

## Remarks

Class qualifiers for this class include:

- Secured
- DisplayName\("Query"\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  You can use `SMS_Query` to persist valid queries that can be used later in an application or that can be run from the Configuration Manager console.

  Instances of this class with the `TargetClassName` property set to an [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class) object appear in the System Status node in the Configuration Manager console. All other instances appear in the Queries node.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class)
