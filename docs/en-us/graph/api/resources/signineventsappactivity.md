<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signineventsappactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-01 -->

# signInEventsAppActivity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the total number of sign-in events that have occurred for a specific application in the past 30 days.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/auditlogroot-list-signineventsappsummary?view=graph-rest-beta) | [signInEventsAppActivity](https://learn.microsoft.com/en-us/graph/api/resources/signineventsappactivity?view=graph-rest-beta) collection | Get a list of the signInEventsAppActivity objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | The application ID for the given summary. Supports `$filter` \(`eq`\). |
| signInCount | Int32 | The total number of sign-in events for the given application. Supports `$filter` \(`gt`\). |
| tenantId | String | The tenant ID where sign-in events occurred. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| application | [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) | Represents an application registered in Microsoft Entra ID. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInEventsAppActivity",
  "appId": "String (identifier)",
  "signInCount": "Integer",
  "tenantId": "String"
}
```
