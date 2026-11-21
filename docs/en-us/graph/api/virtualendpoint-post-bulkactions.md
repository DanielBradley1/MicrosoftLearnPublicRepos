<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-bulkactions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Create cloudPcBulkAction

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

Note

For delegated access using work or school accounts, the signed-in user must have the `BulkActions/Write` permission and the permissions required for the selected action through [Windows 365 role-based access control](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access), in addition to the Microsoft Graph permission. To create a [cloudPcBulkSetDeviceName](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulksetdevicename?view=graph-rest-beta&preserve-view=true) action, the user must also have `CloudPCs/SetDeviceName`. The **Cloud PC Administrator** role or a custom role that grants these permissions can be used. Supported Microsoft Entra roles include **Windows 365 Administrator** and **Intune Administrator**.

For scoped role assignments, the target Cloud PCs must also be within the user's assigned [scope groups](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access#scope-groups) and [scope tags](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access#scope-tags). These user role requirements don't apply to application-only access.

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/bulkActions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object.

The **cloudPcBulkAction** resource is abstract. Specify a derived type in **@odata.type** to select the action to perform. For example, use `#microsoft.graph.cloudPcBulkSetDeviceName` to set device names by using a template, or `#microsoft.graph.cloudPcBulkPowerOff` to power off Cloud PCs.

You can specify the following properties when you create a **cloudPcBulkAction**.

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcIds | String collection | IDs of the Cloud PCs the bulk action applies to. Individual Cloud PC IDs are GUID-formatted strings. Required. |
| deviceNamingTemplate | String | The naming template for [cloudPcBulkSetDeviceName](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulksetdevicename?view=graph-rest-beta). Required for that derived type. Use an optional prefix followed by one `%RAND:x%` macro, where `x` represents the number of random alphanumeric characters and is at least 5. The generated name must be 5–15 characters long. The prefix can contain ASCII letters, digits, and hyphens, and must not start with a hyphen. The prefix length plus `x` must not exceed 15. For example, `ACRA-%RAND:5%` generates a ten-character name such as `ACRA-A1B2C`. |
| displayName | String | Name of this bulk action. Required. |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the bulk actions can be initiated during maintenance window. When `true`, bulk action will use maintenance window to schedule action, When `false` means bulk action will not use the maintenance window. Default value is `false`. |

## Response

If successful, this method returns a `202 Accepted` response code and a derived [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object in the response body.

The action runs asynchronously after the request is accepted. Use [Get cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/cloudpcbulkaction-get?view=graph-rest-beta) to check its **status** and **actionSummary**. An accepted request doesn't mean that all targeted Cloud PCs completed the action.

## Examples

### Example 1: Power off Cloud PCs

The following example shows how to power off Cloud PCs.

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/bulkActions
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcBulkPowerOff",
  "displayName": "Bulk Power Off by Andy",
  "cloudPcIds": [
    "d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
    "85994912-197b-4927-b569-447bd81350ec"
  ],
  "scheduledDuringMaintenanceWindow": true
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcBulkPowerOff",
  "id": "231ad98f-41b3-872b-dd37-c70bf22cbdac",
  "displayName": "Bulk Power Off by Andy",
  "cloudPcIds": [
    "d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
    "85994912-197b-4927-b569-447bd81350ec"
  ],
  "actionSummary": null,
  "initiatedByUserPrincipalName": "johnd@contoso.com",
  "scheduledDuringMaintenanceWindow": true,
  "status": "pending",
  "createdDateTime": "2024-02-05T10:29:57Z"
}
```

### Example 2: Set device names for Cloud PCs

The following example shows how to create a bulk action to set the device names of two Cloud PCs. The template generates a name with the prefix `ACRA-` followed by five random alphanumeric characters for each Cloud PC.

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/bulkActions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcBulkSetDeviceName",
  "cloudPcIds": [
    "30d0e128-de93-41dc-89ec-33d84bb662a0",
    "7c82a3e3-9459-44e4-94d9-b92f93bf78dd"
  ],
  "deviceNamingTemplate": "ACRA-%RAND:5%",
  "displayName": "Set device names for sales Cloud PCs",
  "scheduledDuringMaintenanceWindow": false
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcBulkSetDeviceName",
  "id": "1d164206-bf41-4fd2-8424-a3192d392273",
  "cloudPcIds": [
    "30d0e128-de93-41dc-89ec-33d84bb662a0",
    "7c82a3e3-9459-44e4-94d9-b92f93bf78dd"
  ],
  "createdDateTime": "2026-10-15T07:00:00Z",
  "deviceNamingTemplate": "ACRA-%RAND:5%",
  "displayName": "Set device names for sales Cloud PCs",
  "scheduledDuringMaintenanceWindow": false,
  "status": "pending"
}
```
