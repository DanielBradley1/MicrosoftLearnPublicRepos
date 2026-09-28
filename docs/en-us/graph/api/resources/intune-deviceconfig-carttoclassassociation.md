<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# cartToClassAssociation resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

CartToClassAssociation for associating device carts with classrooms.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List cartToClassAssociations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-carttoclassassociation-list?view=graph-rest-beta) | [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) collection | List properties and relationships of the [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) objects. |
| [Get cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-carttoclassassociation-get?view=graph-rest-beta) | [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) | Read properties and relationships of the [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) object. |
| [Create cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-carttoclassassociation-create?view=graph-rest-beta) | [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) | Create a new [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) object. |
| [Delete cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-carttoclassassociation-delete?view=graph-rest-beta) | None | Deletes a [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta). |
| [Update cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-carttoclassassociation-update?view=graph-rest-beta) | [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) | Update the properties of a [cartToClassAssociation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-carttoclassassociation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| createdDateTime | DateTimeOffset | DateTime the object was created. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| version | Int32 | Version of the CartToClassAssociation. |
| displayName | String | Admin provided name of the device configuration. |
| description | String | Admin provided description of the CartToClassAssociation. |
| deviceCartIds | String collection | Identifiers of device carts to be associated with classes. |
| classroomIds | String collection | Identifiers of classrooms to be associated with device carts. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.cartToClassAssociation",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "version": 1024,
  "displayName": "String",
  "description": "String",
  "deviceCartIds": [
    "String"
  ],
  "classroomIds": [
    "String"
  ]
}
```
