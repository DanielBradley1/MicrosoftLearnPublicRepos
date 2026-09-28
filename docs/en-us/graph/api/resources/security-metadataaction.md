<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-metadataaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# metadataAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the metadata to be written or removed from a file. **metadataAction** might be returned by the [evaluateRemoval](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateremoval?view=graph-rest-beta), [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta), and [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta) APIs. The action informs the consuming application of the specific key-value pairs that should be added to the file or the specific metadata keys that should be removed from the file. This metadata is what describes the file or information as being *labeled*.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| metadataToAdd | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | A collection of key-value pairs that should be added to the file. |
| metadataToRemove | String collection | A collection of strings that indicate which keys to remove from the file metadata. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.metadataAction",
  "metadataToAdd": [
    {
      "@odata.type": "microsoft.graph.security.keyValuePair"
    }
  ],
  "metadataToRemove": [
    "String"
  ]
}
```
