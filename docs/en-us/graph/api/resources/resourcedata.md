<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourcedata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# resourceData resource type

Namespace: microsoft.graph

Represents the resource data attached to the [change notification](https://learn.microsoft.com/en-us/graph/api/resources/changenotification?view=graph-rest-1.0) sent to the subscriber. This resource is an open type that allows additional properties beyond those documented here.

For details, see [Use Microsoft Graph to get change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview?view=graph-rest-1.0).

## Methods

None.

## Properties

None except for Outlook resources where **resourceData** contains the following fields:

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | The OData entity type in Microsoft Graph that describes the represented object. |
| @odata.id | String | The OData identifier of the object. |
| @odata.etag | String | The HTTP entity tag that represents the version of the object. |
| id | String | The identifier of the object. |

> **Note:** The **id** value provided in **resourceData** is valid at the time the change notification was generated. Some actions, such as moving a message to another folder, might result in the `id` no longer being valid when the change notification is processed.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.resourceData"
}
```
