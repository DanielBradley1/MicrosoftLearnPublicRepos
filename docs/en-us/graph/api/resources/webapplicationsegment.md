<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-23 -->

# webApplicationSegment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the segment configurations that are allowed for an **on-premises wildcard application** published through Microsoft Entra application proxy and accessed via HTTP.

Inherits from [applicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/applicationsegment?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/websegmentconfiguration-list-applicationsegments?view=graph-rest-beta) | [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) collection | Get a list of the [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/websegmentconfiguration-post-applicationsegments?view=graph-rest-beta) | [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) | Create a new [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/webapplicationsegment-get?view=graph-rest-beta) | [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) | Read the properties and relationships of a [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/webapplicationsegment-update?view=graph-rest-beta) | [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) | Update the properties of a [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/websegmentconfiguration-delete-applicationsegments?view=graph-rest-beta) | None | Delete a [webApplicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationsegment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| alternateUrl | String | If you're configuring a traffic manager in front of multiple app proxy application segments, this property contains the user-friendly URL that points to the traffic manager. |
| externalUrl | String | The published external URL for the application segment; for example, `https://intranet.contoso.com/`. |
| id | String | The unique identifier that is assigned to an applicationSegment by Microsoft Entra ID. Not nullable. Read-only. Supports `$filter` \(`eq`\). Inherited from [applicationSegment](https://learn.microsoft.com/en-us/graph/api/resources/applicationsegment?view=graph-rest-beta). |
| internalUrl | String | The internal URL of the application segment; for example, `https://intranet/`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| corsConfigurations | [corsConfiguration\_v2](https://learn.microsoft.com/en-us/graph/api/resources/corsconfiguration_v2?view=graph-rest-beta) collection | A collection of CORS Rule definitions for a particular application segment. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.webApplicationSegment",
  "alternateUrl": "String",
  "externalUrl": "String",
  "internalUrl": "String"
}
```
