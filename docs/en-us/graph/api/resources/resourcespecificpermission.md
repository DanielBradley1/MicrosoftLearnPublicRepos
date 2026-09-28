<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# resourceSpecificPermission resource type

Namespace: microsoft.graph

Represents permissions used to authorize an application for direct access to data for a specific instance of resource, such as a chat or team. For example, the resource-specific permission ChannelMessage.Read.Group allows a Microsoft Teams app to read the channel messages of a single team.

Resource-specific permissions are only supported for Teams apps accessing to specific chats and teams using the Microsoft Graph API. For details, see [Resource-specific consent for Teams apps](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Describes the level of access that the resource-specific permission represents. |
| displayName | String | The display name for the resource-specific permission. |
| id | Guid | The unique identifier for the resource-specific application permission. |
| isEnabled | Boolean | Indicates whether the permission is enabled. |
| value | String | The value of the permission. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.resourceSpecificPermission",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "value": "String"
}
```
