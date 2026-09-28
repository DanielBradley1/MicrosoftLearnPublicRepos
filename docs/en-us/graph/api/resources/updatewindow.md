<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/updatewindow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# updateWindow resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the time window during which [agents](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesagent?view=graph-rest-beta) can receive updates. This object is configured in the **updateWindow** property of [hybridAgentUpdaterConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hybridagentupdaterconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| updateWindowEndTime | TimeOfDay | End of a time window during which agents can receive updates |
| updateWindowStartTime | TimeOfDay | Start of a time window during which agents can receive updates |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "updateWindowEndTime": "String (timestamp)",
  "updateWindowStartTime": "String (timestamp)"
}
```
