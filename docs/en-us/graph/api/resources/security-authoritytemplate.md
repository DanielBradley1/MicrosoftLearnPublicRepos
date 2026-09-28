<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authorityTemplate resource type

Namespace: microsoft.graph.security

Specifies the underlying authority that describes the type of content to be retained and its retention schedule. This resource supports CRUD operations to apply and manage the [filePlanAuthority](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanauthority?view=graph-rest-1.0) descriptor for a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0). The **authority** file plan descriptor supplements a retention label to improve the manageability and organization of Microsoft 365 content.

Inherits from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-authorities?view=graph-rest-1.0) | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-authorities?view=graph-rest-1.0) | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) | Create a new [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-authoritytemplate-get?view=graph-rest-1.0) | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-delete-authorities?view=graph-rest-1.0) | None | Delete a [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the authority descriptor. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the authority descriptor is created. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| displayName | String | Unique string that defines an authority name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). |
| id | String | Unique ID of the authority. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.authorityTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)"
}
```
