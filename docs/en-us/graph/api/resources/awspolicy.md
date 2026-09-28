<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an AWS policy in an AWS authorization system. An AWS policy is an object in AWS that defines the permissions of the associated entity or resource. When a principal, such as a user, makes a request, the policies and their associated permissions determine whether the request is allowed or denied.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-policies?view=graph-rest-beta) | [awsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta) collection | List all [awsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta) objects and their properties for a specific AWS authorization system. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awspolicy-get?view=graph-rest-beta) | [awsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta) | Read the properties and relationships of a single [awsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/awspolicy?view=graph-rest-beta) object in an AWS authorization system. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| awsPolicyType | awsPolicyType | The type of the AWS policy. The possible values are: `system`, `custom`, `unknownFutureValue`. Read-only. Supports `$filter` and \(`eq`\). |
| displayName | String | The display name for the AWS policy. Read-only. Supports `$filter` and \(`eq`,`contains`\). |
| externalId | String | The base64 encoded identifier for the AWS policy as defined by AWS. Read-only. Alternate key. Supports `$filter` and `eq`. |
| id | String | The unique encoded identifier for the AWS policy. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsPolicy",
  "id": "String (identifier)",
  "externalId": "String",
  "displayName": "String",
  "awsPolicyType": "String"
}
```
