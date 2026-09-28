<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userFlowApiConnectorConfiguration resource type

Namespace: microsoft.graph

Defines the APIs that are called at specific points in the user flow. Each relationship of this object corresponds to a specific step in the user flow that can be configured to call an API connector.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| postAttributeCollection | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) | Specifies an API to call after a user submits the collected attributes and before the user account is created during sign-up. |
| postFederationSignup | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) | Specifies an API to call after federation with an external identity provider. For example, a Google, Facebook, or Microsoft Entra API is completed when the user is signing up \(does not apply to sign-in\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userFlowApiConnectorConfiguration"
}
```
