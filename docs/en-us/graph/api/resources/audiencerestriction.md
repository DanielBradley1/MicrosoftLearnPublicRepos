<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/audiencerestriction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# audienceRestriction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a restriction to block apps based on their signInAudience value.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeActors | [appManagementPolicyActorExemptions](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-beta) | Collection of custom security attribute exemptions. If an actor user or service principal has the custom security attribute defined in this section, they're exempted from the restriction. This means that calls the user or service principal makes to create or update apps are exempt from this policy enforcement. |
| restrictForAppsCreatedAfterDateTime | DateTimeOffset | Specifies the date from which the policy restriction applies to newly created applications. For existing applications, the enforcement date can be retroactively applied. |
| state | appManagementRestrictionState | String value that indicates if the restriction is evaluated. The possible values are: enabled, disabled, and unknownFutureValue. If enabled, the restriction is evaluated. If disabled, the restriction isn't evaluated or enforced. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.audienceRestriction",
  "state": "String",
  "restrictForAppsCreatedAfterDateTime": "String (timestamp)",
  "excludeActors": {
    "@odata.type": "microsoft.graph.appManagementPolicyActorExemptions"
  }
}
```
