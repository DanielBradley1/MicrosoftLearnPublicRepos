<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestprincipal -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageRequestPrincipal resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a member of the `assignees` collection in [copilotPackageRequestInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestinfo).

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta&preserve-view=true). The source order and duplicates are preserved. Groups and broad audiences aren't expanded.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `displayName` | String | Nullable. Resolved recipient name. Inherited from `identity`. |
| `id` | String | Nullable. Source recipient identifier. Interpretation depends on `principalType`; not always a navigable directory object. Inherited from `identity`. |
| `principalType` | [copilotPackageRequestPrincipalType](#copilotpackagerequestprincipaltype-enumeration) | Non-nullable. Source principal kind. Missing or unrecognized kinds use `unknownFutureValue` without dropping the recipient. |
| `userPrincipalName` | String | Nullable. Resolved user principal name for `user` or `agentUser` recipients. Null when unavailable and for other kinds; never inferred from email or creator identity. |

### copilotPackageRequestPrincipalType enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following values. Both this read-side enumeration and [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagepublishprincipal) use lowercase `user` and `group`. The agent principal vocabulary differs: this enumeration uses `agentApplication`, while Publish uses `agentIdentity`.

| Value | Description |
| :--- | :--- |
| `user` | A user recipient. |
| `group` | A group recipient. |
| `agentApplication` | An agent application recipient. |
| `agentUser` | An agent user recipient. |
| `unknownFutureValue` | A missing, unrecognized, or future source principal kind. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageRequestPrincipal",
  "displayName": "String",
  "id": "String",
  "principalType": "String",
  "userPrincipalName": "String"
}
```
