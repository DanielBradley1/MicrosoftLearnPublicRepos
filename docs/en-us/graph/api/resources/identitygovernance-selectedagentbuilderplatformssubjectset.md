<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-selectedagentbuilderplatformssubjectset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# selectedAgentBuilderPlatformsSubjectSet resource type

Namespace: microsoft.graph.identityGovernance

Represents an inclusion scope that selects agent identities created by one or more agent builder platforms. Use this type in the **scope** property of an [agentIdentityLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecyclepolicy?view=graph-rest-1.0) resource. This type is valid only for agent identity lifecycle policies; using it with another lifecycle policy type returns `400 Bad Request`.

Inherits from [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includedAgentBuilderPlatforms | microsoft.graph.identityGovernance.agentBuilderPlatforms | The agent builder platforms whose agent identities are included in the policy scope. This flags enumeration supports combining values in a comma-separated string. An agent is included when its builder platform matches any selected value. The possible values are: `microsoftCopilotStudio`, `foundry`, `unknownFutureValue`. You must specify at least one supported value. The `unknownFutureValue` value is reserved for future use and isn't supported in create or update requests. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.selectedAgentBuilderPlatformsSubjectSet",
  "includedAgentBuilderPlatforms": "String"
}
```
