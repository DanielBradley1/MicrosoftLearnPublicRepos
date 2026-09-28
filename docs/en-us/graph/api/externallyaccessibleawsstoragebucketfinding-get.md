<!-- Source: https://learn.microsoft.com/en-us/graph/api/externallyaccessibleawsstoragebucketfinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Get externallyAccessibleAwsStorageBucketFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of an [externallyAccessibleAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleawsstoragebucketfinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.externallyAccessibleAwsStorageBucketFinding
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

If successful, this method returns a `200 OK` response code and an [externallyAccessibleAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleawsstoragebucketfinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/MSxFeHRlcm5hbGx5QWNjZXNzaWJsZUF3c1N0b3JhZ2VCdWNrZXRGaW5kaW5nLDI3NjQ3OQ/findings/microsoft.graph.externallyAccessibleAwsStorageBucketFinding
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.externallyAccessibleAwsStorageBucketFinding/$entity",
    "id": "MSxFeHRlcm5hbGx5QWNjZXNzaWJsZUF3c1N0b3JhZ2VCdWNrZXRGaW5kaW5nLDI3NjQ3OQ",
    "createdDateTime": "2023-10-25T19:48:44.050499Z",
    "accessibility": "crossAccount",
    "accountsWithAccess": {
        "@odata.type": "#microsoft.graph.enumeratedAccountsWithAccess"
    },
    "storageBucket": {
        "id": "YXJuOmF3czpzMzo6OmNmLXRlbXBsYXRlcy0xYmZxY2w4c3h0OTUwLXVzLWVhc3QtMg",
        "externalId": "arn:aws:s3:::cf-templates-1bfqcl8sxt950-us-east-2",
        "displayName": "cf-templates-1bfqcl8sxt950-us-east-2",
        "resourceType": "bucket"
    }
}
```
