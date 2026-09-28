<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkConnection resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the connection status of a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta) and its peripherals. The connection status is useful when you calculate the device health as when the required peripheral is not connected properly the device health changes to critical state.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connectionStatus | teamworkConnectionStatus | Indicates whether a component/peripheral is connected/disconnected or its state is unknown. The possible values are: `unknown`, `connected`, `disconnected`, `unknownFutureValue`. |
| lastModifiedDateTime | DateTimeOffset | Time at which the state was last changed. For example, indicates *connected since* when the state is `connected` and *disconnected since* when the state is `disconnected`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkConnection",
  "connectionStatus": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
