<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualappointment-put?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Create virtualAppointment \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The **virtualAppointment** resource and supporting methods are deprecated and will stop returning data on June 30, 2023. We recommend that you update existing apps that use this API to use the new [Get join link](https://learn.microsoft.com/en-us/graph/api/virtualappointment-getvirtualappointmentjoinweburl?view=graph-rest-beta) function.

Create a new [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Note

Virtual appointment will transition from online meeting permissions to more specific virtual appointment permissions during the preview period. This will give developers more granular control over virtual appointment permissions. We'll provide additional details on when online meeting permissions will no longer be supported before the preview period ends.

## HTTP request

```http
PUT /me/onlineMeetings/{onlineMeetingId}/virtualAppointment
PUT /users/{userId}/onlineMeetings/{onlineMeetingId}/virtualAppointment
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object.

You can specify the following properties when you create a **virtualAppointment**.

| Property | Type | Description |
| :--- | :--- | :--- |
| appointmentClients | [virtualAppointmentUser](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentuser?view=graph-rest-beta) collection | The client information for the virtual appointment, including name, email, and SMS phone number. Optional. |
| appointmentClientJoinWebUrl | String | The join web URL of the virtual appointment for clients with waiting room and browser join. Optional. |
| externalAppointmentId | String | The identifier of the appointment from the scheduling system, associated with the current virtual appointment. Optional. |
| externalAppointmentUrl | String | The URL of the appointment resource from the scheduling system, associated with the current virtual appointment. Optional. |
| settings | [virtualAppointmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentsettings?view=graph-rest-beta) | The settings associated with the virtual appointment resource. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/virtualAppointment
Content-Type: application/json
ETag: W/"ZfYdV7Meckeip07P//nwjAAADyI7NQ=="
Content-length: 379

{
    "@odata.type": "#microsoft.graph.virtualAppointment",
    "settings": {
        "@odata.type": "microsoft.graph.virtualAppointmentSettings",
        "allowClientToJoinUsingBrowser": "true"
    },
    "appointmentClients": [
        {
            "@odata.type": "microsoft.graph.virtualAppointmentUser",
            "emailAddress": "gradya@contoso.com",
            "displayName": "Grady Archie",
            "smsCapablePhoneNumber": "123-456-7890"
        }
    ],
    "externalAppointmentId": "AAMkADKnAAA=",
    "externalAppointmentUrl": "https://anyschedulingsystem.com/api/appointments/MkADKnAAA="
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualAppointment = {
    '@odata.type': '#microsoft.graph.virtualAppointment',
    settings: {
        '@odata.type': 'microsoft.graph.virtualAppointmentSettings',
        allowClientToJoinUsingBrowser: 'true'
    },
    appointmentClients: [
        {
            '@odata.type': 'microsoft.graph.virtualAppointmentUser',
            emailAddress: 'gradya@contoso.com',
            displayName: 'Grady Archie',
            smsCapablePhoneNumber: '123-456-7890'
        }
    ],
    externalAppointmentId: 'AAMkADKnAAA=',
    externalAppointmentUrl: 'https://anyschedulingsystem.com/api/appointments/MkADKnAAA='
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/virtualAppointment')
	.version('beta')
	.put(virtualAppointment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.virtualAppointment",
    "id": "0c7fda79-ff00-f57f-37e3-28183b6d09b5",
    "settings": {
        "@odata.type": "microsoft.graph.virtualAppointmentSettings",
        "allowClientToJoinUsingBrowser": "true"
    },
    "appointmentClients": [
        {
            "@odata.type": "microsoft.graph.virtualAppointmentUser",
            "emailAddress": "gradya@contoso.com",
            "displayName": "Grady Archie",
            "smsCapablePhoneNumber": "123-456-7890"
        }
    ],
    "externalAppointmentId": "AAMkADKnAAA=",
    "externalAppointmentUrl": "https://anyschedulingsystem.com/api/appointments/MkADKnAAA=",
    "appointmentClientJoinWebUrl": "https://visit.teams.microsoft.com/webrtc-svc/api/route?tid=a796be92-&convId=19:meeting_=True"
}
```
