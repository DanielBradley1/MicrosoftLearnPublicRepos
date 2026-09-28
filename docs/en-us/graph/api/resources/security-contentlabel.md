<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentlabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# contentLabel resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the **contentLabel** object that defines Microsoft Purview Information Protection metadata on an object. The **contentLabel** returned by the [extractContentLabel](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-extractcontentlabel?view=graph-rest-beta) API resolve the **sensitivityLabel** that is currently applied to a file.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignmentMethod | String | Describes whether the label was applied by an automated \(`standard`\) process or a person \(`privileged`\). |
| creationDateTime | DateTimeOffset | Timestamp of when the **contentLabel** was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sensitivityLabel | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) | The **sensitivityLabel** referred to by the content metadata. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentLabel",
  "assignmentMethod": "String",
  "creationDateTime": "String (timestamp)"
}
```
