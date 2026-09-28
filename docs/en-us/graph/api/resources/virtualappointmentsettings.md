<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# virtualAppointmentSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Virtual appointment resource and supporting methods are deprecated and will stop returning data on June 30, 2023.

Represents settings that define the experience of a client user during a virtual appointment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowClientToJoinUsingBrowser | Boolean | Indicates whether the client can use the browser to join a virtual appointment. If set to `false`, the client can only use Microsoft Teams to join. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.virtualAppointmentSettings",
    "allowClientToJoinUsingBrowser": "Boolean"
}
```
