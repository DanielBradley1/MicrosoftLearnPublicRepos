<!-- Source: https://learn.microsoft.com/en-us/graph/api/superuserfinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Get superUserFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of a [superUserFinding](https://learn.microsoft.com/en-us/graph/api/resources/superuserfinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Get AWS super users:

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.superUserFinding
```

Get Azure super users:

```http
GET /identityGovernance/permissionsAnalytics/azure/findings/{id}/microsoft.graph.superUserFinding
```

Get GCP super users:

```http
GET /identityGovernance/permissionsAnalytics/gcp/findings/{id}/microsoft.graph.superUserFinding
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

If successful, this method returns a `200 OK` response code and a [superUserFinding](https://learn.microsoft.com/en-us/graph/api/resources/superuserfinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/MSxTdXBlclVzZXJGaW5kaW5nLDE1NDczMQ/microsoft.graph.superUserFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let superUserFinding = await client.api('/identityGovernance/permissionsAnalytics/aws/findings/MSxTdXBlclVzZXJGaW5kaW5nLDE1NDczMQ/microsoft.graph.superUserFinding')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.superUserFinding/$entity",
    "id": "MSxTdXBlclVzZXJGaW5kaW5nLDE1NDczMQ",
    "createdDateTime": "2023-10-17T19:49:19.622563Z",
    "actionSummary": {
        "assigned": 10783,
        "exercised": 0,
        "available": 58
    },
    "identityDetails": {
      "createdDateTime": "String (timestamp)",
      "lastActiveDateTime": "String (timestamp)"
    },
    "permissionsCreepIndex": {
        "score": 100
    },
    "identity": {
        "@odata.type": "#microsoft.graph.awsUser",
        "id": "YXJuOmF3czppYW06Ojk1Njk4Nzg4NzczNTp1c2VyL2FzaHlh",
        "externalId": "arn:aws:iam::956987887735:user/ashya",
        "displayName": "ashya",
        "source": {
            "@odata.type": "#microsoft.graph.awsSource",
            "identityProviderType": "aws",
            "accountId": "956987887735"
        },
        "authorizationSystem": {
            "@odata.type": "#microsoft.graph.awsAuthorizationSystem",
            "authorizationSystemId": "956987887735",
            "authorizationSystemName": "contoso-development",
            "authorizationSystemType": "aws",
            "id": "MSxhd3MsOTU2OTg3ODg3NzM1"
        }
    }
}
```
