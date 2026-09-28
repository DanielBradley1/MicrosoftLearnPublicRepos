<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedMobileApp resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The identifier for the deployment an app.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedMobileApps](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedmobileapp-list?view=graph-rest-1.0) | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) collection | List properties and relationships of the [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) objects. |
| [Get managedMobileApp](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedmobileapp-get?view=graph-rest-1.0) | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) | Read properties and relationships of the [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) object. |
| [Create managedMobileApp](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedmobileapp-create?view=graph-rest-1.0) | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) | Create a new [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) object. |
| [Delete managedMobileApp](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedmobileapp-delete?view=graph-rest-1.0) | None | Deletes a [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0). |
| [Update managedMobileApp](https://learn.microsoft.com/en-us/graph/api/intune-mam-managedmobileapp-update?view=graph-rest-1.0) | [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) | Update the properties of a [managedMobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedmobileapp?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mobileAppIdentifier | [mobileAppIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mobileappidentifier?view=graph-rest-1.0) | The identifier for an app with it's operating system type. |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedMobileApp",
  "mobileAppIdentifier": {
    "@odata.type": "microsoft.graph.androidMobileAppIdentifier",
    "packageId": "String"
  },
  "id": "String (identifier)",
  "version": "String"
}
```
