<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# filePlanReferenceTemplate resource type

Namespace: microsoft.graph.security

Supports CRUD operations to apply and manage the [filePlanReference](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreference?view=graph-rest-1.0) descriptor for a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0). The **filePlanReference** descriptor supplements a retention label to improve the manageability and organization of Microsoft 365 content.

Inherits from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-fileplanreferences?view=graph-rest-1.0) | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-fileplanreferences?view=graph-rest-1.0) | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) | Create a new [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-fileplanreferencetemplate-get?view=graph-rest-1.0) | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-delete-fileplanreferences?view=graph-rest-1.0) | None | Delete a [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the file plan reference descriptor. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the filePlanReference descriptor is created. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| displayName | String | Unique string that defines a filePlanReference name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). |
| id | String | Unique ID of the filePlanReference. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanReferenceTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)"
}
```
