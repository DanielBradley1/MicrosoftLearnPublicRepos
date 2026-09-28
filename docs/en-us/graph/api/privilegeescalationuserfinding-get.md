<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegeescalationuserfinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Get privilegeEscalationUserFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of a [privilegeEscalationUserFinding](https://learn.microsoft.com/en-us/graph/api/resources/privilegeescalationuserfinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

List AWS users with privilege escalation:

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.privilegeEscalationUserFinding
```

List GCP users with privilege escalation:

```http
GET /identityGovernance/permissionsAnalytics/gcp/findings/{id}/microsoft.graph.privilegeEscalationUserFinding
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [privilegeEscalationUserFinding](https://learn.microsoft.com/en-us/graph/api/resources/privilegeescalationuserfinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/MSxQcml2aWxlZ2VFc2NhbGF0aW9uVXNlckZpbmRpbmcsNjI4MzQ/microsoft.graph.privilegeEscalationUserFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let privilegeEscalationUserFinding = await client.api('/identityGovernance/permissionsAnalytics/aws/findings/MSxQcml2aWxlZ2VFc2NhbGF0aW9uVXNlckZpbmRpbmcsNjI4MzQ/microsoft.graph.privilegeEscalationUserFinding')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.privilegeEscalationUserFinding/$entity",
    "id": "MSxQcml2aWxlZ2VFc2NhbGF0aW9uVXNlckZpbmRpbmcsNjI4MzQ",
    "createdDateTime": "2023-10-17T23:47:24.056138Z",
    "permissionsCreepIndex": {
        "score": 99
    },
    "identity": {
        "@odata.type": "#microsoft.graph.awsUser",
        "id": "YWx2b2xrb3ZAZ21haWwuY29t",
        "externalId": "alvolkov@gmail.com",
        "displayName": "readonly user1",
        "source": {
            "@odata.type": "#microsoft.graph.awsSource",
            "identityProviderType": "aws",
            "accountId": "956987887735"
        },
        "authorizationSystem": {
            "@odata.type": "#microsoft.graph.awsAuthorizationSystem",
            "authorizationSystemId": "956987887735",
            "authorizationSystemName": "ck-development",
            "authorizationSystemType": "aws",
            "id": "MSxhd3MsOTU2OTg3ODg3NzM1"
        }
    }
}
```
