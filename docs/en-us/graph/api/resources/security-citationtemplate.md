<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# citationTemplate resource type

Namespace: microsoft.graph.security

Represents the specific rule or regulation created by a jurisdiction used to determine whether certain labels and content should be retained or deleted. This resource supports CRUD operations to apply and manage the [filePlanCitation](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplancitation?view=graph-rest-1.0) descriptor for a [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0). The **citation** file plan descriptor supplements a retention label to improve the manageability and organization of Microsoft 365 content.

Inherits from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-citations?view=graph-rest-1.0) | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-citations?view=graph-rest-1.0) | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) | Create a new [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-citationtemplate-get?view=graph-rest-1.0) | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-delete-citations?view=graph-rest-1.0) | None | Delete a [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| citationJurisdiction | String | Represents the jurisdiction or agency that published the citation. |
| citationUrl | String | Represents the URL to the published citation. |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the citation descriptor. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the citation descriptor is created. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). Read-only. |
| displayName | String | Unique string that defines a citation name. Inherited from [microsoft.graph.security.filePlanDescriptorTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0). |
| id | String | Unique ID of the citation. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.citationTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "citationUrl": "String",
  "citationJurisdiction": "String"
}
```
