<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessdriftsummary-list-details?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# List details

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the access drift details from the **details** navigation property of an [accessDriftSummary](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftsummary?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.Read.All | EntitlementManagement.ReadWrite.All |

Tip

For delegated access using a work or school account, the signed-in user must have access to the relevant entitlement management catalog. The least privileged [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) is *Catalog reader*.

When the request identifies a catalog, access is evaluated for that catalog. Otherwise, the results are limited to catalogs that the signed-in user can access.

In app-only scenarios, the calling app must have the `EntitlementManagement.Read.All` or `EntitlementManagement.ReadWrite.All` application permission. An entitlement management catalog role doesn't replace the required application permission.

## HTTP request

```http
GET /identityGovernance/insights/accessDriftSummary/{accessDriftSummary-id}/details
```

## Optional query parameters

This method supports the `$filter`, `$search`, `$top`, `$skip`, `$orderby`, and `$count` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

The `$filter` parameter supports the `isof('microsoft.graph.entraAccessDriftDetail')` expression to return details from the Microsoft Entra drift source.

The `$search` parameter performs a case-insensitive substring search against `identities/principalName` and `accessPackage/displayName`. For example, `$search=conto` matches an identity principal name that contains `contoso.com`.

The `$orderby` parameter supports `createdDateTime`, `driftType`, `microsoft.graph.entraAccessDriftDetail/assignedRole`, and `microsoft.graph.entraAccessDriftDetail/expectedRole`. You can combine multiple properties and specify `asc` or `desc` for each one. The `identities` relationship is collection-valued, so its child properties don't support `$orderby`.

The maximum value for `$top` is `5000`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/identityGovernance/insights/accessDriftSummary/v1_e4c2b24ce2c799a6ce199b1988b8fbf880766cdf21a3d288743082c3822b06f2/details?$filter=isof('microsoft.graph.entraAccessDriftDetail')&$search=conto&$orderby=createdDateTime desc,driftType asc
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.entraAccessDriftDetail",
      "id": "39d6711c-56ce-aeb3-8079-4f288e363a5f",
      "resource": {
        "@odata.type": "#microsoft.graph.applicationDriftResourceInfo",
        "catalogName": "Business applications",
        "identifier": "app-xyz-001",
        "displayName": "Salesforce",
        "type": "application",
        "catalogIdentifier": "cat-001"
      },
      "driftSource": "entra",
      "driftType": "unauthorized",
      "createdDateTime": "2026-04-27T03:15:42Z",
      "assignedRole": "User",
      "expectedRole": "None",
      "accessPackage": {
        "@odata.type": "#microsoft.graph.driftAccessPackageInfo",
        "identifier": "pkg-sales-001",
        "displayName": "Salesforce Access"
      },
      "identities": [
        {
          "@odata.type": "#microsoft.graph.entraDriftIdentityInfo",
          "identifier": "user-001",
          "principalName": "user@contoso.com",
          "displayName": "User One",
          "identityType": "user"
        }
      ]
    }
  ]
}
```
