<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceappmanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAppManagement resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all device app management functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceappmanagement-get?view=graph-rest-1.0) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceappmanagement?view=graph-rest-1.0) | Read properties and relationships of the [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceappmanagement?view=graph-rest-1.0) object. |
| [Update deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceappmanagement-update?view=graph-rest-1.0) | [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceappmanagement?view=graph-rest-1.0) | Update the properties of a [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceappmanagement?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedEBooks | [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-1.0) collection | The Managed eBook. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagement",
  "id": "String (identifier)"
}
```
