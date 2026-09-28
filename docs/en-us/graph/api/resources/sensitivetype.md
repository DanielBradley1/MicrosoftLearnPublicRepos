<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sensitivetype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# sensitiveType resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about a sensitive information type \(SIT\) used to classify content.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| classificationMethod | [classificationMethod](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#classificationmethod-values) | The classification method. The possible values are: `patternMatch`, `exactDataMatch`, `fingerprint`, `machineLearning`, `privacyDataMatch`, `aiPowered`, `unknownFutureValue`. `privacyDataMatch` performs privacy data matching based on tenant data. `aiPowered` performs AI-powered classification and can benefit from supported caller-supplied embeddings. `unknownFutureValue` is an evolvable enumeration sentinel value. Don't use it. |
| description | String | The description of the sensitive information type. |
| id | String | The unique identifier for the sensitive information type. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the sensitive information type was last modified. |
| name | String | The name of the sensitive information type. |
| publisherName | String | The name of the publisher. |
| rulePackageId | String | The identifier of the rule package. |
| rulePackageType | String | The type of the rule package. |
| scope | [sensitiveTypeScope](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#sensitivetypescope-values) | The scope of the sensitive information type. The possible values are: `fullDocument`, `partialDocument`. |
| sensitiveTypeSource | [sensitiveTypeSource](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#sensitivetypesource-values) | The source of sensitive type. The possible values are: `outOfBox`, `tenant`. |
| state | String | The state of the sensitive information type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sensitiveType",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "rulePackageId": "String",
  "rulePackageType": "String",
  "publisherName": "String",
  "state": "String",
  "scope": "String",
  "sensitiveTypeSource": "String",
  "classificationMethod": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```
