<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupwritebackconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# groupWritebackConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates whether writeback of cloud groups to on-premises Active Directory is enabled and the target group type for the on-premises group.

By default, all Microsoft Entra security groups aren't writeback enabled. For Microsoft 365 groups, the default settings that are defined by the properties of this resource can be overwritten by the `NewUnifiedgroupWritebackDefault` [directory setting object](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting?view=graph-rest-beta).

Inherits from [writebackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/writebackconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether writeback of cloud groups to on-premises Active Directory is enabled. Nullable. Default value is `true` for Microsoft 365 groups and `false` for security groups. Inherited from [writebackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/writebackconfiguration?view=graph-rest-beta). |
| onPremisesGroupType | String | Indicates the target on-premises group type the cloud object is written back as. Nullable. The possible values are: `universalDistributionGroup`, `universalSecurityGroup`, `universalMailEnabledSecurityGroup`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupWritebackConfiguration",
  "isEnabled": "Boolean",
  "onPremisesGroupType": "String"
}
```
