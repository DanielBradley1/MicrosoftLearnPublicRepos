<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/relatedperson?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-03 -->

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
| relationshipLabel | String | Information \(free-text\) describing the relationship between the user and the related person. This property provides additional context beyond the predefined relationship values and can be used by clients, including AI-powered experiences, to better understand and reason about the relationship. |
| userId | String | The user's directory object ID \(Microsoft Entra ID or CID\). |
| userPrincipalName | String | Email address or reference to person within the organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "relationship": "String",
  "relationshipLabel": "String",
  "userId": "String",
  "userPrincipalName": "String"
}
```
