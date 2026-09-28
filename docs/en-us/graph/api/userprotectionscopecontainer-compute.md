<!-- Source: https://learn.microsoft.com/en-us/graph/api/userprotectionscopecontainer-compute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# userProtectionScopeContainer: compute

Namespace: microsoft.graph

Compute the data protection policies and actions applicable to a specific user based on their context.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ProtectionScopes.Compute.User | ProtectionScopes.Compute.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ProtectionScopes.Compute.User | ProtectionScopes.Compute.All |

## HTTP request

```http
POST /me/dataSecurityAndGovernance/protectionScopes/compute
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

```http
POST /users/{usersId}/dataSecurityAndGovernance/protectionScopes/compute
```

Note

If you only have the user's **userPrincipalName**, use the following URL to retrieve their object ID.

`GET https://graph.microsoft.com/v1.0/users/{userPrincipalName}?$select=id`

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Client-Request-Id | String \(GUID recommended\). Optional. Unique identifier for this request, which is used for tracing and debugging in logs and support interactions. If an ID isn't provided, one may be generated automatically. We recommend that you specify the ID to make tracing and debugging easier. The same ID that was sent in the request is returned in the response. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| activities | microsoft.graph.security.userActivityTypes | Optional. Flags specifying the user activities the calling application supports or is interested. Possible values are `none`, `uploadText`, `uploadFile`, `downloadText`, `downloadFile, 'unknownFutureValue`. This object is a multi-valued enumeration. |
| deviceMetadata | [deviceMetadata](https://learn.microsoft.com/en-us/graph/api/resources/devicemetadata?view=graph-rest-1.0) | Optional. Information about the user's device \(type, OS\) used for contextual policy evaluation. |
| integratedAppMetadata | [integratedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/integratedapplicationmetadata?view=graph-rest-1.0) | Optional. Information about the calling application \(name, version\) integrating with Microsoft Purview. |
| locations | [policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0) collection | Optional. List of specific locations the application is interested in. If provided, results are trimmed to policies covering these locations. Use [policy location application](https://learn.microsoft.com/en-us/graph/api/resources/policylocationapplication?view=graph-rest-1.0) for application locations, [policy location domain](https://learn.microsoft.com/en-us/graph/api/resources/policylocationdomain?view=graph-rest-1.0) for domain locations, or [policy location URL](https://learn.microsoft.com/en-us/graph/api/resources/policylocationurl?view=graph-rest-1.0) for URL locations. You must specify the `@odata.type` property to declare the type of policyLocation. For example, `"@odata.type": "microsoft.graph.policyLocationApplication"`. |
| pivotOn | microsoft.graph.policyPivotProperty | Optional. Specifies how the results should be aggregated. If omitted or `none`, results might be less aggregated. Possible values are `activity`,`location`, `none`. |

## Response headers

| Name | Description |
| :--- | :--- |
| ETag | An indicator whether the admin-configured policy state changed. If you cached Etag value and it matches ETag from previous results from this API, there's no need to parse the response and cache the parsed results. Cache this value for calls to [process content](https://learn.microsoft.com/en-us/graph/api/userdatasecurityandgovernance-processcontent?view=graph-rest-1.0). |

## Response

If successful, this action returns a `200 OK` response code and a collection of [policyUserScope](https://learn.microsoft.com/en-us/graph/api/resources/policyuserscope?view=graph-rest-1.0) objects in the response body. Each object represents a set of locations and activities governed by a common set of policy actions and execution mode for the specified user.

## Examples

### Example 1: Compute protection scope for an Enterprise app

#### Request

The following example computes the protection scope for a user performing text uploads and downloads.

```http
POST https://graph.microsoft.com/v1.0/users/7c1f8f10-cba8-4a8d-9449-db4b876d1ef70/dataSecurityAndGovernance/protectionScopes/compute
Content-type: application/json
Client-Request-Id: 50dc805c-3af4-42d9-ad16-a746235cc736

{
   "activities": "uploadText,downloadText",
   "locations": [
      {
         "@odata.type": "microsoft.graph.policyLocationApplication",
         "value": "83ef208a-0396-4893-9d4f-d36efbffc8bd"
      }
   ]
}
```

#### Response

The following example shows the response. It indicates that for the `uploadText` activity for the integrated application with id 83ef208a-0396-4893-9d4f-d36efbffc8bd, policies require inline evaluation. For the `uploadFile` activity for the integrated application with id 83ef208a-0396-4893-9d4f-d36efbffc8bd, policies require offline evaluation and trigger a `restrictAccess` action \(likely blocking uploads based on contextual information; for example, blocking uploads for specific users or group\).

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json
Client-Request-Id: 50dc805c-3af4-42d9-ad16-a746235cc736

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.policyUserScope)",
  "value": [
    {
      "activities": "uploadText",
      "executionMode": "evaluateInline",
      "locations": [
        {
          "value": "83ef208a-0396-4893-9d4f-d36efbffc8bd"
        }
      ],
      "policyActions": []
    },
    {
      "activities": "uploadFile",
      "executionMode": "evaluateOffline",
      "locations": [
        {
          "value": "83ef208a-0396-4893-9d4f-d36efbffc8bd"
        }
      ],
      "policyActions": [
        {
            "@odata.type": "#microsoft.graph.restrictAccessAction",
            "action": "restrictAccess",
            "restrictionAction": "block"
        }
     ]
    }
  ]
}
```

### Example 2: Compute protection scope for a network provider app

#### Request

The following example computes the tenant-wide protection scope for text uploads and downloads and file uploads and downloads, interested in a specific application.

```http
POST https://graph.microsoft.com/v1.0/security/dataSecurityAndGovernance/protectionScopes/compute
Content-type: application/json

{
    "activities": "uploadText,downloadText, uploadFile,downloadFile"
}
```

#### Response

The following example shows the response. It indicates that uploadText, downloadText, uploadFile, or downloadFile activities for 'subdomain.domain1.com', 'domain2.com' or 'https://subdomain.domain3.com/content/subcontent' require offline evaluation. UploadText activity for 'subdomain.domain1.com', 'domain2.com' or 'https://subdomain.domain3.com/content/subcontent' require inline evaluation.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.policyTenantScope)",
  "value": [
    {
      "activities": "uploadText,uploadFile,downloadText,downloadFile",
      "executionMode": "evaluateOffline",
      "locations": [
        {
          "@odata.type": "#microsoft.graph.policyLocationDomain",
          "value": "subdomain.domain1.com"
        },
        {
          "@odata.type": "#microsoft.graph.policyLocationDomain",
          "value": "domain2.com"
        },
        {
          "@odata.type": "#microsoft.graph.policyLocationUrl",
          "value": "https://subdomain.domain3.com/content/subcontent"
        }
      ],
      "policyActions": []
    },
    {
      "activities": "uploadText",
      "executionMode": "evaluateInline",
      "locations": [
        {
          "@odata.type": "#microsoft.graph.policyLocationDomain",
          "value": "subdomain.domain1.com"
        },
        {
          "@odata.type": "#microsoft.graph.policyLocationDomain",
          "value": "domain2.com"
        },
        {
          "@odata.type": "#microsoft.graph.policyLocationUrl",
          "value": "https://subdomain.domain3.com/content/subcontent"
        }
      ],
      "policyActions": []
    }
  ]
}
```
