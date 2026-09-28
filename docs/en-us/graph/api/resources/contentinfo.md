<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# contentInfo resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents the current state of some information that is to be labeled. **contentInfo** is passed in to the [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateremoval?view=graph-rest-beta), [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta), and [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) APIs to describe to the API the current state of the information. This **contentInfo** detail drives the results on what metadata, content marking, and protection should be added or removed when the label is applied, updated, or removed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| format | String | The possible values are: `default`, `email`. |
| identifier | String | Identifier used for Azure Information Protection Analytics. |
| metadata | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Existing Microsoft Purview Information Protection metadata is passed as key/value pairs, where the key is the MSIP\_Label\_GUID\_PropName. |
| state | String | The possible values are: `rest`, `motion`, `use`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "format": "String",
  "identifier": "String",
  "metadata": [{"@odata.type": "microsoft.graph.keyValuePair"}],
  "state": "String"
}
```
