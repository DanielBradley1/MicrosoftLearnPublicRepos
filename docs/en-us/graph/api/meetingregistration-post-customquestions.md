<!-- Source: https://learn.microsoft.com/en-us/graph/api/meetingregistration-post-customquestions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create meetingRegistrationQuestion

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [custom registration question](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) associated with a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object on behalf of the organizer.

Tip

You can create custom registration questions in line when you create a meeting registration. For details, see [Create meetingRegistration](https://learn.microsoft.com/en-us/graph/api/meetingregistration-post?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/onlineMeetings/{id}/registration/microsoft.graph.meetingRegistration/customQuestions
```

Tip

To access `/customQuestions`, follow the [example](#example) to cast the type of **registration** to **meetingRegistration**.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the writable properties of a [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) object.

## Response

If successful, this method returns a `201 Created` response code and a [meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistrationquestion?view=graph-rest-beta) object in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/microsoft.graph.meetingRegistration/customQuestions
Content-Type: application/json

{
  "displayName": "What's your job position?",
  "isRequired": false,
  "answerInputType": "text"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const meetingRegistrationQuestion = {
  displayName: 'What\'s your job position?',
  isRequired: false,
  answerInputType: 'text'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration/microsoft.graph.meetingRegistration/customQuestions')
	.version('beta')
	.post(meetingRegistrationQuestion);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('16664f75-11dc-4870-bec6-38c1aaa81431')/onlineMeetings('MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ')/registration/microsoft.graph.meetingRegistration/customQuestions/$entity",
  "id": "MSNhYjc5NWI4MC119zX3gwMDIwX3lvdXJfeDAwMjBfam8=",
  "displayName": "What's your job position?",
  "isRequired": false,
  "answerInputType": "text",
  "answerOptions": []
}
```
