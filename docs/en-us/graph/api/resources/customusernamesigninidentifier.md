<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customusernamesigninidentifier?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# customUsernameSignInIdentifier resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom username sign-in identifier that enables users to authenticate using custom patterns such as account numbers, member IDs, or employee identifiers. This resource allows tenant administrators to define validation patterns using regular expressions to ensure custom usernames follow specific formats required by their organization.

Inherits from [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta).

## Methods

None.

For the list of API operations for managing this resource type, see the [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether this custom username sign-in identifier type is enabled for user authentication in the tenant. Inherited from [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta). |
| name | String | The unique name identifier for this custom username sign-in identifier configuration. Possible values include: `CustomUsername1`, `CustomUsername2`. Inherited from [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase?view=graph-rest-beta). |
| validationRegex | String | The regular expression pattern used to validate custom usernames. The pattern must be a valid regex, can't exceed 60 characters in length, and can't be an email-supported regex pattern. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customUsernameSignInIdentifier",
  "name": "String (identifier)",
  "isEnabled": "Boolean",
  "validationRegex": "String"
}
```
