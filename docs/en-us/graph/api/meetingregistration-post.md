<!-- Source: https://learn.microsoft.com/en-us/graph/api/meetingregistration-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-15 -->

# Create meetingRegistration \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The meeting registration API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Create and enable registration for an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-beta) on behalf of the organizer. An online meeting can only have one registration enabled.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/onlineMeetings/{id}/registration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language. Optional. |

## Request body

In the request body, supply a JSON representation of a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object.

Important

You must supply the **@odata.type** property to specify the registration type. For more details, see the following [example](#example).

## Response

If successful, this method returns a `201 Created` response code and a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object in the response body.

Note

- The **registrationPageViewCount** property is not returned in the response body of this method. Use the [Get meetingRegistration](https://learn.microsoft.com/en-us/graph/api/meetingregistration-get?view=graph-rest-beta) method to retrieve that property.
- **customQuestions** is a related resource that can only be created in line, but not returned in this method. Use the [Get meetingRegistration](https://learn.microsoft.com/en-us/graph/api/meetingregistration-get?view=graph-rest-beta) or [Get meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/meetingregistrationquestion-get?view=graph-rest-beta) method to retrieve it.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.meetingRegistration",
  "subject":"Microsoft Ignite",
  "description": "Join us November 2–4, 2021 to explore the latest tools, training sessions, technical expertise, networking opportunities, and more.",
  "startDateTime":"2021-11-02T08:00:00-08:00",
  "endDateTime":"2021-11-04T04:00:00-08:00",
  "allowedRegistrant": "everyone",
  "speakers": [
    {
      "displayName": "Henry Ross",
      "bio": "Chairman and Chief Executive Officer"
    },
    {
      "displayName": "Hailey Clark",
      "bio": "EVP"
    }
  ],
  "customQuestions": [
    {
      "displayName": "Are you a developer?",
      "answerInputType": "radioButton",
      "answerOptions": [ "Yes", "No" ],
      "isRequired": true
    },
    {
      "displayName": "Where did you hear about us?",
      "answerInputType": "text",
      "isRequired": false
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const meetingRegistration = {
  '@odata.type': '#microsoft.graph.meetingRegistration',
  subject: 'Microsoft Ignite',
  description: 'Join us November 2–4, 2021 to explore the latest tools, training sessions, technical expertise, networking opportunities, and more.',
  startDateTime: '2021-11-02T08:00:00-08:00',
  endDateTime: '2021-11-04T04:00:00-08:00',
  allowedRegistrant: 'everyone',
  speakers: [
    {
      displayName: 'Henry Ross',
      bio: 'Chairman and Chief Executive Officer'
    },
    {
      displayName: 'Hailey Clark',
      bio: 'EVP'
    }
  ],
  customQuestions: [
    {
      displayName: 'Are you a developer?',
      answerInputType: 'radioButton',
      answerOptions: [ 'Yes', 'No' ],
      isRequired: true
    },
    {
      displayName: 'Where did you hear about us?',
      answerInputType: 'text',
      isRequired: false
    }
  ]
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration')
	.version('beta')
	.post(meetingRegistration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('16664f75-11dc-4870-bec6-38c1aaa81431')/onlineMeetings('MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ')/registration/$entity",
  "@odata.type": "#microsoft.graph.meetingRegistration",
  "id": "gWWckDBR6UOI8_yzWCzeNw,6pAAiSU1bkGqzLnbHG_muA,bzLh6uR-5EGYsCvtvIvs6Q,2Hui7cZ3e0m1BblvyhKFaw,Bcn5itxWh0ui5zRxG26Akw,XCvoVSOmK0e9fivLeKuR_w",
  "registrationPageWebUrl": "https://teams.microsoft.com/registration/gWWckDBR6UOI8_yzWCzeNw,6pABiSU1bkGqzLnbHG_muA,bzLh6uR-5EGYsCvtvIvs6Q,luiTigKrcUGE6Cm33MyQgA,29OIGSH4skyQNu6mNxJr3w,m2bnpmqE_EqwV1Q8dr280E?mode=read&tenantId=eefc0b3a-a334-4fb7-ac60-2f1cf13ec00d",
  "allowedRegistrant": "everyone",
  "subject": "Microsoft Ignite",
  "description": "Join us November 2–4, 2021 to explore the latest tools, training sessions, technical expertise, networking opportunities, and more.",
  "startDateTime": "2021-11-02T016:00:00Z",
  "endDateTime": "2021-11-04T12:00:00Z",
  "registrationPageViewCount": null,
  "speakers": [
    {
      "displayName": "Henry Ross",
      "bio": "Chairman and Chief Executive Officer"
    },
    {
      "displayName": "Hailey Clark",
      "bio": "EVP"
    }
  ]
}
```
