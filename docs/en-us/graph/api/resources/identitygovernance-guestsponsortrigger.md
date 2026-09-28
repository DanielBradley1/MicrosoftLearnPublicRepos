<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-guestsponsortrigger?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# guestSponsorTrigger resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a workflow execution trigger that initiates workflow execution when a guest user has fewer than the required number of sponsors.

This complex type is used in the **trigger** property of the [triggerAndScopeBasedConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerandscopebasedconditions?view=graph-rest-beta) resource.

Inherits from [microsoft.graph.identityGovernance.workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| minimumRequiredSponsors | Int32 | The minimum number of sponsors required for a guest user. When a guest has fewer sponsors than this value, the workflow is triggered. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.guestSponsorTrigger",
  "minimumRequiredSponsors": "Integer"
}
```
