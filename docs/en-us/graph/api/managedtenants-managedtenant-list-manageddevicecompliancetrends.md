<!-- Source: https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-manageddevicecompliancetrends?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# List managedDeviceComplianceTrends

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.Read.All | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /tenantRelationships/managedTenants/managedDeviceComplianceTrends
```

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response, including `$apply`, `$count`, `$filter`, `$orderby`, `$select`, `$skip`, and `$top`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [managedDeviceComplianceTrend](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-manageddevicecompliancetrend?view=graph-rest-beta) objects in the response body.

## Examples

### Request

```http
GET https://graph.microsoft.com/v1.0/tenantRelationships/managedTenants/managedDeviceComplianceTrends
```

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#tenantRelationships/managedTenants/managedDeviceComplianceTrends",
  "value": [
    {
      "id": "34298981-4fc8-4974-9486-c8909ed1521b_2021-06-12",
      "unknownDeviceCount": 0,
      "compliantDeviceCount": 4,
      "noncompliantDeviceCount": 0,
      "errorDeviceCount": 0,
      "inGracePeriodDeviceCount": 0,
      "configManagerDeviceCount": 0,
      "countDateTime": "2021-06-12",
      "tenantId": "34298981-4fc8-4974-9486-c8909ed1521b",
      "tenantDisplayName": "Fourth Coffee"
    },
    {
      "id": "38227791-a88b-4fcc-81c5-58cf77668320_2021-06-16",
      "unknownDeviceCount": 0,
      "compliantDeviceCount": 1,
      "noncompliantDeviceCount": 4,
      "errorDeviceCount": 0,
      "inGracePeriodDeviceCount": 0,
      "configManagerDeviceCount": 0,
      "countDateTime": "2021-06-16",
      "tenantId": "38227791-a88b-4fcc-81c5-58cf77668320",
      "tenantDisplayName": "Consolidated Messenger"
    }
  ]
}
```
