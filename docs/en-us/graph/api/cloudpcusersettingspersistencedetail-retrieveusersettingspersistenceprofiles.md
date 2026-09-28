<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcusersettingspersistencedetail-retrieveusersettingspersistenceprofiles?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# cloudPCUserSettingsPersistenceDetail: retrieveUserSettingsPersistenceProfiles

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the user storage list for Cloud PC [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) under the selected Cloud PC policy assignment.

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
GET /deviceManagement/virtualEndpoint/provisioningPolicies/{id}/assignments/{assignment_id}/cloudPCUserSettingsPersistence/retrieveUserSettingsPersistenceProfiles(configurationId='{value}')
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

If successful, this method returns a `200 OK` response code and a collection of [cloudPCUserSettingsPersistenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistenceprofile?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request to retrieve the user storage list for the specific [user settings persistence](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingspersistencedetail?view=graph-rest-beta) of a Cloud PC assignment.

```http
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/provisioningPolicies/bed92b3e-4b42-4be5-af0d-ebb2d96c432f/assignments/e9d4eb36-7056-4161-93a4-2d6f8d20d6c0/cloudPCUserSettingsPersistence/retrieveUserSettingsPersistenceProfiles(configurationId='64ff06de-9c00-4a5a-98b5-7f5abe26bfd9')
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK

{
  "@odata.type": "https://graph.microsoft.com/beta/$metadata#retrieveUserSettingsPersistenceProfiles",
  "value": [
    {
      "profileId": "8fd04a0b-ed49-46c0-a62d-e7980d829058",
      "userPrincipalName": "json@contoso.com",
      "profileSizeInGB": 4,
      "lastProfileAttachedDateTime": "2020-06-03T12:43:32Z",
      "status": "connected"
    },
    {
      "profileId": "95d04a0b-ed49-46c0-a62d-e7980d829058",
      "userPrincipalName": "json@contoso.com",
      "profileSizeInGB": 4,
      "lastProfileAttachedDateTime": null,
      "status": "notConnected"
    },
    {
      "profileId": "12d04a0b-ed49-46c0-a62d-e7980d829058",
      "userPrincipalName": "connie@contoso.com",
      "profileSizeInGB": 4,
      "lastProfileAttachedDateTime": "2020-11-03T12:43:32Z",
      "status": "deleting"
    }
  ]
}
```
