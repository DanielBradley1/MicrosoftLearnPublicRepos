<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcusersettingspersistencedetail-retrieveusersettingspersistenceprofileusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudPCUserSettingsPersistenceDetail: retrieveUserSettingsPersistenceProfileUsage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the usage of Cloud PC [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) in the selected Cloud PC policy assignment.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | Not available. |

## HTTP request

```http
GET /deviceManagement/virtualEndpoint/provisioningPolicies/{id}/assignments/{assignment_id}/cloudPCUserSettingsPersistence/retrieveUserSettingsPersistenceProfileUsage(configurationId='{value}')
```

## Function parameters

In the request URL, provide the following function parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| configurationId | String | The unique identifier for the selected Cloud PC user's settings persistence. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Response

If successful, this method returns a `200 OK` response code and a [cloudPCUserSettingsPersistenceUsageResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistenceusageresult?view=graph-rest-beta) in the response body.

## Examples

### Request

The following example shows a request to retrieve the specific [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) usage for a Cloud PC policy assignment.

```http
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/provisioningPolicies/bed92b3e-4b42-4be5-af0d-ebb2d96c432f/assignments/e9d4eb36-7056-4161-93a4-2d6f8d20d6c0/cloudPCUserSettingsPersistence/retrieveUserSettingsPersistenceProfileUsage(configurationId='64ff06de-9c00-4a5a-98b5-7f5abe26bfd9')
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#retrieveUserSettingsPersistenceProfileUsage",
  "totalAllocatedStorageInGB": 1200,
  "remainingAvailableStorageInGB": 100,
  "usedStorageInGB": 1100
}
```
