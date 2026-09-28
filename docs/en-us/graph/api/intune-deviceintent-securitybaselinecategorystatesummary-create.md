<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinecategorystatesummary-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create securityBaselineCategoryStateSummary

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/templates/{deviceManagementTemplateId}/microsoft.graph.securityBaselineTemplate/categoryDeviceStateSummaries
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the securityBaselineCategoryStateSummary object.

The following table shows the properties that are required when you create the securityBaselineCategoryStateSummary.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity. Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| secureCount | Int32 | Number of secure devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| notSecureCount | Int32 | Number of not secure devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| unknownCount | Int32 | Number of unknown devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| errorCount | Int32 | Number of error devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| conflictCount | Int32 | Number of conflict devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| notApplicableCount | Int32 | Number of not applicable devices Inherited from [securityBaselineStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinestatesummary?view=graph-rest-beta) |
| displayName | String | The category name |

## Response

If successful, this method returns a `201 Created` response code and a [securityBaselineCategoryStateSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecategorystatesummary?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/templates/{deviceManagementTemplateId}/microsoft.graph.securityBaselineTemplate/categoryDeviceStateSummaries
Content-type: application/json
Content-length: 261

{
  "@odata.type": "#microsoft.graph.securityBaselineCategoryStateSummary",
  "secureCount": 11,
  "notSecureCount": 14,
  "unknownCount": 12,
  "errorCount": 10,
  "conflictCount": 13,
  "notApplicableCount": 2,
  "displayName": "Display Name value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 310

{
  "@odata.type": "#microsoft.graph.securityBaselineCategoryStateSummary",
  "id": "7a650997-0997-7a65-9709-657a9709657a",
  "secureCount": 11,
  "notSecureCount": 14,
  "unknownCount": 12,
  "errorCount": 10,
  "conflictCount": 13,
  "notApplicableCount": 2,
  "displayName": "Display Name value"
}
```
