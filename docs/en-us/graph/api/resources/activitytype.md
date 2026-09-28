<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activitytype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-24 -->

# activityType enum type

Namespace: microsoft.graph

Represents the type of activity associated with a risk detection. This enumeration is used by multiple resources.

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `servicePrincipal`.

## Members

| Member | Description |
| :--- | :--- |
| signin | The risk is linked to a sign-in activity.  <br>  <br>Applies to: **activity** property of [riskDetection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection?view=graph-rest-1.0) and [servicePrincipalRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0) |
| user | The risk is linked to a user activity.  <br>  <br>Applies to: **activity** property of [riskDetection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection?view=graph-rest-1.0) |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use.  <br>  <br>Applies to: **activity** property of [riskDetection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection?view=graph-rest-1.0) and [servicePrincipalRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0) |
| servicePrincipal | The risk is linked to a service principal activity.  <br>  <br>Applies to: **activity** property of [riskDetection](https://learn.microsoft.com/en-us/graph/api/resources/riskdetection?view=graph-rest-1.0) and [servicePrincipalRiskDetection](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipalriskdetection?view=graph-rest-1.0) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.activityType"
}
```
