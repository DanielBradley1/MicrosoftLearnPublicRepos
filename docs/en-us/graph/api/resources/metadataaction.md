<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/metadataaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# metadataAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents the metadata to be written or removed from a file. **metadataAction** may be returned by the [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateremoval?view=graph-rest-beta), [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta), and [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) APIs. The action informs the consuming application of the specific key/value pairs that should be added to the file or the specific metadata keys that should be removed from the file. This metadata is what describes the file or information as being *labeled*.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| metadataToAdd | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | A collection of key value pairs that should be added to the file. |
| metadataToRemove | String collection | A collection of strings that indicate which keys to remove from the file metadata. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "metadataToAdd": [{"@odata.type": "microsoft.graph.keyValuePair"}],
  "metadataToRemove": ["String"]
}
```
