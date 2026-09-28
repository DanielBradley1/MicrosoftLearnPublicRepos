<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# serviceApp resource type

Namespace: microsoft.graph

Represents a service application that's registered as a backup service control app.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-serviceapps?view=graph-rest-1.0) | [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) collection | Get a list of the [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-serviceapps?view=graph-rest-1.0) | [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) | Create a new [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/serviceapp-get?view=graph-rest-1.0) | [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) | Read the properties and relationships of a [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-delete-serviceapps?view=graph-rest-1.0) | None | Delete a [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0). |
| [Activate](https://learn.microsoft.com/en-us/graph/api/serviceapp-activate?view=graph-rest-1.0) | [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) | Activate a service app on behalf of the signed-in user. |
| [Deactivate](https://learn.microsoft.com/en-us/graph/api/serviceapp-deactivate?view=graph-rest-1.0) | [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) | Deactivate a service app on behalf of the signed-in user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The Entra ID application ID. |
| effectiveDateTime | DateTimeOffset | Timestamp of the effective activation of the service app. |
| id | String | The unique identifier of the service app. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified the entity. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification of the entity. |
| registrationDateTime | DateTimeOffset | Timestamp of the creation of the service app entity. |
| status | [serviceAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0#serviceappstatus-values) | The status of the service app. This value indicates whether or not the application can be used to control the backup service. The possible values are: `inactive`, `active`, `pendingActive`, `pendingInactive`, `unknownFutureValue`. |

### serviceAppStatus values

| Member | Description |
| :--- | :--- |
| inactive | The app is registered with the backup service. |
| active | The app is actively in use as a backup service control app. |
| pendingActive | A request was made to activate the app but it's not yet active. The app can't be used to control or manage the backup service and has read-only access to the protection policies and protection units. |
| pendingInactive | A request was made to deactivate the app but the app isn't yet inactive. The app can be used to control the backup service until the effective date. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceApp",
  "id": "String (identifier)",
  "status": "String",
  "registrationDateTime": "String (timestamp)",
  "effectiveDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "application": {
    "@odata.type": "microsoft.graph.identity"
  }
}
```
