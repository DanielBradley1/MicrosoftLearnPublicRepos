<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# identityVerificationEvent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an identity verification event, including verification facts, lifecycle state, and administrative override details. Events are contained in a user's [identityVerificationStatus](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationstatus?view=graph-rest-beta) and are returned when you [get the status](https://learn.microsoft.com/en-us/graph/api/identityverificationstatus-get?view=graph-rest-beta).

Use the update operation to apply or change an administrative override reason. Verification facts and lifecycle state can't be changed through PATCH.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/identityverificationstatus-post-verificationevents?view=graph-rest-beta) | [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta) | Create a new identityVerificationEvent object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identityverificationevent-update?view=graph-rest-beta) | None | Apply or update an administrative override reason. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityverificationevent-delete?view=graph-rest-beta) | None | Delete an identityVerificationEvent object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique event identifier, supplied by the client on creation. Acts as an idempotency key. Immutable. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lifecycle | [verificationEventLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventlifecycle?view=graph-rest-beta) | The source and current lifecycle state of the event. |
| overrideDetails | [verificationEventOverride](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventoverride?view=graph-rest-beta) | The administrative or programmatic override applied to the event. `null` when no override was applied. |
| verification | [verificationEventDetail](https://learn.microsoft.com/en-us/graph/api/resources/verificationeventdetail?view=graph-rest-beta) | The verification state, provider, credential identifiers, and timestamps. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityVerificationEvent",
  "id": "String (identifier)",
  "verification": {
    "@odata.type": "microsoft.graph.verificationEventDetail"
  },
  "lifecycle": {
    "@odata.type": "microsoft.graph.verificationEventLifecycle"
  },
  "overrideDetails": {
    "@odata.type": "microsoft.graph.verificationEventOverride"
  }
}
```
