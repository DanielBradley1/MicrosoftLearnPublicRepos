<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepublishresult-publish -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackage: publish

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Publish the bound package's pending publication request with the selected availability audience and policy template. For a regular package, optionally request acquisition for a separate installation audience.

This reference describes the proposed typed beta contract. Matching schema and backend cutover are required before these wire values are available; source review isn't deployed availability or a v1.0 release.

The service checks existing consent, applies policies, approves the pending publication, applies availability, optionally acquires the package, and publishes its template mapping. This is not [Approve](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-approve) of an individual access or hiring request or native [Activate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackageactivationresult-activate) of a template.

The operation doesn't grant permission consent. Acquisition isn't a promise of client-host installation, instance creation, or effective user access.

Optionally supply a complete `policyConfiguration` for this request. Omit it or supply null to retain saved-template behavior. Customization doesn't [save](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-update) or [copy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-copy) the reusable template.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotPackages.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CopilotPackages.ReadWrite.All | Not available. |

The target contract covers an authorized delegated administrator or application with the existing write permission. Matching receiving-service support must be qualified before use; these declarations don't establish current application-only backend execution.

A non-null `installScope` additionally requires the delegated administrator context. Application-only, missing, or unrecognized caller contexts are rejected before the publication workflow. Application-only installation isn't supported.

## HTTP request

```http
POST https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{id}/publish
```

Use the package's canonical title identifier. The body doesn't accept a second package, tenant, or individual request identifier.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | Bearer token. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |

## Request body

Supply a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| `installScope` | [copilotPackageInstallScope](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageinstallscope) | Optional and nullable. Separate regular-package acquisition audience. Omit or supply null for no added installation calls and no `deploy` result step; this doesn't remove an existing acquisition. |
| `policyConfiguration` | [copilotPackagePolicyConfiguration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepolicyconfiguration) | Optional and nullable. Complete selected policy set used only for this request; omitted/null uses saved template settings. A supplied object replaces the complete set, not an overlay or template update. |
| `policyTemplateId` | String | Required. Opaque identifier of an applicable [policy template](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-list), not a policy definition. |
| `publishEvenIfPolicyFails` | Boolean | Optional; default `false`. If true, an eligible policy-assignment failure can become a warning and publication can continue. Doesn't bypass authorization, consent, or arbitrary failures in other stages. |
| `publishScope` | [copilotPackagePublishScope](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishscope) | Required. Availability audience, separate from acquisition. |
| `version` | String | Optional. Exact pending title version. Omission/null retains versionless lookup, not a promise to select latest; some first-publication titles require a version to resolve. |

`publishScope.scope` accepts `everyone`, `specificUsers`, or `noOne`. Explicit principals use [copilotPackagePublishPrincipal](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishprincipal); output and request literals follow the public camelCase enum vocabulary, not native provider enum names.

The HTTP body has six parameters. The schema declares seven parameters in total, including the package binding supplied through the route rather than another body identifier.

Read [saved template detail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicytemplate-get) and the complete template-bound [policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list) before choosing overrides. Include all applicable mandatory families. Default and optional families may be omitted; within every selected family, include all required choices. An explicit empty `policies` set is valid only when no applicable mandatory family exists. Invalid configuration is rejected before publication effects.

Configured choices use supported Boolean, Int32, String, Int32-collection, or String-collection values with explicit `@odata.type`; Boolean false and integer zero aren't omission. Reference-only choices require an omitted/null value. Configurable choices require a non-null typed value satisfying trusted constraints.

Request-local overrides don't Save-existing or Save-as-new. A later native [Activate](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackageactivationresult-activate) still requires `policyTemplateId` and reads fresh saved settings for that ID. It doesn't automatically reuse a prior Publish configuration or accept an ID-less activation.

Optional `publishScope.policyType` is `allowAccess` or `allowOnboarding`; omission/null defaults to `allowAccess`. It selects the availability policy category, not a per-policy workload such as Defender or Purview. The strict typed contract requires the corresponding backend admission to be enabled at cutover; acceptance of historical legacy strings isn't proof of this contract.

For `installScope`, `everyone` requires explicit `principals: []`, and `specificUsers` requires one or more `user`/`group` entries with nonzero hyphenated object GUIDs. Missing/null collections, nonempty `everyone`, empty `specificUsers`, unsupported/unknown enum inputs, malformed identifiers, and `policyType` inside `installScope` are rejected. Every principal is validated before set-based duplicate normalization.

Installation-selected requests require a verified canonical package/version, regular-package type, and any required persisted instance identity before publication mutations. A selected instance missing that identity is rejected before policy assignment or approval. The service verifies the exact materialized target again after approval; it doesn't use a new preview lookup that can upgrade an acquired version.

An initially positive already-deployed decision is retained. A later exact-version runtime read can add a positive skip but can't clear an earlier deployment or upgrade-consent signal using default values or state that wasn't computed. The supplied acquisition audience isn't applied when deployment is skipped. These are snapshots, not atomic concurrency guards.

If target verification fails after approval, the request returns a non-2xx Graph error without `stepResults`; the pending publication may already be approved. No later availability, acquisition, or template calls or automatic retry follow, and earlier effects aren't rolled back.

## Response

If successful, this method returns `200 OK` and a [copilotPackagePublishResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishresult), not an updated package.

The result's `stepResults` records attempted stages in execution order:

1. `validateRequest`
2. `loadRequestedAgent`
3. `validatePermissionConsent`
4. `assignPolicies`
5. `approve`
6. `allow`
7. Optional `deploy`
8. `publishAgentForTemplate`

Omitted/null installation has no `deploy` entry. For valid installation, `deploy` follows `allow` and precedes template mapping. Its outcome is `succeeded` for acquisition completion or `skipped` for positive existing-deployment evidence. A skipped deployment reports `operationStatus: "success"` and null `errorMessage`; it isn't an acquisition effect or audience replacement.

Step `outcome` describes execution \(`succeeded`, `warning`, `failed`, `skipped`\); step `operationStatus` is a backend-neutral business reason. Neither is an HTTP status. No aggregate `statusCode` or provider-category field is part of this result.

Inspect policy and step results even on HTTP 200. A tolerated policy warning or skipped policy doesn't mean all policies were applied. Unknown business values use their enum's `unknownFutureValue`; missing nullable values remain distinct. Don't rely on undocumented preference-header behavior.

Acquisition sets/replaces the administrator-acquisition audience for the selected version and propagates asynchronously, rather than adding recipients or guaranteeing host completion. To change an already-deployed audience, use [Update package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-update) separately.

The workflow isn't transactional. Failed or interrupted requests can have completed earlier effects. Failures use a neutral Graph error envelope without `stepResults`; don't parse an internal operation object serialized into `error.message` as a supported response property. Reconcile current package state before another attempt; no blind replay or rollback guarantee is introduced.

## Examples

### Example 1: Publish for everyone and install for specific user and group

#### Request

The following request publishes availability for everyone and separately requests acquisition for a user and a group. Replace the sample identifiers with the intended package, template, and object IDs.

```http
POST https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{package-id}/publish
Content-Type: application/json

{
  "version": "1.0.0",
  "publishScope": {
    "scope": "everyone",
    "principals": [],
    "policyType": "allowAccess"
  },
  "policyTemplateId": "contoso-agent-policy-template",
  "publishEvenIfPolicyFails": false,
  "installScope": {
    "scope": "specificUsers",
    "principals": [
      { "id": "11111111-1111-4111-8111-111111111111", "type": "user" },
      { "id": "22222222-2222-4222-8222-222222222222", "type": "group" }
    ]
  }
}
```

#### Response

This response shows the final three stages when the target was already deployed. Earlier stages and optional nested details are omitted. No acquisition call occurred and the supplied user/group installation audience wasn't applied.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "errorMessage": null,
  "stepResults": [
    { "step": "allow", "outcome": "succeeded", "operationStatus": "success", "errorMessage": null },
    { "step": "deploy", "outcome": "skipped", "operationStatus": "success", "errorMessage": null },
    { "step": "publishAgentForTemplate", "outcome": "succeeded", "operationStatus": "success", "errorMessage": null }
  ]
}
```

### Example 2: Customize policies without saving the template

#### Request

This illustrative request selects values from the example catalog in [List policy definitions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagepolicydefinition-list). It uses a complete selected set for this request only; no template Save or Copy occurs. Acquisition isn't requested because `installScope` is omitted.

```http
POST https://graph.microsoft.com/beta/copilot/admin/catalog/packages/{package-id}/publish
Content-Type: application/json

{
  "publishScope": {
    "scope": "everyone",
    "principals": [],
    "policyType": "allowAccess"
  },
  "policyTemplateId": "example-template",
  "version": "1.0.0",
  "publishEvenIfPolicyFails": false,
  "policyConfiguration": {
    "policies": [
      {
        "policyDefinitionId": "example-family",
        "selections": [
          {
            "choiceId": "example-boolean-choice",
            "value": {
              "@odata.type": "#microsoft.graph.copilotPackagePolicyBooleanValue",
              "value": true
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

#### Response

The response uses the same [copilotPackagePublishResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishresult) contract. These sample identifiers and values aren't evidence of deployed routing or known-valid live targets.
