<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-list -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# List copilotPackagePolicyTemplate

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get the available [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate) objects before selecting a policy template for [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepublishresult-publish) or native [Activate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackageactivationresult-activate).

Templates belong to the tenant, not an individual package. This operation returns template metadata, not policy definitions or assignments. A returned template still needs to be applicable to the package being published.

This proposed beta reference doesn't imply publication or deployment. A summary omits saved `policyConfiguration`. Use [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-get) for saved settings and the separate template-bound [policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list) for complete applicable choices. Explicit [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-update) and [Copy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-copy) are separate operations; discovery doesn't modify a template.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |

The target permission contract covers delegated and application callers. Matching backend support and applicable tenant authorization are separate release requirements; permission metadata isn't deployed application-only execution.

## HTTP request

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/policyTemplates
```

This operation returns summaries. [Get policy template](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-get) separately reads one template by its opaque ID.

## Optional query parameters

The existing summary paging contract is unchanged. Follow `@odata.nextLink` when returned rather than treating one page as the complete inventory. This reference doesn't establish a numeric page-size bound.

The single-response completeness and unsupported `$top`/`$skip` rules of [List policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list) apply only to that template-bound catalog, not this summary list.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | Bearer access token. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a `value` collection of [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate) objects in the response body.

## Example

### Request

The following example shows an illustrative request.

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/policyTemplates
```

### Response

The following example shows an illustrative response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "MicrosoftAgentDefaultTemplate",
      "displayName": "Default policy template for agents",
      "description": "Default policy template for agents"
    }
  ]
}
```
