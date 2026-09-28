<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-credential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-05 -->

# credential resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base type for credentials supported in the Industry Data API. This type is abstract.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the credential. |
| isValid | Boolean | Indicates whether the credential provided is valid based on the last data connector [validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) operation. |
| lastValidDateTime | DateTimeOffset | The time that the credential was last successfully validated by the data connector [validate](https://learn.microsoft.com/en-us/graph/api/industrydata-industrydataconnector-validate?view=graph-rest-beta) operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.credential",
  "displayName": "String",
  "isValid": "Boolean",
  "lastValidDateTime": "String (timestamp)"
}
```
