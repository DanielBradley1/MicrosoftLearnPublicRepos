<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-allexcludingagentbuilderplatformssubjectset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# allExcludingAgentBuilderPlatformsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents all agent identities except those created through the specified agent builder platforms. Use this type in the **scope** property of an [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-beta). Inherits from [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta).

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
