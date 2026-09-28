<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-post-webinars?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Create virtualEventWebinar

Namespace: microsoft.graph

Create a new [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object in draft mode.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VirtualEvent.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /solutions/virtualEvents/webinars
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the supported derived types of [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object.

You can specify the following properties when you create a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| audience | meetingAudience | The audience to whom the webinar is visible. The possible values are: `everyone`, `organization`, and `unknownFutureValue`. |
| coOrganizers | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) collection | The identity information of coorganizers of the webinar. |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | A description of the webinar. |
| displayName | String | The display name of the webinar. |
| endDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time when the webinar ends. |
| isRegistrationRequired | Boolean | Indicates whether attendee registration is enabled for the webinar. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). Optional. |
| settings | [virtualEventSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsettings?view=graph-rest-1.0) | The webinar settings. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time when the webinar starts. |

## Response

If successful, this method returns a `201 Created` response code and a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars
Content-Type: application/json

{     
    "displayName": "The Impact of Tech on Our Lives",
    "description": {
      "contentType": "text",
      "content": "Discusses how technology has changed the way we communicate."
    },
    "startDateTime": {
      "dateTime": "2024-03-30T10:00:00", 
      "timeZone": "Pacific Standard Time" 
    },
    "endDateTime": {
      "dateTime": "2024-03-30T17:00:00", 
      "timeZone": "Pacific Standard Time" 
    },
    "audience": "organization",
    "coOrganizers": [
      {
        "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b", 
        "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c" 
      }
    ],
    "settings": {
      "isAttendeeEmailNotificationEnabled": false
    },
    "isRegistrationRequired": true
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventWebinar = {
    displayName:  'The Impact of Tech on Our Lives',
    description:  {
      contentType: 'text',
      content: 'Discusses how technology has changed the way we communicate.'
    },
    startDateTime:  {
      dateTime:  '2024-03-30T10:00:00', 
      timeZone:  'Pacific Standard Time' 
    },
    endDateTime:  {
      dateTime:  '2024-03-30T17:00:00', 
      timeZone:  'Pacific Standard Time' 
    },
    audience:  'organization',
    coOrganizers:  [
      {
        id:  '7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b', 
        tenantId:  '77229959-e479-4a73-b6e0-ddac27be315c' 
      }
    ],
    settings: {
      isAttendeeEmailNotificationEnabled: false
    },
    isRegistrationRequired: true
};

await client.api('/solutions/virtualEvents/webinars')
	.post(virtualEventWebinar);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{ 
    "id": "a57082a9-7629-4f74-8da0-8d621aab4d2d@4aa05bcc-1cac-4a83-a9ae-0db84b88f4ba",
    "status": "draft",
    "displayName": "The Impact of Tech on Our Lives",
    "description": {
      "contentType": "text",
      "content": "Discusses how technology has changed the way we communicate."
    },
    "startDateTime": {
      "dateTime": "2024-03-30T10:00:00", 
      "timeZone": "Pacific Standard Time" 
    },
    "endDateTime": {
      "dateTime": "2024-03-30T17:00:00", 
      "timeZone": "Pacific Standard Time" 
    },
    "audience": "organization",
    "createdBy": {
      "application": null,
      "device": null,
      "user": {
        "id": "b7ef013a-c73c-4ec7-8ccb-e56290f45f68",
        "displayName": "Diane Demoss",
        "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
      }
    },
    "coOrganizers": [
      { 
        "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b", 
        "displayName": "Kenneth Brown", 
        "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c" 
      }
    ],
    "settings": {
      "isAttendeeEmailNotificationEnabled": false
    },
    "isRegistrationRequired": true,
    "externalEventInformation": []
}
```
