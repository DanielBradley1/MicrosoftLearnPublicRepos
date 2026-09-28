<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualevent-setexternaleventinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# virtualEvent: setExternalEventInformation

Namespace: microsoft.graph

Link external event information to a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) or [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) by setting an **externalEventId**.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VirtualEvent.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

To link external town hall event information to a town hall event:

```http
POST /solutions/virtualEvents/townhalls/{id}/setExternalEventInformation
```

To link external webinar event information to a webinar event:

```http
POST /solutions/virtualEvents/webinars/{id}/setExternalEventInformation
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the **externalEventId** property of the [virtualEventExternalInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0) object.

You can specify the following property when you create the [virtualEventExternalInformation](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| externalEventId | String | The identifier for a **virtualEventExternalInformation** object. Optional. If set, the maximum supported length is 256 characters. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Link external town hall event information to a town hall event

The following example shows how to link external town hall event information to a town hall event by setting an **externalEventId**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/townhalls/a57082a9-7629-4f74-8da0-8d621aab4d2d@4aa05bcc-1cac-4a83-a9ae-0db84b88f4ba/setExternalEventInformation
Content-Type: application/json

{
  "externalEventId": "myExternalEventId"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setExternalEventInformation = {
  externalEventId: 'myExternalEventId'
};

await client.api('/solutions/virtualEvents/townhalls/a57082a9-7629-4f74-8da0-8d621aab4d2d@4aa05bcc-1cac-4a83-a9ae-0db84b88f4ba/setExternalEventInformation')
	.post(setExternalEventInformation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Link external webinar event information to a webinar event

The following example shows how to link external webinar event information to a webinar event by setting an **externalEventId**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/a57082a9-7629-4f74-8da0-8d621aab4d2d@4aa05bcc-1cac-4a83-a9ae-0db84b88f4ba/setExternalEventInformation
Content-Type: application/json

{
  "externalEventId": "myExternalEventId"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setExternalEventInformation = {
  externalEventId: 'myExternalEventId'
};

await client.api('/solutions/virtualEvents/webinars/a57082a9-7629-4f74-8da0-8d621aab4d2d@4aa05bcc-1cac-4a83-a9ae-0db84b88f4ba/setExternalEventInformation')
	.post(setExternalEventInformation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
