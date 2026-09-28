<!-- Source: https://learn.microsoft.com/en-us/graph/api/projectrome-put-activity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Create or replace an activity

Namespace: microsoft.graph

Create a new or replace an existing [user activity](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-activity?view=graph-rest-1.0) for your app. If you'd like to create a user activity and its related **activityHistoryItems** in one request, you can use [deep insert](#example-2-deep-insert).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserActivity.ReadWrite.CreatedByApp | Not available. |
| Delegated \(personal Microsoft account\) | UserActivity.ReadWrite.CreatedByApp | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PUT /me/activities/{appActivityId}
```

> **Note:** The appActivityId in the URL needs to be URL-safe \(all characters except for RFC 2396 unreserved characters must be converted to their hexadecimal representation\), but the original appActivityId doesn't have to be URL-safe.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of an [activity](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-activity?view=graph-rest-1.0) object.

## Response

If successful, this method returns the `201 Created` response code if the activity was created or `200 OK` if the activity was replaced.

## Examples

### Example 1: Create an activity

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/me/activities/3F12345
Content-type: application/json

{
  "activitySourceHost": "https://contoso.com",
  "createdDateTime": "2017-06-09T20:54:43.969Z",
  "lastModifiedDateTime": "2017-06-09T20:54:43.969Z",
  "id": "14332800362997268276",
  "appActivityId": "/article?12345",
  "status": "updated",
  "expirationDateTime": "2017-02-26T20:20:48.114Z",
  "visualElements": {
    "displayText": "Contoso How-To: How to Tie a Reef Knot",
    "description": "How to Tie a Reef Knot. A step-by-step visual guide to the art of nautical knot-tying.",
    "attribution": {
      "iconUrl": "https://www.contoso.com/icon",
      "alternateText": "Contoso Ltd",
      "addImageQuery": false
    },
    "backgroundColor": "#ff0000",
    "content": {
      "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
      "type": "AdaptiveCard",
      "body": [
        {
          "type": "TextBlock",
          "text": "Contoso MainPage"
        }
      ]
    }
  },
  "activationUrl": "https://www.contoso.com/article?id=12345"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const userActivity = {
  activitySourceHost: 'https://contoso.com',
  createdDateTime: '2017-06-09T20:54:43.969Z',
  lastModifiedDateTime: '2017-06-09T20:54:43.969Z',
  id: '14332800362997268276',
  appActivityId: '/article?12345',
  status: 'updated',
  expirationDateTime: '2017-02-26T20:20:48.114Z',
  visualElements: {
    displayText: 'Contoso How-To: How to Tie a Reef Knot',
    description: 'How to Tie a Reef Knot. A step-by-step visual guide to the art of nautical knot-tying.',
    attribution: {
      iconUrl: 'https://www.contoso.com/icon',
      alternateText: 'Contoso Ltd',
      addImageQuery: false
    },
    backgroundColor: '#ff0000',
    content: {
      '$schema': 'https://adaptivecards.io/schemas/adaptive-card.json',
      type: 'AdaptiveCard',
      body: [
        {
          type: 'TextBlock',
          text: 'Contoso MainPage'
        }
      ]
    }
  },
  activationUrl: 'https://www.contoso.com/article?id=12345'
};

await client.api('/me/activities/3F12345')
	.put(userActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "activitySourceHost": "https://contoso.com",
  "createdDateTime": "2017-06-09T20:54:43.969Z",
  "lastModifiedDateTime": "2017-06-09T20:54:43.969Z",
  "id": "14332800362997268276",
  "appActivityId": "/article?12345",
  "status": "updated",
  "expirationDateTime": "2017-02-26T20:20:48.114Z",
  "visualElements": {
    "displayText": "Contoso How-To: How to Tie a Reef Knot",
    "description": "How to Tie a Reef Knot. A step-by-step visual guide to the art of nautical knot-tying.",
    "attribution": {
      "iconUrl": "https://www.contoso.com/icon",
      "alternateText": "Contoso, Ltd.",
      "addImageQuery": false
    },
    "backgroundColor": "#ff0000",
    "content": {
      "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
      "type": "AdaptiveCard",
      "body": [
        {
          "type": "TextBlock",
          "text": "Contoso MainPage"
        }
      ]
    }
  },
  "activationUrl": "https://www.contoso.com/article?id=12345",
  "appDisplayName": "Contoso, Ltd.",
  "userTimezone": "Africa/Casablanca",
  "fallbackUrl": "https://www.contoso.com/article?id=12345",
  "contentUrl": "https://www.contoso.com/article?id=12345",
  "contentInfo": {
    "@context": "https://schema.org",
    "@type": "Article",
    "author": "Jennifer Booth",
    "name": "How to Tie a Reef Knot"
  }
}
```

### Example 2: Deep insert

This example creates a new activity and a history item for that activity in one request.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
PUT https://graph.microsoft.com/v1.0/me/activities/12345
Content-type: application/json

{
  "activitySourceHost": "https://contoso.com",
  "createdDateTime": "2017-06-09T20:54:43.969Z",
  "lastModifiedDateTime": "2017-06-09T20:54:43.969Z",
  "id": "14332800362997268276",
  "appActivityId": "/article?12345",
  "status": "updated",
  "expirationDateTime": "2017-02-26T20:20:48.114Z",
  "visualElements": {
    "displayText": "Contoso How-To: How to Tie a Reef Knot",
    "description": "How to Tie a Reef Knot. A step-by-step visual guide to the art of nautical knot-tying.",
    "attribution": {
      "iconUrl": "https://www.contoso.com/icon",
      "alternateText": "Contoso Ltd",
      "addImageQuery": false
    },
    "backgroundColor": "#ff0000",
    "content": {
      "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
      "type": "AdaptiveCard",
      "body": [
        {
          "type": "TextBlock",
          "text": "Contoso MainPage"
        }
      ]
    }
  },
  "historyItems": [
    {
      "userTimezone": "Africa/Casablanca",
      "startedDateTime": "2018-02-26T20:54:04.345Z",
      "lastActiveDateTime": "2018-02-26T20:54:24.345Z"
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const userActivity = {
  activitySourceHost: 'https://contoso.com',
  createdDateTime: '2017-06-09T20:54:43.969Z',
  lastModifiedDateTime: '2017-06-09T20:54:43.969Z',
  id: '14332800362997268276',
  appActivityId: '/article?12345',
  status: 'updated',
  expirationDateTime: '2017-02-26T20:20:48.114Z',
  visualElements: {
    displayText: 'Contoso How-To: How to Tie a Reef Knot',
    description: 'How to Tie a Reef Knot. A step-by-step visual guide to the art of nautical knot-tying.',
    attribution: {
      iconUrl: 'https://www.contoso.com/icon',
      alternateText: 'Contoso Ltd',
      addImageQuery: false
    },
    backgroundColor: '#ff0000',
    content: {
      '$schema': 'https://adaptivecards.io/schemas/adaptive-card.json',
      type: 'AdaptiveCard',
      body: [
        {
          type: 'TextBlock',
          text: 'Contoso MainPage'
        }
      ]
    }
  },
  historyItems: [
    {
      userTimezone: 'Africa/Casablanca',
      startedDateTime: '2018-02-26T20:54:04.345Z',
      lastActiveDateTime: '2018-02-26T20:54:24.345Z'
    }
  ]
};

await client.api('/me/activities/12345')
	.put(userActivity);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "activitySourceHost": "https://contoso.com",
  "createdDateTime": "2017-06-09T20:54:43.969Z",
  "lastModifiedDateTime": "2017-06-09T20:54:43.969Z",
  "id": "14332800362997268276",
  "appActivityId": "/article?12345",
  "status": "updated",
  "expirationDateTime": "2017-02-26T20:20:48.114Z",
  "visualElements": {
    "displayText": "Contoso How-To: How to Tie a Reef Knot",
    "description": "How to Tie a Reef Knot. A step-by-step visual guide to the art of nautical knot-tying.",
    "attribution": {
      "iconUrl": "https://www.contoso.com/icon",
      "alternateText": "Contoso, Ltd.",
      "addImageQuery": false
    },
    "backgroundColor": "#ff0000",
    "content": {
      "$schema": "https://adaptivecards.io/schemas/adaptive-card.json",
      "type": "AdaptiveCard",
      "body": [
        {
          "type": "TextBlock",
          "text": "Contoso MainPage"
        }
      ]
    }
  },
  "activationUrl": "https://www.contoso.com/article?id=12345",
  "appDisplayName": "Contoso, Ltd.",
  "userTimezone": "Africa/Casablanca",
  "fallbackUrl": "https://www.contoso.com/article?id=12345",
  "contentUrl": "https://www.contoso.com/article?id=12345",
  "contentInfo": {
    "@context": "https://schema.org",
    "@type": "Article",
    "author": "Jennifer Booth",
    "name": "How to Tie a Reef Knot"
  },
  "historyItems": [
    {
      "status": "updated",
      "userTimezone": "Africa/Casablanca",
      "createdDateTime": "2018-04-12T21:42:42.495Z",
      "lastModifiedDateTime": "2018-04-12T21:42:42.495Z",
      "id": "61fc8f36-919f-4b73-89d4-1cb7b159d912",
      "startedDateTime": "2018-02-26T20:54:04.345Z",
      "lastActiveDateTime": "2018-02-26T20:54:24.345Z",
      "expirationDateTime": "2018-05-12T21:42:42.495Z",
      "activeDurationSeconds": 20
    }
  ]
}
```
