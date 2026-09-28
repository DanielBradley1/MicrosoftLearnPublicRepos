<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentidentitytype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# agentIdentityType enum type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the type of Microsoft Entra agent identity for risk detection and management. This enumeration is used by the [riskyAgent](https://learn.microsoft.com/en-us/graph/api/resources/riskyagent?view=graph-rest-beta) and [agentRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/agentriskdetection?view=graph-rest-beta) resources to classify different types of agent identities.

## Members

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following member in this evolvable enum: `agentIdentityBlueprintPrincipal`.

| Member | Description |
| :--- | :--- |
| agentIdentity | Represents a standard agent identity registered in Microsoft Entra ID. |
| agentUser | Represents a user account associated with an AI agent. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| agentIdentityBlueprintPrincipal | Represents an agent identity blueprint principal that defines agent identity templates. |
| user | Represents a regular user account. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentIdentityType"
}
```
