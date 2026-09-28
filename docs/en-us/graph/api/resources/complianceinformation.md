<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/complianceinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# complianceInformation resource type

Namespace: microsoft.graph

Contains compliance data associated with secure score control.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificationControls | [certificationControl](https://learn.microsoft.com/en-us/graph/api/resources/certificationcontrol?view=graph-rest-1.0) collection | Collection of the certification controls associated with the certification. |
| certificationName | String | The name of the compliance certification, for example, `ISO 27018:2014`, `GDPR`, `FedRAMP`, and `NIST 800-171`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "certificationControls": [{"@odata.type": "microsoft.graph.certificationControl"}],
  "certificationName": "String"
}
```
