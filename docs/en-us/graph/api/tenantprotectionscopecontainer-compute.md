<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantprotectionscopecontainer-compute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# tenantProtectionScopeContainer: compute

Namespace: microsoft.graph

Compute the tenant-wide data protection policies and actions, including user/group scoping.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ProtectionScopes.Compute.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ProtectionScopes.Compute.All | Not available. |

## HTTP request

```http
POST /security/dataSecurityAndGovernance/protectionScopes/compute
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Client-Request-Id | String \(GUID recommended\). Optional. Unique identifier for this request, which is used for tracing and debugging in logs and support interactions. If an ID is not provided, one may be generated automatically. We recommend that you specify the ID to make tracing and debugging easier. The same ID that was sent in the request will be returned in the response. |

## Request body

In the request body, provide JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| activities | microsoft.graph.security.userActivityTypes | Optional. Flags specifying the user activities the calling application supports or is interested. Possible values are `none`, `uploadText`, `uploadFile`, `downloadText`, `downloadFile`, `unknownFutureValue`. This object is a multi-valued enumeration. |
| deviceMetadata | [deviceMetadata](https://learn.microsoft.com/en-us/graph/api/resources/devicemetadata?view=graph-rest-1.0) | Optional. Information about the device context \(type, OS\) used for contextual policy evaluation. Not expected to be used when computing tenant protection scopes |
| integratedAppMetadata | [integratedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/integratedapplicationmetadata?view=graph-rest-1.0) | Optional. Information about the calling application \(name, version\) integrating with Microsoft Purview. |
| locations | [policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0) collection | Optional. List of specific locations the application is interested in. If provided, results are trimmed to policies covering these locations. Use [policy location application](https://learn.microsoft.com/en-us/graph/api/resources/policylocationapplication?view=graph-rest-1.0) for application locations, [policy location domain](https://learn.microsoft.com/en-us/graph/api/resources/policylocationdomain?view=graph-rest-1.0) for domain locations, or [policy location URL](https://learn.microsoft.com/en-us/graph/api/resources/policylocationurl?view=graph-rest-1.0) for URL locations. You must specify the `@odata.type` property to declare the type of policyLocation. For example, `"@odata.type": "microsoft.graph.policyLocationApplication"`. |
| pivotOn | microsoft.graph.policyPivotProperty | Optional. Specifies how the results should be aggregated. If omitted or `none`, results might be less aggregated. Possible values are `activity`,`location`, `none`. |

## Response

If successful, this action returns a `200 OK` response code and a collection of [policyTenantScope](https://learn.microsoft.com/en-us/graph/api/resources/policytenantscope?view=graph-rest-1.0) objects in the response body. Each object represents a set of locations and activities governed by a common set of policy actions and execution mode, along with the user/group bindings for that specific policy configuration.

## Examples

### Request

The following example computes the tenant-wide protection scope for text uploads and downloads, interested in a specific application.

```http
POST https://graph.microsoft.com/v1.0/security/dataSecurityAndGovernance/protectionScopes/compute
Content-type: application/json

{
    "activities": "uploadText,downloadText",
    "locations": [
        {
            "@odata.type": "microsoft.graph.policyLocationApplication",
            "value": "be121c8f-ecd8-4026-b699-669e0ce1bcbf"
        }
    ]
}
```

### Response

The following example shows the response. It indicates that uploadText or downloadText activities "All" users \(tenant scope\) with no exclusions require inline evaluation.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.policyTenantScope)",
    "value": [
        {
            "activities": "uploadText,downloadText",
            "executionMode": "evaluateOffline",
            "policyScope": {
                "inclusions": [
                    {
                        "identity": "All"
                    }
                ],
                "exclusions": [
                ]
            },
            "locations": [
                {
                    "value": "be121c8f-ecd8-4026-b699-669e0ce1bcbf"
                }
            ],
            "policyActions": [
            ]
        }
    ]
}
```
