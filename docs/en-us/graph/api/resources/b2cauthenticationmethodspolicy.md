<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/b2cauthenticationmethodspolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# b2cAuthenticationMethodsPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Azure Active Directory \(Azure AD\) B2C allows tenant admins to choose a mechanism for letting end users register via local accounts. Local accounts are the accounts where Microsoft Entra ID does the identity assertion, as opposed to a federated identity provider such as Google or Facebook etc.

The local accounts in Azure AD B2C do not follow the settings or paradigms from Microsoft Entra ID. The Microsoft Entra authentication methods policy isn't used or enforced by Azure AD B2C. Azure AD B2C stores these settings in a different policy, which is consumed by user flows.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/b2cauthenticationmethodspolicy-get?view=graph-rest-beta) | [b2cauthenticationmethodspolicy](https://learn.microsoft.com/en-us/graph/api/resources/b2cauthenticationmethodspolicy?view=graph-rest-beta) | Read the properties of a **b2cauthenticationmethodspolicy** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/b2cauthenticationmethodspolicy-update?view=graph-rest-beta) | None | Update the properties of a **b2cauthenticationmethodspolicy** objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the B2C authentication methods policy. This is a read only property and the key. |
| isEmailPasswordAuthenticationEnabled | Boolean | The tenant admin can configure local accounts using email if the email and password authentication method is enabled. |
| isUserNameAuthenticationEnabled | Boolean | The tenant admin can configure local accounts using username if the username and password authentication method is enabled. |
| isPhoneOneTimePasswordAuthenticationEnabled | Boolean | The tenant admin can configure local accounts using phone number if the phone number and one-time password authentication method is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "id": "b2CAuthenticationMethodsPolicy",
    "isEmailPasswordAuthenticationEnabled": true,
    "isUserNameAuthenticationEnabled": false,
    "isPhoneOneTimePasswordAuthenticationEnabled": true
}
```
