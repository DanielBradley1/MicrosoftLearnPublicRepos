<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplancitation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-05 -->

# filePlanCitation resource type

Namespace: microsoft.graph.security

Represents a file plan descriptor that specifies a rule or regulation created by a jurisdiction to determine whether certain content should be retained or deleted. Used to supplement a [retention label](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) for [record management purposes](https://learn.microsoft.com/en-us/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-1.0).

To create, get, or delete a **filePlanCitation** descriptor, use the [citationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/security-citationtemplate?view=graph-rest-1.0) resource.

This resource is one of a set of file plan descriptors that an administrator can choose to supplement a retention label. To find out more about these optional descriptors, and how to get the descriptors that have been chosen for a retention label, see [file plan descriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0).

Inherits from [microsoft.graph.security.filePlanDescriptorBase](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptorbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| citationJurisdiction | String | Represents the jurisdiction or agency that published the filePlanCitation. |
| citationUrl | String | Represents the URL to the published filePlanCitation. |
| displayName | String | Unique string that defines a filePlanCitation name. Inherited from [microsoft.graph.security.filePlanDescriptor](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptor?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanCitation",
  "displayName": "String",
  "citationUrl": "String",
  "citationJurisdiction": "String"
}
```
