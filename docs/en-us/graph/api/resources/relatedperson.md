<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# relatedPerson resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about people related to information within a given entity in a [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta) for a user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of the person. |
| relationship | String | The possible values are: `manager`, `colleague`, `directReport`, `dotLineReport`, `assistant`, `dotLineManager`, `alternateContact`, `friend`, `spouse`, `sibling`, `child`, `parent`, `sponsor`, `emergencyContact`, `other`, `unknownFutureValue`. |
| userId | String | The user's directory object ID \(Microsoft Entra ID or CID\). |
| userPrincipalName | String | Email address or reference to person within the organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "relationship": "String",
  "userId": "String",
  "userPrincipalName": "String"
}
```
