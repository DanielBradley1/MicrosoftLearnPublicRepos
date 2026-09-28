<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# virtualAppointment resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Virtual appointment resource and supporting methods are deprecated and will stop returning data on June 30, 2023. We recommend that you update existing apps that use this API to the new [Get Virtual appointment join link](https://learn.microsoft.com/en-us/graph/api/virtualappointment-getvirtualappointmentjoinweburl?view=graph-rest-beta) function.

Represents information about a virtual appointment, including the client join URL, settings, and the client information. Virtual appointments are designed for business to consume online workflows and include enhanced features such as mobile browser join and client waiting room.

Note

For the preview period, customers with access to virtual appointments with their Microsoft 365 licenses benefit from unlimited virtual appointment calls via the Microsoft Graph API. We'll provide additional details on the licensing requirements before the preview period ends.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create virtual appointment \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/virtualappointment-put?view=graph-rest-beta) | [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) | Create a new [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object. |
| [Get virtual appointment \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/virtualappointment-get?view=graph-rest-beta) | [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) | Read the properties and relationships of a [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object. |
| [Update virtual appointment \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/virtualappointment-update?view=graph-rest-beta) | None | Update the properties of a [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object. |
| [Delete virtual appointment \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/virtualappointment-delete?view=graph-rest-beta) | None | Delete a [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object. |

Tip

When you create a virtual appointment resource for the first time in a tenant, the request returns a `409 Conflict` response code with a retry header that indicates how long a caller should wait before making the request again. The service provisioning takes less than five minutes. This step is only required once per customer tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appointmentClients | [virtualAppointmentUser](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentuser?view=graph-rest-beta) collection | The client information for the virtual appointment, including name, email, and SMS phone number. Optional. |
| appointmentClientJoinWebUrl | String | The join web URL of the virtual appointment for clients with waiting room and browser join. Optional. |
| externalAppointmentId | String | The identifier of the appointment from the scheduling system, associated with the current virtual appointment. Optional. |
| externalAppointmentUrl | String | The URL of the appointment resource from the scheduling system, associated with the current virtual appointment. Optional. |
| settings | [virtualAppointmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentsettings?view=graph-rest-beta) | The settings associated with the virtual appointment resource. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.virtualAppointment",
    "appointmentClients": [
        {
            "@odata.type": "microsoft.graph.virtualAppointmentUser"
        }
    ],
    "appointmentClientJoinWebUrl": "String",
    "externalAppointmentId": "String",
    "externalAppointmentUrl": "String",
    "id": "String (identifier)",
    "settings": {
        "@odata.type": "microsoft.graph.virtualAppointmentSettings"
    }
}
```
