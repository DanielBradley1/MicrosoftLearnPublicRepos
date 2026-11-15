<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpc-setdevicename?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# cloudPC: setDeviceName

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Set the operating system device name of a [Cloud PC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta). This action runs asynchronously and changes the computer name, not the **displayName** property. To change the display name, use [rename](https://learn.microsoft.com/en-us/graph/api/cloudpc-rename?view=graph-rest-beta).

This action supports Windows 365 Enterprise and Windows 365 Flex \(formerly Frontline\) Cloud PCs in dedicated mode. Use [getSupportedCloudPcRemoteActions](https://learn.microsoft.com/en-us/graph/api/cloudpc-getsupportedcloudpcremoteactions?view=graph-rest-beta) to check whether the action is available for a Cloud PC.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

Note

For delegated access using work or school accounts, the signed-in user must have the `CloudPCs/SetDeviceName` permission through [Windows 365 role-based access control](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access), in addition to the Microsoft Graph permission. The **Cloud PC Administrator** role or a custom role that grants this permission can be used. Supported Microsoft Entra roles include **Windows 365 Administrator** and **Intune Administrator**.

For scoped role assignments, the target Cloud PC must also be within the user's assigned [scope groups](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access#scope-groups) and [scope tags](https://learn.microsoft.com/en-us/windows-365/enterprise/role-based-access#scope-tags). These user role requirements don't apply to application-only access.

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/cloudPCs/{cloudPC-id}/setDeviceName
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| deviceName | String | The device name to assign to the Cloud PC. Required. Must be 5–15 characters and contain only ASCII letters, digits, or hyphens. The name must not consist entirely of digits and must be unique within the tenant. Use a name that doesn't start with a hyphen. |

## Response

If successful, this action returns a `204 No Content` response code. A successful response doesn't mean that the device name changed or that Intune synchronized the change. Use [retrieveCloudPcRemoteActionResults](https://learn.microsoft.com/en-us/graph/api/cloudpc-retrievecloudpcremoteactionresults?view=graph-rest-beta) to check the remote action result.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/b0a9cde2-e170-4dd9-97c3-ad1d3328a711/setDeviceName
Content-Type: application/json

{
  "deviceName": "CPC-SALES01"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
