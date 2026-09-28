<!-- Source: https://learn.microsoft.com/en-us/graph/api/awsidentityaccessmanagementkeyusagefinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Get awsIdentityAccessManagementKeyUsageFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of an [awsIdentityAccessManagementKeyUsageFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyusagefinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.awsIdentityAcessManagementKeyUsageFinding
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

If successful, this method returns a `200 OK` response code and an [awsIdentityAccessManagementKeyUsageFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyusagefinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/MSxBd3NJZGVudGl0eUFjY2Vzc01hbmFnZW1lbnRLZXlVc2FnZUZpbmRpbmcsMjEyNjk/microsoft.graph.awsIdentityAcessManagementKeyUsageFinding
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.awsIdentityAccessManagementKeyUsageFinding/$entity",
    "id": "MSxBd3NJZGVudGl0eUFjY2Vzc01hbmFnZW1lbnRLZXlVc2FnZUZpbmRpbmcsMjEyNjk",
    "createdDateTime": "2023-10-25T23:48:12.164332Z",
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
        "id": "QUtJQTU1VUhNS0IzM1hTWFRSNjI",
        "externalId": "AKIA55UHMKB33XSXTR62",
        "displayName": "AKIA55UHMKB33XSXTR62",
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
            "externalId": "arn:aws:iam::956987887735:user/andywang",
            "displayName": "andywang",
            "source": {
                "@odata.type": "#microsoft.graph.awsSource",
                "identityProviderType": "aws",
                "accountId": "956987887735"
            }
        }
    }
}
```
