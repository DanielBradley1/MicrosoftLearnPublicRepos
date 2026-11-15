<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verificationeventlifecycle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# verificationEventLifecycle resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the source and lifecycle state of an [identityVerificationEvent](https://learn.microsoft.com/en-us/graph/api/resources/identityverificationevent?view=graph-rest-beta). The service manages lifecycle state; event PATCH requests can't update it.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| invalidatedDateTime | DateTimeOffset | The service-populated timestamp for an event in the `invalidated` lifecycle state. Otherwise, `null`. Read-only. |
| source | [verificationLifecycleSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#verificationlifecyclesource-values) | The source that triggered the lifecycle state change. The possible values are: `entra`, `adminOverride`, `apiOverride`, `unknownFutureValue`. Immutable once set. |
| state | [verificationEventLifecycleState](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#verificationeventlifecyclestate-values) | The service-managed lifecycle state. The possible values are: `active`, `revoked`, `suspended`, `invalidated`, `issued`, `blocked`, `unknownFutureValue`. These response values don't make administrative state-changing operations available. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verificationEventLifecycle",
  "source": "String",
  "state": "String",
  "invalidatedDateTime": "String (timestamp)"
}
```
