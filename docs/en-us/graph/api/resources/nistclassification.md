<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/nistclassification?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# nistClassification resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mapping of a Microsoft Entra ID [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) to a NIST Cybersecurity Framework \(CSF\) 2.0 category. A recommendation can map to one or more NIST CSF 2.0 categories through its **nistClassifications** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | String | The NIST CSF 2.0 category name, for example `Adverse Event Analysis`. |
| description | String | A description of the NIST CSF 2.0 category. |
| function | String | The NIST CSF 2.0 function, for example `Detect (DE)`. |
| name | String | The NIST CSF 2.0 category identifier, for example `DE.AE`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.nistClassification",
  "function": "String",
  "category": "String",
  "name": "String",
  "description": "String"
}
```
