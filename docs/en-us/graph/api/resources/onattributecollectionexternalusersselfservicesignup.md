<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionexternalusersselfservicesignup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# onAttributeCollectionExternalUsersSelfServiceSignUp resource type

Namespace: microsoft.graph

This resource is a managed handler for the attribute collection step in an external identities user flow on a Microsoft Entra workforce or customer tenant. It defines what attributes to collect from a user and how the attribute collection will be rendered for the user.

Inherits from [onAttributeCollectionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionhandler?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing this resource type, see the [authenticationEventsFlow resource type](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attributeCollectionPage | [authenticationAttributeCollectionPage](https://learn.microsoft.com/en-us/graph/api/resources/authenticationattributecollectionpage?view=graph-rest-1.0) | Required. The configuration for how attributes are displayed in the sign-up experience defined by a user flow, like the [externalUsersSelfServiceSignupEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/externalusersselfservicesignupeventsflow?view=graph-rest-1.0), specifically on the attribute collection page. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attributes | [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0) collection | A list of user attributes to collect. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onAttributeCollectionExternalUsersSelfServiceSignUp",
  "attributeCollectionPage": {
    "@odata.type": "microsoft.graph.authenticationAttributeCollectionPage"
  }
}
```
