<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-user-getmanagedappdiagnosticstatuses?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# getManagedAppDiagnosticStatuses function

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Gets diagnostics validation status for a given user. ## Permissions One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) |  |
| **MAM** | DeviceManagementApps.ReadWrite.All, DeviceManagementApps.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application |  |
| **MAM** | DeviceManagementApps.ReadWrite.All, DeviceManagementApps.Read.All |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## HTTP Request

```http
GET /users/{usersId}/getManagedAppDiagnosticStatuses
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [managedAppDiagnosticStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdiagnosticstatus?view=graph-rest-beta) collection in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/users/{usersId}/getManagedAppDiagnosticStatuses
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 249

{
  "value": [
    {
      "@odata.type": "microsoft.graph.managedAppDiagnosticStatus",
      "validationName": "Validation Name value",
      "state": "State value",
      "mitigationInstruction": "Mitigation Instruction value"
    }
  ]
}
```
