<!-- Source: https://learn.microsoft.com/en-us/graph/api/inactiveserverlessfunctionfinding-aggregatedsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# inactiveServerlessFunctionFinding: aggregatedSummary

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

View the raw count of inactive serverless functions in the specified AWS, Azure, or GCP authorization systems.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

For an AWS authorization system:

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.inactiveServerlessFunctionFinding/aggregatedSummary(authorizationSystemIds=['awsAuthSystemId'])
```

For an Azure authorization system:

```http
GET /identityGovernance/permissionsAnalytics/azure/findings/microsoft.graph.inactiveServerlessFunctionFinding/aggregatedSummary(authorizationSystemIds=['azureAuthSystemId'])
```

For a GCP authorization system:

```http
GET /identityGovernance/permissionsAnalytics/gcp/findings/microsoft.graph.inactiveServerlessFunctionFinding/aggregatedSummary(authorizationSystemIds=['gcpAuthSystemId'])
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

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.inactiveServerlessFunctionFinding/microsoft.graph.aggregatedSummary(authorizationSystemIds=['377596131774'])
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let permissionsAnalyticsAggregatedIdentitySummary = await client.api('/identityGovernance/permissionsAnalytics/aws/findings/microsoft.graph.inactiveServerlessFunctionFinding/microsoft.graph.aggregatedSummary(authorizationSystemIds=['377596131774'])')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.permissionsAnalyticsAggregatedIdentitySummary",
    "totalCount": 25,
    "findingsCount": 21
}
```
