<!-- Source: https://learn.microsoft.com/en-us/graph/api/exchangemessagetrace-getdetailsbyrecipient?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# exchangeMessageTrace: getDetailsByRecipient

Namespace: microsoft.graph

Get a list of [exchangeMessageTraceDetail](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetracedetail?view=graph-rest-1.0) objects filtered on the recipient.

Note

- Before you can use this API, ensure that the [Prerequisites](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetrace?view=graph-rest-1.0#prerequisites) are met.
- This API has a throttling limit of 100 requests per 5 minutes. For more information, see [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ExchangeMessageTrace.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ExchangeMessageTrace.Read.All | Not available. |

## HTTP request

```http
GET /admin/exchange/tracing/messageTraces/{exchangeMessageTraceId}/getDetailsByRecipient(recipientAddress='parameterValue')
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| recipientAddress | String | Required. The SMTP email address of the user that the message was addressed to. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and an [exchangeMessageTraceDetail](https://learn.microsoft.com/en-us/graph/api/resources/exchangemessagetracedetail?view=graph-rest-1.0) collection in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/tracing/messageTraces/7e3b2b2e-1b5e-4b17-80cc-2af6c1d9a3b1/getDetailsByRecipient(recipientAddress='robert@contoso.com')
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getDetailsByRecipient = await client.api('/admin/exchange/tracing/messageTraces/7e3b2b2e-1b5e-4b17-80cc-2af6c1d9a3b1/getDetailsByRecipient(recipientAddress='robert@contoso.com')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.exchangeMessageTraceDetail)",
  "value": [
    {
      "id": "7e3b2b2e-1b5e-4b17-80cc-2af6c1d9a3b1",
      "messageId": "<d9683b4c-127b-413a-ae2e-fa7dfb32c69d@contoso.com>",
      "dateTime": "2025-06-13T10:30:05Z",
      "event": "Receive",
      "action": "",
      "description": "Message received by: MN2PR00MB0670.namprd00.prod.outlook.com",
      "data": "<root><MEP ... String=\"Message Body\" /></root>"
    },
    {
      "id": "7e3b2b2e-1b5e-4b17-80cc-2af6c1d9a3b1",
      "messageId": "<d9683b4c-127b-413a-ae2e-fa7dfb32c69d@contoso.com>",
      "dateTime": "2025-06-13T10:30:10Z",
      "event": "Deliver",
      "action": "",
      "description": "The message was successfully delivered.",
      "data": "<root><MEP ... String=\"Message Body\" /></root>"
    }
  ]
}
```
