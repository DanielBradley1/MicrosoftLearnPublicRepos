<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-incident-post-comments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# Create comment

Namespace: microsoft.graph

Create a comment for an existing [incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) based on the specified incident **id** property.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIncident.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIncident.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Operator
- Security Administrator

## HTTP request

```http
POST /security/incidents/{incidentId}/comments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, use `@odata.type` to specify the parameter type of [alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0), and provide a JSON object for the parameter, `comment`. See an [example](#examples).

| Parameter | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment to be added. |

## Response

If successful, this method returns a `200 OK` response code and an updated list of all [alertComment](https://learn.microsoft.com/en-us/graph/api/resources/security-alertcomment?view=graph-rest-1.0) resources of the incident.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/security/incidents/3962396/comments
Content-Type: application/json

{
    "@odata.type": "microsoft.graph.security.alertComment",
    "comment": "Demo for docs"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alertComment = {
    '@odata.type': 'microsoft.graph.security.alertComment',
    comment: 'Demo for docs'
};

await client.api('/security/incidents/3962396/comments')
	.post(alertComment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/alerts_v2('da637865765418431569_-773071023')/comments",
    "value": [
        {
            "comment": "test",
            "createdByDisplayName": "secAdmin@contoso.com",
            "createdDateTime": "2022-10-13T07:08:45.4626766Z"
        },
        {
            "comment": "Demo for docs",
            "createdByDisplayName": "secAdmin@contoso.com",
            "createdDateTime": "2022-10-13T07:08:50.5821324Z"
        }
    ]
}
```
