<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsstatement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsStatement resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Specifies an AWS statement that includes information about a single permission.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | String collection | The AWS actions. |
| condition | [awsCondition](https://learn.microsoft.com/en-us/graph/api/resources/awscondition?view=graph-rest-beta) | The AWS conditions associated with the statement. |
| effect | awsStatementEffect | The AWS action effect, whether to allow or deny. The possible values are: `allow`, `deny`, `unknownFutureValue`. |
| notActions | String collection | AWS Not Actions |
| notResources | String collection | AWS Not Resources |
| resources | String collection | The AWS resources associated with the statement. |
| statementId | String | The ID of the AWS statement. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsStatement",
  "statementId": "String (identifier)",
  "actions": [
    "String"
  ],
  "notActions": [
    "String"
  ],
  "resources": [
    "String"
  ],
  "notResources": [
    "String"
  ],
  "effect": "String",
  "condition": {
    "@odata.type": "microsoft.graph.awsCondition"
  }
}
```
