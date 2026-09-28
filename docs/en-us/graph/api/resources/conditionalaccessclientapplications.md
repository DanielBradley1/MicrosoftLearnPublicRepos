<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessclientapplications?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# conditionalAccessClientApplications resource type

Namespace: microsoft.graph

Represents client applications \(service principals and workload identities\) included in and excluded from the policy scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeServicePrincipals | String collection | Service principal IDs excluded from the policy scope. |
| includeServicePrincipals | String collection | Service principal IDs included in the policy scope, or `ServicePrincipalsInMyTenant`. |
| servicePrincipalFilter | [conditionalAccessFilter](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessfilter?view=graph-rest-1.0) | Filter that defines the dynamic-servicePrincipal-syntax rule to include/exclude service principals. A filter can use custom security attributes to include/exclude service principals. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessClientApplications",
  "excludeServicePrincipals": [
    "String"
  ],
  "includeServicePrincipals": [
    "String"
  ],
  "servicePrincipalFilter": {"@odata.type": "microsoft.graph.conditionalAccessFilter"}
}
```
