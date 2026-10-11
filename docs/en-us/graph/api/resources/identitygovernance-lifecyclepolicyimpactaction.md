<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyimpactaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyImpactAction resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes a lifecycle policy action taken for a subject during an impact evaluation. Returned in the **actionsTaken** property of a [lifecyclePolicyImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyimpactsummary?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionType | [microsoft.graph.identityGovernance.lifecyclePolicyImpactActionType](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicyimpactactiontype-values) | The type of action taken for the subject. The possible values are: `objectCoveredByPolicy`, `attestationNeededWarning`, `attestationNeededNotificationSent`, `disabledDueToAttestationNonCompliance`, `deletedDueToAttestationNonCompliance`, `unknownFutureValue`. |
| dateTime | DateTimeOffset | The date and time when the action occurred. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyImpactAction",
  "actionType": "String",
  "dateTime": "String (timestamp)"
}
```
