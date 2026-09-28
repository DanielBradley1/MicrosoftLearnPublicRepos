<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-adminunitcreationoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# adminUnitCreationOptions resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different management choices for the administrative units to be provisioned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createBasedOnOrg | Boolean | Indicates whether the administrative unit should be created based on the org. |
| createBasedOnOrgPlusRoleGroup | Boolean | Indicates whether the administrative unit should be created based on the org and role group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.adminUnitCreationOptions",
  "createBasedOnOrg": "Boolean",
  "createBasedOnOrgPlusRoleGroup": "Boolean"
}
```
