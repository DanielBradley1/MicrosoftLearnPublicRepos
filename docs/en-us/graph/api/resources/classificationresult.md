<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classificationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# classificationResult resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Represents the result of a classification operation from the Microsoft Classification Engine. Data classification results from Azure Information Protection, Office, and other Microsoft services may return a [well-defined set of classification types](https://learn.microsoft.com/en-us/office365/securitycompliance/what-the-sensitive-information-types-look-for). These types can be provided to the [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) API to resolve a sensitive information to a Microsoft Purview Information Protection label.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| confidenceLevel | Int32 | The confidence level, 0 to 100, of the result. |
| count | Int32 | The number of instances of the specific information type in the input. |
| sensitiveTypeId | GUID | The GUID of the discovered sensitive information type. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "confidenceLevel": 1024,
  "count": 1024,
  "sensitiveTypeId": "Guid"
}
```
