<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# fileStorageContainerType resource type

Namespace: microsoft.graph

Associates a SharePoint Embedded application and a set of [containers](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). A **fileStorageContainerType**, also called container type, defines settings, access privileges, and billing accountability.

Each container type is coupled with one SharePoint Embedded application that is referred to as the owning application.

A **fileStorageContainerType** must be [registered](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) in a tenant to be able to create containers.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/filestorage-list-containertypes?view=graph-rest-1.0) | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) collection | Get a list of the [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) objects and their properties for the current tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertypes?view=graph-rest-1.0) | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) | Create a new [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) in the owning tenant. |
| [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertype-get?view=graph-rest-1.0) | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) | Get a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) using its ID. |
| [Update](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertype-update?view=graph-rest-1.0) | [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) | Update the properties of a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/filestorage-delete-containertypes?view=graph-rest-1.0) | None | Delete a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) object from the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| billingClassification | fileStorageContainerBillingClassification | The billing type. The possible values are: `standard`, `trial`, `directToCustomer`, `unknownFutureValue`. The default value is `standard`. |
| billingStatus | fileStorageContainerBillingStatus | The billing status. Valid when the billing is set up or with trial **fileStorageContainerType** objects that don't require billing. The possible values are: `invalid`, `valid`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | The creation date. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| etag | String | Used in update scenarios for optimistic concurrency control. Read-only. |
| expirationDateTime | DateTimeOffset | The expiration date. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier of the **fileStorageContainerType** object. Read-only. |
| name | String | The name of the **fileStorageContainerType**. |
| owningAppId | Guid | ID of the application that owns the **fileStorageContainerType**. |
| settings | [fileStorageContainerTypeSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0) | The settings of the **fileStorageContainerType**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "billingClassification": "String",
  "billingStatus": "String",
  "createdDateTime": "String (timestamp)",
  "etag": "String",
  "expirationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "name": "String",
  "owningAppId": "Guid",
  "settings": {"@odata.type": "microsoft.graph.fileStorageContainerTypeSettings"}
}
```
