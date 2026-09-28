<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudrealtimecommunicationinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# cloudRealtimeCommunicationInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a group of properties that relate to Microsoft real-time communication information for a user.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| isSipEnabled | Boolean | Indicates whether the user has a SIP-enabled client registered for them. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudRealtimeCommunicationInfo",
  "isSipEnabled": "Boolean"
}
```
