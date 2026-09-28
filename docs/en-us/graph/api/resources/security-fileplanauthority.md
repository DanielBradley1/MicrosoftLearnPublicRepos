<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanauthority?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# filePlanAuthority resource type

Namespace: microsoft.graph.security

Represents a file plan descriptor that specifies the type of the underlying authority which determines the content to be retained and its retention schedule. Used to supplement a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) for [record management purposes](https://learn.microsoft.com/en-us/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-1.0).

To create, get, or delete a **filePlanAuthority** descriptor, use the [authorityTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-authoritytemplate?view=graph-rest-1.0) resource.

This resource is one of a set of file plan descriptors that an administrator can choose to supplement a retention label. To find out more about these optional descriptors, and how to get the descriptors that have been chosen for a retention label, see [file plan descriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0).

Inherits from [microsoft.graph.security.filePlanDescriptorBase](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptorbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines a filePlanAuthority name. Inherited from [microsoft.graph.security.filePlanDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanAuthority",
  "displayName": "String"
}
```
