<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-get -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# Get copilotPackagePolicyTemplate

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Read one tenant [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate), including its saved `policyConfiguration`. Use its opaque identifier from [List policy templates](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-list).

This proposed contract isn't evidence of deployed availability. Declared delegated and application permission coverage requires matching receiving-service support before either path can be used.

Saved selections are separate from the complete applicable definitions and choices returned by [List policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list). Template summaries omit `policyConfiguration`; omission in a summary doesn't mean the saved template is unconfigured.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotPackages.Read.All | CopilotPackages.ReadWrite.All |

Permission metadata doesn't establish current application-only backend execution or bypass applicable tenant authorization.

## HTTP request

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/policyTemplates/{policyTemplateId}
```

The key identifies a template in the authenticated tenant, not a package, policy family, or individual choice.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | Bearer token. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns `200 OK` and one [copilotPackagePolicyTemplate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicytemplate), not a `value` collection.

A null `policyConfiguration` means the saved template was verified as unconfigured. Unavailable or malformed saved configuration returns an error, not null or an invented empty configuration. Displayed values don't include all source metadata and must not be used to reconstruct a [server-side copy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-copy).

## Example

The identifiers and selected values below illustrate the proposed contract, not a live response. The saved configuration contains a Boolean `false` and integer `0`; both are present values, not omitted settings.

### Request

```http
GET https://graph.microsoft.com/beta/copilot/admin/catalog/policyTemplates/example-template
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "example-template",
  "displayName": "Example custom template",
  "description": null,
  "policyConfiguration": {
    "policies": [
      {
        "policyDefinitionId": "example-family",
        "selections": [
          {
            "choiceId": "example-boolean-choice",
            "value": {
              "@odata.type": "#microsoft.graph.copilotPackagePolicyBooleanValue",
              "value": false
            }
          },
          {
            "choiceId": "example-integer-choice",
            "value": {
              "@odata.type": "#microsoft.graph.copilotPackagePolicyIntegerValue",
              "value": 0
            }
          }
        ]
      }
    ]
  }
}
```
