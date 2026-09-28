<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentic-agentsignin?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# agentSignIn resource type

Namespace: microsoft.graph.agentic

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

For agentic sign-ins, provides information about the agent. This object is configured in the **agent** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta) and [summarizedSignIn](https://learn.microsoft.com/en-us/graph/api/resources/summarizedsignin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agentSubjectParentId | String | The subject's parent object ID. This is either the **id** of the **agentIdentity** or **agentIdentityBlueprint**. |
| agentSubjectType | microsoft.graph.agentic.agentType | The type of the subject that requested the token. The possible values are: `notAgentic`, `agenticApp`, `agenticAppInstance`, `unknownFutureValue`, `agentIdentityBlueprintPrincipal`, `agentIDuser`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `agentIdentityBlueprintPrincipal`, `agentIDuser`. |
| agentType | microsoft.graph.agentic.agentType | Indicates whether the identity is agentic or nonagentic. The possible values are: `notAgentic`, `agenticApp`, `agenticAppInstance`, `unknownFutureValue`, `agentIdentityBlueprintPrincipal`, `agentIDuser`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `agentIdentityBlueprintPrincipal`, `agentIDuser`. |
| parentAppId | String | The **appId** of the parent agent where the **agentType** is agentic. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentic.agentSignIn",
  "agentType": "String",
  "parentAppId": "String",
  "agentSubjectType": "String",
  "agentSubjectParentId": "String"
}
```
