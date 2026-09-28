<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-06 -->

# b2xIdentityUserFlow resource type

Namespace: microsoft.graph

Represents a self-service sign up user flow within a Microsoft Entra tenant.

User flows are used to enable a [self-service sign up](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/self-service-sign-up-overview) experience for guest users on an application. User flows define the experience the end user sees while signing up. This experience includes which [identity providers](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/identity-providers) they can use to authenticate, and which attributes are collected as part of the sign up process.

Inherits from base class [identityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflow?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List user flows](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-b2xuserflows?view=graph-rest-1.0) | b2xIdentityUserFlow collection | Retrieve all self-service sign-up user flows. |
| [Get user flow](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-get?view=graph-rest-1.0) | b2xIdentityUserFlow | Retrieve properties of a self-service sign-up user flow. |
| [Create user flow](https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-b2xuserflows?view=graph-rest-1.0) | b2xIdentityUserFlow | Create a new self-service sign-up user flow. |
| [Delete user flow](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-delete?view=graph-rest-1.0) | None | Delete a self-service sign-up user flow. |
| [List identity providers](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-list-identityproviders?view=graph-rest-1.0) | [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityprovider?view=graph-rest-1.0) collection | Retrieve all identity providers in a self-service sign-up user flow. |
| [Add identity provider](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-post-identityproviders?view=graph-rest-1.0) | None | Add an identity provider to a self-service sign-up user flow. |
| [Remove identity provider](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-delete-identityproviders?view=graph-rest-1.0) | None | Remove an identity provider from a self-service sign-up user flow. |
| [List user attribute assignments](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-list-userattributeassignments?view=graph-rest-1.0) | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0) collection | Retrieve all user attribute assignments in a self-service sign-up user flow. |
| [Create user attribute assignment](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-post-userattributeassignments?view=graph-rest-1.0) | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0) | Create a user attribute assignment in a self-service sign-up user flow. |
| [List languages](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-list-languages?view=graph-rest-1.0) | [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration?view=graph-rest-1.0) collection | Retrieve all languages within a self-service sign-up user flow. |
| [Get API connectors configuration for user flow](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-get-apiconnectorconfiguration?view=graph-rest-1.0) | [userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-1.0) | Get the configuration for API connectors used in the self-service sign-up user flow. The $expand query parameter isn't supported for this method. |
| [Configure an API connector in a user flow](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-put-apiconnectorconfiguration?view=graph-rest-1.0) | None | Configure an API connector for specific steps in a self-service sign-up user flow by updating the [apiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-1.0) property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apiConnectorConfiguration | [userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-1.0) | Configuration for enabling an API connector for use as part of the self-service sign-up user flow. You can only obtain the value of this object using [Get userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-get-apiconnectorconfiguration?view=graph-rest-1.0). |
| id | String | The name of the user flow is a required value and is immutable after it's created. The name will be prefixed with the value of `B2X_1_` after creation. |
| userFlowType | userFlowType | The type of user flow. For self-service sign-up user flows, the value can only be `signUpOrSignIn` and can't be modified after creation. |
| userFlowTypeVersion | Single | The version of the user flow. For self-service sign-up user flows, the version is always `1`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identityProviders | [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityprovider?view=graph-rest-1.0) collection | The identity providers included in the user flow. |
| languages | [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration?view=graph-rest-1.0) collection | The languages supported for customization within the user flow. Language customization is enabled by default in self-service sign-up user flow. You can't create custom languages in self-service sign-up user flows. |
| userAttributeAssignments | [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment?view=graph-rest-1.0) collection | The user attribute assignments included in the user flow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "apiConnectorConfiguration": {
      "@odata.type": "microsoft.graph.userFlowApiConnectorConfiguration"
    },
    "id": "String (identifier)",
    "identityProviders": [{"@odata.type": "microsoft.graph.identityProvider"}],
    "languages": [{"@odata.type": "microsoft.graph.userFlowLanguageConfiguration"}],
    "userAttributeAssignments": [{"@odate.type": "microsoft.graph.identityUserFlowAttributeAssignment"}],
    "userFlowType": "String",
    "userFlowTypeVersion": "Single"
}
```
