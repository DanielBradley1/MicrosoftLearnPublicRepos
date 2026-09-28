<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/termsofusecontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# termsOfUseContainer resource type

Namespace: microsoft.graph

Container for the relationships that expose the terms of use API and its features. Currently exposes the [agreements](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) and [agreementAcceptances](https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0) relationships.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agreementAcceptances | [agreementAcceptance](https://learn.microsoft.com/en-us/graph/api/resources/agreementacceptance?view=graph-rest-1.0) collection | Represents the current status of a user's response to a company's customizable terms of use agreement. |
| agreements | [agreement](https://learn.microsoft.com/en-us/graph/api/resources/agreement?view=graph-rest-1.0) collection | Represents a tenant's customizable terms of use agreement that's created and managed with Microsoft Entra ID Governance. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.termsOfUseContainer"
}
```
