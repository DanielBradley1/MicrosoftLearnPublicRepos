<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityverificationstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# identityVerificationStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user's overall identity verification state and recent verification events. Each user has one **identityVerificationStatus** object. The service computes its properties from the user's verification events.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/identityverificationstatus-get?view=graph-rest-beta) | [identityVerificationStatus](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationstatus?view=graph-rest-beta) | Read a user's identity verification status and recent verification events. |
| [Create verification event](https://learn.microsoft.com/en-us/graph/api/identityverificationstatus-post-verificationevents?view=graph-rest-beta) | [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) | Record a verification event for a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expiryDateTime | DateTimeOffset | The effective expiry of the user's overall verified state, computed as the latest **expiresDateTime** across active verification events. `null` when no active event has an expiry. Read-only. |
| id | String | The unique identifier of this singleton resource. Equals the owning user's object ID. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastVerifiedDateTime | DateTimeOffset | The date and time of the most recent successful identity verification. `null` when **state** is `unverified`. Read-only. |
| state | [verificationState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#verificationstate-values) | The overall verification state, computed from the most recent active verification event. The possible values are: `unverified`, `verified`, `revoked`, `suspended`, `issued`, `blocked`, `unknownFutureValue`. The service doesn't return an `expired` state; compare **expiryDateTime** with the current time to determine expiry. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| verificationEvents | [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) collection | The user's recent verification events, automatically included when the status is retrieved. Contains up to 10 events, ordered by recency. Older events are removed when the limit is reached. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityVerificationStatus",
  "id": "String (identifier)",
  "state": "String",
  "lastVerifiedDateTime": "String (timestamp)",
  "expiryDateTime": "String (timestamp)"
}
```
