<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-companyterms-termsandconditionsassignment-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Create termsAndConditionsAssignment

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) object.

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
POST /deviceManagement/termsAndConditions/{termsAndConditionsId}/assignments
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the termsAndConditionsAssignment object.

The following table shows the properties that are required when you create the termsAndConditionsAssignment.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | Assignment target that the T&C policy is assigned to. |

## Response

If successful, this method returns a `201 Created` response code and a [termsAndConditionsAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-companyterms-termsandconditionsassignment?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/termsAndConditions/{termsAndConditionsId}/assignments
Content-type: application/json
Content-length: 233

{
  "@odata.type": "#microsoft.graph.termsAndConditionsAssignment",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "targetType": "user",
    "entraObjectId": "Entra Object Id value"
  }
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 282

{
  "@odata.type": "#microsoft.graph.termsAndConditionsAssignment",
  "id": "64c1a196-a196-64c1-96a1-c16496a1c164",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "targetType": "user",
    "entraObjectId": "Entra Object Id value"
  }
}
```
