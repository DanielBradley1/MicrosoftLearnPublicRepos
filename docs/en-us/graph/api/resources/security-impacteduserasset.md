<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-impacteduserasset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# impactedUserAsset resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **impactedUserAsset** resource type is deprecated and will be removed on 2026-10-01. Use [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta) and its derived types via `alertTemplate.entityMappings` instead. See the [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) topic for the new shape.

Represents a user account that was identified in an alert triggered by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta).

Inherits from [microsoft.graph.security.impactedAsset](https://learn.microsoft.com/en-us/graph/api/resources/security-impactedasset?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifier | [microsoft.graph.security.userAssetIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#userassetidentifier-values) | Unique identifier for the impacted user asset. The possible values are: `accountObjectId`, `accountSid`, `accountUpn`, `accountName`, `accountDomain`, `accountId`, `requestAccountSid`, `requestAccountName`, `requestAccountDomain`, `recipientObjectId`, `processAccountObjectId`, `initiatingAccountSid`, `initiatingProcessAccountUpn`, `initiatingAccountName`, `initiatingAccountDomain`, `servicePrincipalId`, `servicePrincipalName`, `targetAccountUpn`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.impactedUserAsset",
  "identifier": "String"
}
```
