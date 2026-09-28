<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# contentInfo resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current state of some information that is to be labeled. **contentInfo** is passed in to the [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateremoval?view=graph-rest-beta), [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta), and [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta) APIs to describe to the API the current state of the information. This **contentInfo** detail drives the results on what metadata, content marking, and protection should be added or removed when the label is applied, updated, or removed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentFormat | String | The format of the content to be labeled. The possible values are: `file`, `email`. |
| identifier | String | Identifier used for Azure Information Protection Analytics. |
| metadata | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/security-keyvaluepair?view=graph-rest-beta) collection | Existing Microsoft Purview Information Protection metadata is passed as key-value pairs, where the key is the `MSIP_Label_GUID_PropName`. |
| state | contentState | The usage state of the content. The possible values are: `rest`, `motion`, or `use`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentInfo",
  "contentFormat": "String",
  "identifier": "String",
  "metadata": [
    {
      "@odata.type": "microsoft.graph.security.keyValuePair"
    }
  ],
  "state": "String"
}
```
