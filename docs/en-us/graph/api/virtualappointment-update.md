<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualappointment-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update virtualAppointment \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The **virtualAppointment** resource and supporting methods are deprecated and will stop returning data on June 30, 2023. We recommend that you update existing apps that use this API to use the new [Get join link](https://learn.microsoft.com/en-us/graph/api/virtualappointment-getvirtualappointmentjoinweburl?view=graph-rest-beta) function.

Update the properties of a [virtualAppointment](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointment?view=graph-rest-beta) object.

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
PATCH /me/onlineMeetings/{onlineMeetingId}/virtualAppointment
PATCH /users/{userId}/onlineMeetings/{onlineMeetingId}/virtualAppointment
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language. Optional. |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| appointmentClients | [virtualAppointmentUser](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentuser?view=graph-rest-beta) collection | The client information for the virtual appointment, including name, email, and SMS phone number. Optional. |
| appointmentClientJoinWebUrl | String | The join web URL of the virtual appointment for clients with waiting room and browser join. Optional. |
| externalAppointmentId | String | The identifier of the appointment from the scheduling system, associated with the current virtual appointment. Optional. |
| externalAppointmentUrl | String | The URL of the appointment resource from the scheduling system, associated with the current virtual appointment. Optional. |
| settings | [virtualAppointmentSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentsettings?view=graph-rest-beta) | The settings associated with the virtual appointment resource. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PATCH https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/virtualAppointment 
Content-Type: application/json
If-Match: W/"ZfYdV7Meckeip07P//nwjAAADyI7NQ=="
Content-length: 379

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

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualAppointment = {
    '@odata.type': '#microsoft.graph.virtualAppointment',
    id: '0c7fda79-ff00-f57f-37e3-28183b6d09b5',
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
    externalAppointmentUrl: 'https://anyschedulingsystem.com/api/appointments/MkADKnAAA=',
    appointmentClientJoinWebUrl: 'https://visit.teams.microsoft.com/webrtc-svc/api/route?tid=a796be92-&convId=19:meeting_=True'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/virtualAppointment')
	.version('beta')
	.update(virtualAppointment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

PATCH returns 412 Precondition Failed if the "If-Match" value doesn't match "ETag" in the virtual appointment.
