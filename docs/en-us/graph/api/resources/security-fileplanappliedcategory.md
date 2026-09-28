<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanappliedcategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# filePlanAppliedCategory resource type

Namespace: microsoft.graph.security

Represents a file plan descriptor that specifies a group of similar types of content in a department. Used to supplement a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) for [record management purposes](https://learn.microsoft.com/en-us/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-1.0).

To create, get, or delete an **filePlanAppliedCategory** descriptor, use the [categoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-categorytemplate?view=graph-rest-1.0) resource.

This resource is one of a set of file plan descriptors that an administrator can choose to supplement a retention label. To find out more about these optional descriptors, and how to get the descriptors that have been chosen for a retention label, see [file plan descriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0).

Inherits from [microsoft.graph.security.filePlanDescriptorBase](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptorbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines a file plan category name applied to the label. Inherited from [microsoft.graph.security.filePlanDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). |
| subcategory | [microsoft.graph.security.filePlanSubcategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplansubcategory?view=graph-rest-1.0) | Represents the file plan descriptor for a subcategory under a specific category, which has been assigned to a particular retention label. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanAppliedCategory",
  "displayName": "String",
  "subcategory": {
    "@odata.type": "microsoft.graph.security.filePlanSubcategory"
  }
}
```
