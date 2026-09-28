<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptortemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# filePlanDescriptorTemplate resource type

Namespace: microsoft.graph.security

Specifies the properties common to the template resources for file plan descriptors. Base type for each of the template resources: [authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0), [categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0), [citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0), [departmentTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-departmenttemplate?view=graph-rest-1.0), [filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0), and [subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [microsoft.graph.identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset) | Represents the user who created the filePlanDescriptorTemplate column. |
| createdDateTime | DateTimeOffset | Represents the date and time in which the filePlanDescriptorTemplate is created. |
| displayName | String | Unique string that defines a filePlanDescriptorTemplate name. |
| id | String | Unique ID of the filePlanDecriptorTemplate column. Read-only. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanDescriptorTemplate",
  "id": "String (identifier)",
  "displayName": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)"
}
```
