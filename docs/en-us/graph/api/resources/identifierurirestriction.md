<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identifierurirestriction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# identifierUriRestriction resource type

Namespace: microsoft.graph

Configuration object to configure a restriction for [identifier URIs on application objects](https://learn.microsoft.com/en-us/graph/api/resources/identifieruriconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-1.0) | Collection of custom security attribute exemptions. If an actor user or service principal has the custom security attribute defined in this section, they're exempted from the restriction. This means that calls the user or service principal makes to create or update apps are exempt from this policy enforcement. |
| excludeAppsReceivingV2Tokens | Boolean | If `true`, the restriction isn't enforced for applications that are configured to receive V2 tokens in Microsoft Entra ID; else, the restriction is enforced for those applications. |
| excludeSaml | Boolean | If `true`, the restriction isn't enforced for SAML applications in Microsoft Entra ID; else, the restriction is enforced for those applications. |
| isStateSetByMicrosoft | Boolean | If `true`, Microsoft sets the `identifierUriRestriction` state. If `false`, the tenant modifies the `identifierUriRestriction` state. Read-only. |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Specifies the date from which the policy restriction applies to newly created applications. For existing applications, the enforcement date can be retroactively applied. |
| state | appManagementRestrictionState | Indicates if the restriction is evaluated. The possible values are: `enabled`, `disabled`, and `unknownFutureValue`. If `enabled`, the restriction is evaluated. If `disabled`, the restriction isn't evaluated or enforced. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identifierUriRestriction",
  "excludeActors": {
      "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  },
  "excludeAppsReceivingV2Tokens": "Boolean",
  "excludeSaml": "Boolean",
  "isStateSetByMicrosoft": "Boolean",
  "restrictForAppsCreatedAfterDateTime": "String (DateTime)",
  "state": "String"
}
```
