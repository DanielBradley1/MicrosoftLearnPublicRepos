<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-roledefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# roleDefinition resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information for the role definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description for the role. |
| displayName | String | The display name for the role assignment. |
| templateId | String | The unique identifier for the template. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.roleDefinition",
  "description": "String",
  "displayName": "String",
  "templateId": "String"
}
```
