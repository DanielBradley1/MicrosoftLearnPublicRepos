<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinaudiencerestrictionsbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# signInAudienceRestrictionsBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The base type for values used in an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) resource's **signInAudienceRestrictions** property. This abstract type has two derived types that can be used:

- [unrestrictedAudience](https://learn.microsoft.com/en-us/graph/api/resources/unrestrictedaudience?view=graph-rest-beta): Used to indicate that there are no restrictions to the **signInAudience** value. Single-tenant applications \(`AzureADMyOrg`\) can only be used in the tenant where the app is registered, and multitenant applications \(`AzureADMultipleOrgs` and `AzureADandPersonalMicrosoftAccount`\) can be used in *any* Microsoft Entra tenant.
- [allowedTenantsAudience](https://learn.microsoft.com/en-us/graph/api/resources/allowedtenantsaudience?view=graph-rest-beta): For multitenant applications with **signInAudience** set to `AzureADMultipleOrgs`, used to indicate that the application \(representing a client app or an API\) can only be used in the given list of Microsoft Entra tenants.

This type is an abstract type.

Important

Using the **signInAudience** and **signInAudienceRestrictions** properties to limit where an application can be used **isn't** a replacement for proper tenant validation and authorization enforcement in your application code. If your application expects access only in specific tenants, you *must* enforce that validation in your application code. To learn more, see [Secure applications and APIs by validating claims](https://learn.microsoft.com/en-us/entra/identity-platform/claims-validation).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | kind | The kind of restrictions on what is allowed by the **signInAudience** value. The possible values are: `unrestricted`, `allowedTenants`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signInAudienceRestrictionsBase",
  "kind": "String"
}
```
