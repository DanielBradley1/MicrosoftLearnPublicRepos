<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hostReputation resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents the reputation of a host based on a series of rules. This score helps users quickly understand any detected ties to malicious or suspicious infrastructure when validating the reputation of a known or unknown entity. The platform provides quick information about the activity of these entities \(such as first and last seen timestamps or [autonomous system](https://learn.microsoft.com/en-us/graph/api/resources/security-autonomoussystem?view=graph-rest-1.0) details\) and a list of rules that affect the reputation score when applicable.

Reputation data is important to understanding the trustworthiness of an attack surface and is also useful when assessing unknown [hostnames](https://learn.microsoft.com/en-us/graph/api/resources/security-hostname?view=graph-rest-1.0) or [IP addresses](https://learn.microsoft.com/en-us/graph/api/resources/security-ipaddress?view=graph-rest-1.0) that appear in investigations. These scores uncover any prior malicious or suspicious activity that affected the entity, or other known indicators of compromise to consider.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get host reputation](https://learn.microsoft.com/en-us/graph/api/security-host-get-reputation?view=graph-rest-1.0) | [microsoft.graph.security.hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) object, for a given [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classification | microsoft.graph.security.hostReputationClassification | The calculated reputation of the host. The possible values are: `unknown`, `neutral`, `suspicious`, `malicious`, `unknownFutureValue`. |
| id | String | A system-generated ID for this **hostReputation**. |
| rules | [microsoft.graph.security.hostReputationRule](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputationrule?view=graph-rest-1.0) collection | A collection of rules that have been used to calculate the classification and score. |
| score | Int32 | The calculated score \(0-100\) of the requested host. A higher value indicates that this [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) is more likely to be suspicious or malicious. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostReputation",
  "classification": "String",
  "id": "String (identifier)",
  "rules": [
    {
      "@odata.type": "microsoft.graph.security.hostReputationRule"
    }
  ],
  "score": "Int32"
}
```
