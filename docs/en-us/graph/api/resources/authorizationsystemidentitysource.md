<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentitysource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# authorizationSystemIdentitySource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the source of an authorization system identity.

The following resource types inherit from this resource:

- [aadSource](https://learn.microsoft.com/en-us/graph/api/resources/aadsource?view=graph-rest-beta)
- [awsSource](https://learn.microsoft.com/en-us/graph/api/resources/awssource?view=graph-rest-beta)
- [azureSource](https://learn.microsoft.com/en-us/graph/api/resources/azuresource?view=graph-rest-beta)
- [gsuiteSource](https://learn.microsoft.com/en-us/graph/api/resources/gsuitesource?view=graph-rest-beta)
- [unknownSource](https://learn.microsoft.com/en-us/graph/api/resources/unknownsource?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identityProviderType | String | Type of identity provider. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationSystemIdentitySource",
  "identityProviderType": "String"
}
```
