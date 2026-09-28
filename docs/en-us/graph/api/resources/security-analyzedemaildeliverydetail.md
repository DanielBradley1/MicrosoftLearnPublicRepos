<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemaildeliverydetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# analyzedEmailDeliveryDetail resource type

Namespace: microsoft.graph.security

Represents the delivery action and location of an [analyzed email](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedemail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.deliveryAction](#deliveryaction-values) | The delivery action of the email. The possible values are: `unknown`, `deliveredToJunk`, `delivered`, `blocked`, `replaced`, `unknownFutureValue`. |
| location | [microsoft.graph.security.deliveryLocation](#deliverylocation-values) | The delivery location of the email. The possible values are: `unknown`, `inbox_folder`, `junkFolder`, `deletedFolder`, `quarantine`, `onprem_external`, `failed`, `dropped`, `others`, `unknownFutureValue`. |
| latestThreats | String | Latest known threat on the email. |
| originalThreats | String | Threats identified at the time of delivery. |

### deliveryAction values

| Member |
| :--- |
| unknown |
| deliveredToJunk |
| delivered |
| blocked |
| replaced |
| unknownFutureValue |

### deliveryLocation values

| Member |
| :--- |
| unknown |
| inbox\_folder |
| junkFolder |
| deletedFolder |
| quarantine |
| onprem\_external |
| failed |
| dropped |
| others |
| unknownFutureValue |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.analyzedEmailDeliveryDetail",
  "action": "String",
  "location": "String",
  "originalThreats": "String",
  "latestThreats": "String"
}
```
