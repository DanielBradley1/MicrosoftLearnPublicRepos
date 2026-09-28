<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontext?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationContext resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the conditional access authentication context of a sign-in event. This object is configured in the **authenticationContextClassReferences** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

For more information about authentication context in conditional access, see the [conditional access context documentation](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#authentication-context-preview).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detail | authenticationContextDetail | Describes how the conditional access authentication context was triggered. A value of `previouslySatisfied` means the auth context was because the user already satisfied the requirements for that authentication context in some previous authentication event. A value of `required` means the user had to meet the authentication context requirement as part of the sign-in flow. The possible values are: `required`, `previouslySatisfied`, `notApplicable`, `unknownFutureValue`. |
| id | String | The identifier of an authentication context in your tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationContext",
  "id": "String (identifier)",
  "detail": "String"
}
```
