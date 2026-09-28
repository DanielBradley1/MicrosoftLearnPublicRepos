<!-- Source: https://learn.microsoft.com/en-us/graph/api/inactivegroupfinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Get inactiveGroupFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Get details about an [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) object in AWS, Azure, or GCP environments.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Get AWS inactive groups:

```http
GET /identityGovernance/permissionsAnalytics/aws/findings/{id}/microsoft.graph.inactiveGroupFinding
```

Get Azure inactive groups:

```http
GET /identityGovernance/permissionsAnalytics/azure/findings/{id}/microsoft.graph.inactiveGroupFinding
```

Get GCP inactive groups:

```http
GET /identityGovernance/permissionsAnalytics/gcp/findings/{id}/microsoft.graph.inactiveGroupFinding
```

## Optional query parameters

This method doesn't support any OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request for an inactive group in a GCP project.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/gcp/findings/MSxJbmFjdGl2ZUdyb3VwRmluZGluZyw2MDI0NA/microsoft.graph.inactiveGroupFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let inactiveGroupFinding = await client.api('/identityGovernance/permissionsAnalytics/gcp/findings/MSxJbmFjdGl2ZUdyb3VwRmluZGluZyw2MDI0NA/microsoft.graph.inactiveGroupFinding')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/gcp/findings/microsoft.graph.inactiveGroupFinding/$entity",
    "id": "MSxJbmFjdGl2ZUdyb3VwRmluZGluZyw2MDI0NA",
    "createdDateTime": "2023-10-17T15:46:31.448597Z",
    "permissionsCreepIndex": {
        "score": 1
    },
    "actionSummary": {
        "assigned": 3011,
        "exercised": 0,
        "available": 7075
    },
    "group": {
        "@odata.type": "#microsoft.graph.gcpGroup",
        "id": "dGVzdGdyb3VwQGNsb3Vka25veC5pbw",
        "externalId": "testgroup@cloudknox.io",
        "displayName": "testgroup",
        "source": {
            "@odata.type": "#microsoft.graph.gsuiteSource",
            "identityProviderType": "gsuite",
            "domain": "carbide-bonsai-205017"
        },
        "authorizationSystem": {
            "@odata.type": "#microsoft.graph.gcpAuthorizationSystem",
            "authorizationSystemId": "carbide-bonsai-205017",
            "authorizationSystemName": "ck-staging",
            "authorizationSystemType": "gcp",
            "id": "MSxnY3AsY2FyYmlkZS1ib25zYWktMjA1MDE3"
        }
    }
}
```
