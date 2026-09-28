<!-- Source: https://learn.microsoft.com/en-us/graph/api/opennetworkazuresecuritygroupfinding-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# Get openNetworkAzureSecurityGroupFinding

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Read the properties and relationships of an [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /identityGovernance/permissionsAnalytics/azure/findings/{id}/microsoft.graph.openNetworkAzureSecurityGroupFinding
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

If successful, this method returns a `200 OK` response code and an [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/identityGovernance/permissionsAnalytics/azure/findings/MSxPcGVuTmV0d29ya0F6dXJlU2VjdXJpdHlHcm91cEZpbmRpbmcsMjIyNjk1/microsoft.graph.openNetworkAzureSecurityGroupFinding
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let openNetworkAzureSecurityGroupFinding = await client.api('/identityGovernance/permissionsAnalytics/azure/findings/MSxPcGVuTmV0d29ya0F6dXJlU2VjdXJpdHlHcm91cEZpbmRpbmcsMjIyNjk1/microsoft.graph.openNetworkAzureSecurityGroupFinding')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/permissionsAnalytics/azure/findings/microsoft.graph.openNetworkAzureSecurityGroupFinding/$entity",
    "id": "MSxPcGVuTmV0d29ya0F6dXJlU2VjdXJpdHlHcm91cEZpbmRpbmcsMjIyNjk1",
    "createdDateTime": "2023-10-25T19:47:57.589627Z",
    "inboundPorts": {
        "@odata.type": "#microsoft.graph.enumeratedInboundPorts",
        "ports": [
            "22"
        ]
    },
    "securityGroup": {
        "id": "L3N1YnNjcmlwdGlvbnMvNmJkZWIzNmUtMjQxNS00ZjdlLWFjMDMtNDljNTE4ZGEwZTEwL3Jlc291cmNlR3JvdXBzL21jaWVtLXN1YnNjcmlwdGlvbi0xLXJlc291cmNlLWdyb3VwL3Byb3ZpZGVycy9NaWNyb3NvZnQuTmV0d29yay9uZXR3b3JrU2VjdXJpdHlHcm91cHMvRXZhbk9wZW5TZWN1cml0eUdyb3Vw",
        "externalId": "/subscriptions/6bdeb36e-2415-4f7e-ac03-49c518da0e10/resourceGroups/mciem-subscription-1-resource-group/providers/Microsoft.Network/networkSecurityGroups/EvanOpenSecurityGroup",
        "displayName": "mciem-subscription-1-resource-group//subscriptions/6bdeb36e-2415-4f7e-ac03-49c518da0e10/resourceGroups/mciem-subscription-1-resource-group/providers/Microsoft.Network/networkSecurityGroups/EvanOpenSecurityGroup",
        "resourceType": "networkSecurityGroups"
    }
}
```
