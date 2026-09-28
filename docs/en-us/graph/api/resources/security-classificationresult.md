<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-classificationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# classificationResult resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the result of a classification operation from the Microsoft classification engine. Data classification results from Azure Information Protection, Office, and other Microsoft services might return a [well-defined set of classification types](https://learn.microsoft.com/en-us/office365/securitycompliance/what-the-sensitive-information-types-look-for). These types can be provided to the [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta) API to resolve a sensitive information to a Microsoft Purview Information Protection label.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| confidenceLevel | Int32 | The confidence level, 0 to 100, of the result. |
| count | Int32 | The number of instances of the specific information type in the input. |
| sensitiveTypeId | GUID | The GUID of the discovered sensitive information type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.classificationResult",
  "confidenceLevel": "Integer",
  "count": "Integer",
  "sensitiveTypeId": "GUID"
}
```
