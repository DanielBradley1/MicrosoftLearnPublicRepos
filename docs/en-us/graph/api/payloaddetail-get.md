<!-- Source: https://learn.microsoft.com/en-us/graph/api/payloaddetail-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# Get payloadDetail

Namespace: microsoft.graph

Get an attack simulation campaign payload detail for a tenant.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.Read.All | AttackSimulation.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.Read.All | AttackSimulation.ReadWrite.All |

## HTTP request

```http
GET /security/attackSimulation/payloads/{payloadId}/detail
```

## Optional query parameters

This method doesn't currently support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [payloadDetail](https://learn.microsoft.com/en-us/graph/api/resources/payloaddetail?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/v1.0/security/attackSimulation/payloads/f1b13829-3829-f1b1-2938-b1f12938b1a/detail
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let payloadDetail = await client.api('/security/attackSimulation/payloads/f1b13829-3829-f1b1-2938-b1f12938b1a/detail')
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
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/attackSimulation/payloads/2f5548d1-0dd8-4cc8-9de0-e0d6ec7ea3dc/detail",
  "fromName": "faiza",
  "fromEmail": "faiza@contoso.com",
  "addIsExternalSender": false,
  "subject": "Payload Detail",
  "content": "<meta http-equiv=\"Content-Type\" content=\"text/html>\">",
  "phishingUrl": "http://www.widgetsinc10+.com",
  "coachMarks": [
    {
      "indicator": "URL hyperlinking",
      "description": "URL hyperlinking hides the true URL behind text; the text can also look like another link",
      "language": "en",
      "order": "0",
      "isValid": true,
      "coachmarkLocation": {
        "offset": 144,
        "length": 6,
        "type": "messageBody"
      }
    }
  ]
}
```
