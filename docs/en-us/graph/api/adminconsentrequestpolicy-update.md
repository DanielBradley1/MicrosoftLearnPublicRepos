<!-- Source: https://learn.microsoft.com/en-us/graph/api/adminconsentrequestpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update adminConsentRequestPolicy

Namespace: microsoft.graph

Update the properties of an [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ConsentRequest | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ConsentRequest | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Cloud Application Administrator
- Application Administrator

## HTTP request

```http
PUT /policies/adminConsentRequestPolicy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update the [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Specifies whether the admin consent request feature is enabled or disabled. |
| notifyReviewers | Boolean | Specifies whether reviewers will receive notifications. |
| remindersEnabled | Boolean | Specifies whether reviewers will receive reminder emails. |
| requestDurationInDays | Int32 | Specifies the duration the request is active before it automatically expires if no decision is applied. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | The list of reviewers for the admin consent. |

## Response

If successful, this method returns a `204 No content` response code and an updated [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/policies/adminConsentRequestPolicy 
Content-Type: application/json

{
  "isEnabled": true,
  "notifyReviewers": true,
  "remindersEnabled": true,
  "requestDurationInDays": 5,
  "reviewers": [
    {
      "query": "/users/b6879be8-fb87-4482-a72e-18445d2b5c54",
      "queryType": "MicrosoftGraph"
    },
    {
      "query": "/users/b3427cc5-bf69-4dcd-95f7-ed1eb432f5e9",
      "queryType": "MicrosoftGraph"
    }
  ]
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const adminConsentRequestPolicy = {
  isEnabled: true,
  notifyReviewers: true,
  remindersEnabled: true,
  requestDurationInDays: 5,
  reviewers: [
    {
      query: '/users/b6879be8-fb87-4482-a72e-18445d2b5c54',
      queryType: 'MicrosoftGraph'
    },
    {
      query: '/users/b3427cc5-bf69-4dcd-95f7-ed1eb432f5e9',
      queryType: 'MicrosoftGraph'
    }
  ]
};

await client.api('/policies/adminConsentRequestPolicy')
	.put(adminConsentRequestPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
Content-Type: text/plain
```
