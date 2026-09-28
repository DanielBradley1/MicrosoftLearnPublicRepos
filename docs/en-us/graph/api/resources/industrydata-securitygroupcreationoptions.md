<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-securitygroupcreationoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# securityGroupCreationOptions resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different options for the security groups to be provisioned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createBasedOnOrgPlusRoleGroup | Boolean | Indicates whether the security group should be created based on the org and role group. |
| createBasedOnRoleGroup | Boolean | A Boolean choice indicating whether the security group should be created based on the role group |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.securityGroupCreationOptions",
  "createBasedOnRoleGroup": "Boolean",
  "createBasedOnOrgPlusRoleGroup": "Boolean"
}
```
