<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# b2cIdentityUserFlow resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user flow within an Azure Active Directory B2C tenant.

To help you set up the most common identity tasks for your applications, Azure Active Directory B2C includes predefined, configurable policies called [user flows](https://learn.microsoft.com/en-us/azure/active-directory-b2c/user-flow-overview). A user flow lets you determine how users interact with your application when they do things like sign in, sign up, edit a profile, or reset a password. You can create many user flows of different types in your tenant and use them in your applications as needed. With user flows, you can control the following capabilities:

- Account types used for sign-in, such as social accounts like a Facebook or local account
- Attributes to be collected from the consumer, such as first name, postal code, and shoe size
- Azure Multi-Factor Authentication
- Customization of the user interface
- Information that the application receives in the token

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List user flows](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-b2cuserflows?view=graph-rest-beta) | b2cIdentityUserFlow collection | Retrieve all B2C user flows. |
| [Get user flow](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-get?view=graph-rest-beta) | b2cIdentityUserFlow | Retrieve properties of a B2C user flow. |
| [Create user flow](https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-b2cuserflows?view=graph-rest-beta) | b2cIdentityUserFlow | Create a new B2C user flow. |
| [Update user flow](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-update?view=graph-rest-beta) | b2cIdentityUserFlow | Update the properties of a B2C user flow. |
| [Delete user flow](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-delete?view=graph-rest-beta) | None | Delete a B2C user flow. |
| [List identity providers](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-list-userflowidentityproviders?view=graph-rest-beta) | [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta) collection | Retrieve all identity providers in a B2C user flow. |
| [Add identity provider](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-userflowidentityproviders-update?view=graph-rest-beta) | None | Add an identity provider to a B2C user flow. |
| [Delete identity provider](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-delete-userflowidentityproviders?view=graph-rest-beta) | None | Remove an identity provider from a B2C user flow |
| [List user attribute assignments](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-list-userattributeassignments?view=graph-rest-beta) | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-beta) collection | Retrieve all user attribute assignments in a B2C user flow. |
| [Create user attribute assignment](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-post-userattributeassignments?view=graph-rest-beta) | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-beta) | Create a user attribute assignment in a B2C user flow. |
| [List languages](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-list-languages?view=graph-rest-beta) | [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration?view=graph-rest-beta) collection | Retrieve all languages within a B2C user flow. |
| [Create language](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-put-languages?view=graph-rest-beta) | [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration?view=graph-rest-beta) | Creates a custom language in a B2C user flow. |
| [Get API connectors configuration for user flow](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-get-apiconnectorconfiguration?view=graph-rest-beta) | [userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-beta) | Get the configuration for API connectors used in the user flow. The $expand query parameter is not supported for this method. |
| [Configure an API connector in a user flow](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-put-apiconnectorconfiguration?view=graph-rest-beta) | None | Configure an API connector for specific steps in a user flow by updating the [apiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-beta) property. |
| [List identity providers](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-list-identityproviders?view=graph-rest-beta) \(deprecated\) | [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityprovider?view=graph-rest-beta) collection | Retrieve all identity providers in a B2C user flow. |
| [Add identity provider](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-post-identityproviders?view=graph-rest-beta) \(deprecated\) | None | Add an identity provider to a B2C user flow. |
| [Delete identity provider](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-delete-identityproviders?view=graph-rest-beta) \(deprecated\) | None | Remove an identity provider from a B2C user flow |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The name of the user flow. This is a required value and is immutable after it's created. The name will be prefixed with the value of `B2C_1_` after creation. |
| userFlowType | userFlowType | The [type of user flow](https://learn.microsoft.com/en-us/azure/active-directory-b2c/user-flow-versions). The supported values for **userFlowType** are: `signUp`, `signIn`, `signUpOrSignIn`, `passwordReset`, `profileUpdate`, `resourceOwner`. |
| userFlowTypeVersion | Single | The version of the user flow. |
| isLanguageCustomizationEnabled | Boolean | The property that determines whether language customization is enabled within the B2C user flow. Language customization is not enabled by default for B2C user flows. |
| defaultLanguageTag | String | Indicates the default language of the b2cIdentityUserFlow that is used when no `ui_locale` tag is specified in the request. This field is [RFC 5646](https://tools.ietf.org/html/rfc5646) compliant. |
| apiConnectorConfiguration | [userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-beta) | Configuration for enabling an API connector for use as part of the user flow. You can only obtain the value of this object using [Get userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-get-apiconnectorconfiguration?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| userFlowIdentityProviders | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta) collection | The identity providers included in the user flow. |
| identityProviders \(deprecated\) | [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityprovider?view=graph-rest-beta) collection | The identity providers included in the user flow. |
| userAttributeAssignments | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-beta) collection | The user attribute assignments included in the user flow. |
| languages | [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration?view=graph-rest-beta) collection | The languages supported for customization within the user flow. Language customization is not enabled by default in B2C user flows. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "id": "String (identifier)",
    "userFlowType": "String",
    "userFlowTypeVersion": "Single",
    "isLanguageCustomizationEnabled": "Boolean",
    "defaultLanguageTag": "String",
    "userFlowIdentityProviders": [{"@odata.type": "microsoft.graph.identityProviderBase"}],
    "identityProviders": [{"@odata.type": "microsoft.graph.identityProvider"}],
    "userAttributeAssignments": [{"@odate.type": "microsoft.graph.identityUserFlowAttributeAssignment"}],
    "languages": [{"@odata.type": "microsoft.graph.userFlowLanguageConfiguration"}],
    "apiConnectorConfiguration": {
      "@odata.type": "microsoft.graph.userFlowApiConnectorConfiguration"
    }
}
```
