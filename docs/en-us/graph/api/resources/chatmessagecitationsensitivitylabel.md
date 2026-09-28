<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagecitationsensitivitylabel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-13 -->

# chatMessageCitationSensitivityLabel resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the sensitivity label applied to the source cited by a [chatMessageCitation](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagecitation?view=graph-rest-beta). Provides the display name and description of the sensitivity classification so that consumers can surface the appropriate handling guidance.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Read-only. User-facing description of the sensitivity restriction. |
| displayName | String | Read-only. Display name of the sensitivity label. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String"
}
```
