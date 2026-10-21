<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/spendingpolicyservicesetting-create -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Create spendingPolicyServiceSetting

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Create a new [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) object to add a service to an existing spending policy. The collection merges by `serviceId`: only the setting in the request body is touched, and settings absent from it are preserved.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Policy.ReadWrite.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /copilot/costManagement/spendingPolicies/{id}/serviceSettings
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |
| `If-Match` | The ETag of the parent spending policy. Required. |

## Request body

In the request body, supply a JSON representation of a [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) object. Required properties are `serviceId` and `state`.

## Response

If successful, this method returns a `201 Created` response code and the created [spendingPolicyServiceSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicyservicesetting) object in the response body. The response includes `Location` and advanced `ETag` headers.

## Example

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/serviceSettings
If-Match: W/"3"
Content-Type: application/json

{
  "serviceId": "researcherCritiqueAndCouncil",
  "state": "enabled"
}
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/serviceSettings/researcherCritiqueAndCouncil
ETag: W/"4"
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/costManagement/spendingPolicies('3f9e2c1a-0000-0000-0000-00000000c21b')/serviceSettings/$entity",
  "serviceId": "researcherCritiqueAndCouncil",
  "state": "enabled",
  "parentStatus": "enabled",
  "parentEtag": "W/\"4\""
}
```
