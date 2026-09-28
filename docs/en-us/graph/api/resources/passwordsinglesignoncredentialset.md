<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordsinglesignoncredentialset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# passwordSingleSignOnCredentialSet resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates a set of credentials that completely define a sign in flow for a user or group to an application.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| credentials | [credential](https://learn.microsoft.com/en-us/graph/api/resources/credential?view=graph-rest-beta) collection | A list of credential objects that define the complete sign in flow. |
| id | String | The ID of the user or group this credential set belongs to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passwordSingleSignOnCredentialSet",
  "id": "String",
  "credentials": [
      {
        "@odata.type": "microsoft.graph.credential"
      }
  ]
}
```
