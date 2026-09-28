<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcusersettingspersistencedetail-batchcleanupusersettingspersistenceprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudPCUserSettingsPersistenceDetail: batchCleanupUserSettingsPersistenceProfile

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a list of selected [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) profiles that aren't attached to a specific user's Cloud PC in the Cloud PC policy assignment.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/provisioningPolicies/{id}/assignments/{assignment_id}/cloudPCUserSettingsPersistence/batchCleanupUserSettingsPersistenceProfile
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this method.

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudProfileIds | String collection | The list of unique identifiers for specific Cloud PC user settings persistence profiles. |
| configurationId | String | The unique identifier for the Cloud PC user settings persistence configuration. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request to delete user storage profiles from the user settings persistence of a Cloud PC policy assignment.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/provisioningPolicies/bed92b3e-4b42-4be5-af0d-ebb2d96c432f/assignments/e9d4eb36-7056-4161-93a4-2d6f8d20d6c0/cloudPCUserSettingsPersistence/batchCleanupUserSettingsPersistenceProfile
Content-Type: application/json

{
  "configurationId": "64ff06de-9c00-4a5a-98b5-7f5abe26bfd9",
  "cloudProfileIds": ["7e8c3054-bda1-4e37-81c5-7d1b080a8849", "568c3054-bda1-4e37-81c5-7d1b080a8849"]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
