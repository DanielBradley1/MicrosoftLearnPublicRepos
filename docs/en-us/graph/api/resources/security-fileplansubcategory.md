<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplansubcategory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# filePlanSubcategory resource type

Namespace: microsoft.graph.security

Represents a unique subcategory applied to a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0). Used to supplement a retention label for [record management purposes](https://learn.microsoft.com/en-us/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-1.0).

To create, get, or delete a **filePlanSubcategory** descriptor, use the [subcategoryTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-subcategorytemplate?view=graph-rest-1.0) resource.

This resource is one of a set of file plan descriptors that an administrator can choose to supplement a retention label. To find out more about these optional descriptors, and how to get the descriptors that have been chosen for a retention label, see [file plan descriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0).

Inherits from [microsoft.graph.security.filePlanDescriptorBase](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptorbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines a filePlanSubcategory name. Inherited from [microsoft.graph.security.filePlanDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanSubcategory",
  "displayName": "String"
}
```
