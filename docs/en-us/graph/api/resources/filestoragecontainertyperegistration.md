<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# fileStorageContainerTypeRegistration resource type

Namespace: microsoft.graph

Represents the entity created when a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0), also known as container type, is registered on a consuming tenant using its ID \(**containerTypeId**\). This registration is required to be able to create [containers](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0).

Some **fileStorageContainerTypeRegistration** [settings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistrationsettings?view=graph-rest-1.0) can be made different from the defined in the [container type settings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0) only if they're set as overridable.

The [applicationPermissionGrants](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) define the access privileges of applications on containers of a specific **containerTypeId**. It supports the definition of both application-only and delegated permissions. A container type registration can have more than one [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) and an application can have access to more than one container type registration. This arrangement allows container access to be shared across applications.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/filestorage-list-containertyperegistrations?view=graph-rest-1.0) | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) collection | Get a list of the [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertyperegistrations?view=graph-rest-1.0) | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) | Create or replace a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-get?view=graph-rest-1.0) | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) | Read the properties and relationships of a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-update?view=graph-rest-1.0) | [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) | Update the properties of a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/filestorage-delete-containertyperegistrations?view=graph-rest-1.0) | None | Delete a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object. |
| [List application permission grants](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-list-applicationpermissiongrants?view=graph-rest-1.0) | [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) collection | List all [app permission grants](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) in a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0). |
| [Create file storage container type app permission grant](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-post-applicationpermissiongrants?view=graph-rest-1.0) | [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) | Create a new [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) object in a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| billingClassification | fileStorageContainerBillingClassification | The billing type. The possible values are: `standard`, `trial`, `directToCustomer`, `unknownFutureValue`. The default value is `standard`. |
| billingStatus | fileStorageContainerBillingStatus | The billing status. Valid when the billing is set up or with trial **fileStorageContainerType** objects that don't require billing. The possible values are: `invalid`, `valid`, `unknownFutureValue`. |
| etag | String | Used in update scenarios for optimistic concurrency control. Read-only. |
| expirationDateTime | DateTimeOffset | The expiration date. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier of the **fileStorageContainerTypeRegistration** object. Read-only. |
| name | String | The name of the **fileStorageContainerTypeRegistration**. Read-only. |
| owningAppId | Guid | ID of the application that owns the **fileStorageContainerType**. Read-only. |
| registeredDateTime | DateTimeOffset | The registration date. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| settings | [fileStorageContainerTypeRegistrationSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistrationsettings?view=graph-rest-1.0) | The settings of the **fileStorageContainerTypeRegistration**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applicationPermissionGrants | [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) collection | Access privileges of applications on containers. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeRegistration",
  "billingClassification": "String",
  "billingStatus": "String",
  "etag": "String",
  "expirationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "name": "String",
  "owningAppId": "Guid",
  "registeredDateTime": "String (timestamp)",
  "settings": {"@odata.type": "microsoft.graph.fileStorageContainerTypeRegistrationSettings"}
}
```
