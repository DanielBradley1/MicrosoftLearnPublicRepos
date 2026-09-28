<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# verifiableCredentialSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Settings for verifiable credential types that a requestor must present to a service such as Entitlement Management.

Used for the **verifiableCredentialSettings** property of an [access package assignment policy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| credentialTypes | [verifiableCredentialType](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialtype?view=graph-rest-beta) collection | The types of verifiable credentials that a requestor must present when requesting an access package that has the policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialSettings",
  "credentialTypes": [
    {
      "@odata.type": "microsoft.graph.verifiableCredentialType"
    }
  ]
}
```
