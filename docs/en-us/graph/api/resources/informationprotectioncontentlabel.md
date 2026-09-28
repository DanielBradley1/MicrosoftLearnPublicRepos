<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/informationprotectioncontentlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# informationProtectionContentLabel resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Describes the informationProtectionContentLabel object that defines MIP metadata on an object. **informationProtectionContentLabel** is returned by the [extractLabel](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-extractlabel?view=graph-rest-beta) API resolve to the label that is currently applied to a file.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | String | The possible values are: `standard`, `privileged`, `auto`. |
| creationDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| label | [labelDetails](https://learn.microsoft.com/en-us/graph/api/resources/labeldetails?view=graph-rest-beta) | Details on the label that is currently applied to the file. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignmentMethod": "String",
  "creationDateTime": "String (timestamp)",
  "label": {"@odata.type": "microsoft.graph.labelDetails"}
}
```
