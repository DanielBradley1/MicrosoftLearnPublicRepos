<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentuser?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# virtualAppointmentUser resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Virtual appointment resource and supporting methods are deprecated and will stop returning data on June 30, 2023.

Represents information about a client user in a virtual appointment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the user who participates in a virtual appointment. Optional. |
| emailAddress | String | The email address of the user who participates in a virtual appointment. Optional. |
| smsCapablePhoneNumber | String | The phone number for sending SMS texts for the user who participates in a virtual appointment. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.virtualAppointmentUser",
    "displayName": "String",
    "emailAddress": "String",
    "smsCapablePhoneNumber": "String"
}
```
