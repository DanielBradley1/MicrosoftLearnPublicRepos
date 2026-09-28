<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-labelsroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# labelsRoot resource type

Namespace: microsoft.graph.security

A root resource for capabilities that support records management for Microsoft 365 data in an organization.

Those capabilities include using a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) to configure retention and deletion settings for a type of content in the Microsoft 365 data, and using one or more [file plan descriptors](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0) to supplement the retention label and provide additional options to better manage and organize the content.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List retentionLabels](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-retentionlabel?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) collection | Get a list of the [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) objects and their properties. |
| [Create retentionLabel](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-retentionlabel?view=graph-rest-1.0) | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) | Create a new [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object. |
| [List authorities](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-authorities?view=graph-rest-1.0) | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) collection | Get the authorityTemplate resources from the authorities navigation property. |
| [Create authorities](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-authorities?view=graph-rest-1.0) | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) | Create a new authorityTemplate object. |
| [List categories](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-categories?view=graph-rest-1.0) | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) collection | Get the categoryTemplate resources from the categories navigation property. |
| [Create categories](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-categories?view=graph-rest-1.0) | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) | Create a new categoryTemplate object. |
| [List citations](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-citations?view=graph-rest-1.0) | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) collection | Get the citationTemplate resources from the citations navigation property. |
| [Create citations](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-citations?view=graph-rest-1.0) | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) | Create a new citationTemplate object. |
| [List departments](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-departments?view=graph-rest-1.0) | [microsoft.graph.security.departmentTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-departmenttemplate?view=graph-rest-1.0) collection | Get the departmentTemplate resources from the departments navigation property. |
| [Create departments](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-departments?view=graph-rest-1.0) | [microsoft.graph.security.departmentTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-departmenttemplate?view=graph-rest-1.0) | Create a new departmentTemplate object. |
| [List filePlanReferences](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-list-fileplanreferences?view=graph-rest-1.0) | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) collection | Get the filePlanReferenceTemplate resources from the filePlanReferences navigation property. |
| [Create filePlanReferences](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-fileplanreferences?view=graph-rest-1.0) | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) | Create a new filePlanReferenceTemplate object. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorities | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) collection | Specifies the underlying authority that describes the type of content to be retained and its retention schedule. |
| categories | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) collection | Specifies a group of similar types of content in a particular department. |
| citations | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) collection | The specific rule or regulation created by a jurisdiction used to determine whether certain labels and content should be retained or deleted. |
| departments | [microsoft.graph.security.departmentTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-departmenttemplate?view=graph-rest-1.0) collection | Specifies the department or business unit of an organization to which a label belongs. |
| filePlanReferences | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) collection | Specifies a unique alpha-numeric identifier for an organization’s retention schedule. |
| retentionLabels | [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) collection | Represents how customers can manage their data, whether and for how long to retain or delete it. |

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.labelsRoot",
  "id": "String (identifier)"
}
```
