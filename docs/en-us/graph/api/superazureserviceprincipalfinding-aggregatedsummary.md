<!-- Source: https://learn.microsoft.com/en-us/graph/api/superazureserviceprincipalfinding-aggregatedsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# superAzureServicePrincipalFinding: aggregatedSummary

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View the count of super Azure service principals for the specified authorization systems in your Azure environment.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PermissionsAnalytics.Read.OwnedBy | Not available. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/azure/findings/microsoft.graph.superAzureServicePrincipalFinding/microsoft.graph.aggregatedSummary(authorizationSystemIds=['azureAuthSystemId'])
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| authorizationSystemIds | String collection | The collection of IDs for the authorization systems against which to get the summary of records. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [permissionsAnalyticsAggregatedIdentitySummary](https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalyticsaggregatedidentitysummary?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request.

```http
GET GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/azure/findings/microsoft.graph.superAzureServicePrincipalFinding/aggregatedSummary(authorizationSystemIds=['00f7dcae-97f9-492b-af2e-36eb35b613af'])
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.permissionsAnalyticsAggregatedIdentitySummary",
    "totalCount": 7,
    "findingsCount": 1
}
```
