<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verificationeventoverride?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# verificationEventOverride resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an administrative or programmatic override applied to an [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta). Supply only **reason** when applying an override; the service records the actor and timestamp from the caller's identity.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actorId | String | The object ID of the actor who applied the override. Set by the service from the caller's identity. Read-only. |
| actorType | [verificationActorType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#verificationactortype-values) | The type of actor who applied the override. The possible values are: `user`, `application`, `unknownFutureValue`. Set by the service from the caller's identity. Read-only. |
| overriddenDateTime | DateTimeOffset | The date and time when the override was applied. Set by the service. Read-only. |
| reason | String | The explanation for the override, such as `In-person identity proofing confirmed by help desk`. Maximum 500 characters. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verificationEventOverride",
  "reason": "String",
  "actorType": "String",
  "actorId": "String",
  "overriddenDateTime": "String (timestamp)"
}
```
