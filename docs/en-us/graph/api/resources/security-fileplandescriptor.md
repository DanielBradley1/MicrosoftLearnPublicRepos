<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-08 -->

# filePlanDescriptor resource type

Namespace: microsoft.graph.security

Represents a *set* of optional descriptors to supplement a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) and improve the manageability and organization of Microsoft 365 content.

You can add a descriptor by using the POST operation of the corresponding file plan descriptor *template*, and specifying data for the descriptor. For example, to include a [filePlanCitation](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplancitation?view=graph-rest-1.0) descriptor, use the [create citationTemplate](https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-citations?view=graph-rest-1.0) operation. Similarly, you can use the GET or DELETE operations on the template resource for the descriptor.

To list the descriptors that supplement a retention label, use the [GET](https://learn.microsoft.com/en-us/graph/api/security-retentionlabel-get?view=graph-rest-1.0) operation on that [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) resource and apply `$expand` on the **descriptors** relationship.

For information on how retention labels and file plan descriptors work in the [Microsoft Purview compliance portal](https://compliance.microsoft.com/), see [Use file plan to create and manage retention labels](https://learn.microsoft.com/en-us/purview/file-plan-manager).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authority | [microsoft.graph.security.filePlanAuthority](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanauthority?view=graph-rest-1.0) | Represents the file plan descriptor of type authority applied to a particular retention label. |
| appliedCategory | [microsoft.graph.security.filePlanAppliedCategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanappliedcategory?view=graph-rest-1.0) | Represents the file plan descriptor of type category applied to a particular retention label. |
| citation | [microsoft.graph.security.filePlanCitation](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplancitation?view=graph-rest-1.0) | Represents the file plan descriptor of type citation applied to a particular retention label. |
| department | [microsoft.graph.security.filePlanDepartment](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandepartment?view=graph-rest-1.0) | Represents the file plan descriptor of type department applied to a particular retention label. |
| filePlanReference | [microsoft.graph.security.filePlanReference](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreference?view=graph-rest-1.0) | Represents the file plan descriptor of type filePlanReference applied to a particular retention label. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorityTemplate | [microsoft.graph.security.authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) | Specifies the underlying authority that describes the type of content to be retained and its retention schedule. |
| categoryTemplate | [microsoft.graph.security.categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) | Specifies a group of similar types of content in a particular department. |
| citationTemplate | [microsoft.graph.security.citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) | The specific rule or regulation created by a jurisdiction used to determine whether certain labels and content should be retained or deleted. |
| departmentTemplate | [microsoft.graph.security.departmentTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-departmenttemplate?view=graph-rest-1.0) | Specifies the department or business unit of an organization to which a label belongs. |
| filePlanReferenceTemplate | [microsoft.graph.security.filePlanReferenceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreferencetemplate?view=graph-rest-1.0) | Specifies a unique alpha-numeric identifier for an organization’s retention schedule. |

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanDescriptor",
  "id": "String (identifier)",
  "authority": {
    "@odata.type": "microsoft.graph.security.filePlanAuthority"
  },
  "category": {
    "@odata.type": "microsoft.graph.security.filePlanAppliedCategory"
  },
  "citation": {
    "@odata.type": "microsoft.graph.security.filePlanCitation"
  },
  "department": {
    "@odata.type": "microsoft.graph.security.filePlanDepartment"
  },
  "filePlanReference": {
    "@odata.type": "microsoft.graph.security.filePlanReference"
  }
}
```
