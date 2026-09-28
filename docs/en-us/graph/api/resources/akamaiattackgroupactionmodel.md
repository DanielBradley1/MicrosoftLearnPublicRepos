<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/akamaiattackgroupactionmodel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# akamaiAttackGroupActionModel resource type

Namespace: microsoft.graph

Represents an Akamai web application firewall \(WAF\) attack group and the action configured for that group, as defined in the **activeAttackGroups** property of the [akamaiVerifiedDetailsModel object](https://learn.microsoft.com/en-us/graph/api/resources/akamaiverifieddetailsmodel?view=graph-rest-1.0). This resource is used to describe how the Akamai integration handles specific categories of attacks, such as blocking, alerting, or logging.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | String | The action Akamai applies to the attack group when a matching threat is detected. Common values include `deny`, `none` or `alert`. |
| group | String | The name or identifier of the attack group. This value categorizes the type of attack the action applies to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.akamaiAttackGroupActionModel",
  "group": "String",
  "action": "String"
}
```
