<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandescriptorbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# filePlanDescriptorBase resource type

Namespace: microsoft.graph.security

Specifies properties common to file plan descriptor resources. Base type for each of the descriptors: [filePlanAppliedCategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanappliedcategory?view=graph-rest-1.0), [filePlanAuthority](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanauthority?view=graph-rest-1.0), [filePlanCitation](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplancitation?view=graph-rest-1.0), [filePlanDepartment](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplandepartment?view=graph-rest-1.0), [filePlanReference](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplanreference?view=graph-rest-1.0), and [filePlanSubcategory](https://learn.microsoft.com/en-us/graph/api/resources/security-fileplansubcategory?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Unique string that defines the name for the file plan descriptor associated with a particular retention label. |

## Relationships

None.

## JSON representation

Here's a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.filePlanDescriptorBase",
  "displayName": "String"
}
```
