<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/investigationidentityset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# investigationIdentitySet resource type

Namespace: microsoft.graph

Identifies the principals recorded in the **initiatedBy** property of an [agentic session](https://learn.microsoft.com/en-us/graph/api/resources/investigationsession?view=graph-rest-beta) or [agentRun](https://learn.microsoft.com/en-us/graph/api/resources/agentrun?view=graph-rest-beta). Recorded identities describe provenance; they don't select execution credentials or grant access.

Inherits from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agent | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The initiating agent principal, when recorded by the service. |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The recorded application identity. Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta). |
| device | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The recorded device identity. Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta). |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The recorded user identity. Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.investigationIdentitySet",
  "user": {
    "@odata.type": "microsoft.graph.identity"
  },
  "application": {
    "@odata.type": "microsoft.graph.identity"
  },
  "device": {
    "@odata.type": "microsoft.graph.identity"
  },
  "agent": {
    "@odata.type": "microsoft.graph.identity"
  }
}
```
