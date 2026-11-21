<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludingagentbuilderplatformssubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# allExcludingAgentBuilderPlatformsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Represents all agent identities except those created through the specified agent builder platforms. Use this type in the **scope** property of an [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-1.0). Inherits from [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludedAgentBuilderPlatforms | microsoft.graph.identityGovernance.agentBuilderPlatforms | The agent builder platforms whose agent identities are excluded from the policy scope. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `microsoftCopilotStudio`, `foundry`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.allExcludingAgentBuilderPlatformsSubjectSet",
  "excludedAgentBuilderPlatforms": "String"
}
```
