<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/allowedtenantsaudience?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# allowedTenantsAudience resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **allowedTenantsAudience** type is used as the **signInAudienceRestrictions** value for an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta) resource to indicate that the application can only be used in one of the allowed Entra tenants in the listed in **allowedTenantIds**.

This type may only be used when the application's **signInAudience** property is `AzureADMultipleOrgs`.

Important

Using the **signInAudience** and **signInAudienceRestrictions** properties to limit where an application can be used **isn't** a replacement for proper tenant validation and authorization enforcement in your application code. If your application expects access only in specific tenants, you *must* enforce that validation in your application code. To learn more, see [Secure applications and APIs by validating claims](https://learn.microsoft.com/en-us/entra/identity-platform/claims-validation).

Inherits from [signInAudienceRestrictionsBase](https://learn.microsoft.com/en-us/graph/api/resources/signinaudiencerestrictionsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedTenantIds | String collection | The list of Entra tenant IDs where the application can be used as either a client application or a resource application \(API\). This property must contain at least one value and can't include more than 20 values. The tenant ID where the application is registered may be included, but is not required \(see **isHomeTenantAllowed**\). Required. |
| isHomeTenantAllowed | Boolean | Whether the tenant where the application is registered is allowed. Currently, only `true` is supported. Default is `true`. |
| kind | kind | If provided, must be `allowedTenants`. Optional. Inherited from [signInAudienceRestrictionsBase](https://learn.microsoft.com/en-us/graph/api/resources/signinaudiencerestrictionsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allowedTenantsAudience",
  "kind": "String",
  "allowedTenantIds": [
    "String"
  ],
  "isHomeTenantAllowed": "Boolean"
}
```
