<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditions-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Create termsAndConditions

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/termsAndConditions
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the termsAndConditions object.

The following table shows the properties that are required when you create the termsAndConditions.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the T&C policy. |
| createdDateTime | DateTimeOffset | DateTime the object was created. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| displayName | String | Administrator-supplied name for the T&C policy. |
| description | String | Administrator-supplied description of the T&C policy. |
| title | String | Administrator-supplied title of the terms and conditions. This is shown to the user on prompts to accept the T&C policy. |
| bodyText | String | Administrator-supplied body text of the terms and conditions, typically the terms themselves. This is shown to the user on prompts to accept the T&C policy. |
| acceptanceStatement | String | Administrator-supplied explanation of the terms and conditions, typically describing what it means to accept the terms and conditions set out in the T&C policy. This is shown to the user on prompts to accept the T&C policy. |
| version | Int32 | Integer indicating the current version of the terms. Incremented when an administrator makes a change to the terms and wishes to require users to re-accept the modified T&C policy. |

## Response

If successful, this method returns a `201 Created` response code and a [termsAndConditions](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditions?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/termsAndConditions
Content-type: application/json
Content-length: 273

{
  "@odata.type": "#microsoft.graph.termsAndConditions",
  "displayName": "Display Name value",
  "description": "Description value",
  "title": "Title value",
  "bodyText": "Body Text value",
  "acceptanceStatement": "Acceptance Statement value",
  "version": 7
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 445

{
  "@odata.type": "#microsoft.graph.termsAndConditions",
  "id": "eefc80cf-80cf-eefc-cf80-fceecf80fcee",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "displayName": "Display Name value",
  "description": "Description value",
  "title": "Title value",
  "bodyText": "Body Text value",
  "acceptanceStatement": "Acceptance Statement value",
  "version": 7
}
```
