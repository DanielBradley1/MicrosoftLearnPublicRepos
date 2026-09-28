<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appconsentapprovalroute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# appConsentApprovalRoute resource type

Namespace: microsoft.graph

Container for base resources that expose the app consent request API and features. Currently exposes only the [appConsentRequests](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) relationship.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appConsentRequests | [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) collection | A collection of [appConsentRequest](https://learn.microsoft.com/en-us/graph/api/resources/appconsentrequest?view=graph-rest-1.0) objects representing apps for which admin consent has been requested by one or more users. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appConsentApprovalRoute"
}
```
