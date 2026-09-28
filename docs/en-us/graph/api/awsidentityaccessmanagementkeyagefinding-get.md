<!-- Source: https://learn.microsoft.com/en-us/graph/api/awsidentityaccessmanagementkeyagefinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Get awsIdentityAccessManagementKeyAgeFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of an [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.awsIdentityAccessManagementKeyAgeFinding
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

If successful, this method returns a `200 OK` response code and an [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/MSxBd3NJZGVudGl0eUFjY2Vzc01hbmFnZW1lbnRLZXlBZ2VGaW5kaW5nLDIyMDE4/microsoft.graph.awsIdentityAccessManagementKeyAgeFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let awsIdentityAccessManagementKeyAgeFinding = await client.api('/identityGovernance/permissionsAnalytics/aws/findings/MSxBd3NJZGVudGl0eUFjY2Vzc01hbmFnZW1lbnRLZXlBZ2VGaW5kaW5nLDIyMDE4/microsoft.graph.awsIdentityAccessManagementKeyAgeFinding')
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
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.awsIdentityAccessManagementKeyAgeFinding/$entity",
    "id": "MSxB...aW5nLDIyMDE4",
    "createdDateTime": "2023-10-25T23:48:12.102767Z",
    "status": "inactive",
    "permissionsCreepIndex": {
        "score": 4
    },
    "actionSummary": {
        "assigned": 4161,
        "exercised": 0,
        "available": 58
    },
    "accessKey": {
        "id": "QUtJQ...FRSNjI",
        "externalId": "AKIA55.....62",
        "displayName": "AKIA55.....62",
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
        },
        "owner": {
            "id": "YXJuOmF3czppYW06Ojk1Njk4Nzg4NzczNTp1c2VyL2FuZHl3YW5n",
            "externalId": "arn:aws:iam::956987887735:user/contoso",
            "displayName": "contoso",
            "source": {
                "@odata.type": "#microsoft.graph.awsSource",
                "identityProviderType": "aws",
                "accountId": "956987887735"
            }
        }
    }
}
```
