<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandepartment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# filePlanDepartment resource type

Namespace: microsoft.graph.security

Represents a file plan descriptor that specifies the department or business unit of an organization to which a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) applies. Used to supplement a retention label for [record management purposes](https://learn.microsoft.com/en-us/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-1.0).

To create, get, or delete a **filePlanDepartment** descriptor, use the [departmentTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-departmenttemplate?view=graph-rest-1.0) resource.

This resource is one of a set of file plan descriptors that an administrator can choose to supplement a retention label. To find out more about these optional descriptors, and how to get the descriptors that have been chosen for a retention label, see [file plan descriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0).

Inherits from [microsoft.graph.security.filePlanDescriptorBase](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptorbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines a filePlanDepartment name. Inherited from [microsoft.graph.security.filePlanDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanDepartment",
  "displayName": "String"
}
```
