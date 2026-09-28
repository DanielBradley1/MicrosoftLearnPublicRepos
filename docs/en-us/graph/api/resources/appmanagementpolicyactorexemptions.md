<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicyactorexemptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# appManagementPolicyActorExemptions resource type

Namespace: microsoft.graph

Represents a collection of custom security attribute conditions that exempt specific actors \(users or service principals\) from application management policy restrictions. This object is configured in the **excludedActors** property of the following resources:

- [keyCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/keycredentialconfiguration?view=graph-rest-1.0)
- [passwordCredentialConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredentialconfiguration?view=graph-rest-1.0)
- [identifierUriRestriction](https://learn.microsoft.com/en-us/graph/api/resources/identifierurirestriction?view=graph-rest-1.0)

Note

Actors with attributes matching any of the defined custom security attributes in the collection are exempt. The collection in this exemption is limited to 5 attributes.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customSecurityAttributes | [customSecurityAttributeExemption](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeexemption?view=graph-rest-1.0) collection | The collection of [customSecurityAttributeExemption](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeexemption?view=graph-rest-1.0) to exempt from the policy enforcement. Limit of 5. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.appManagementPolicyActorExemptions",
  "customSecurityAttributes": [
    {
      "@odata.type": "#microsoft.graph.customSecurityAttributeExemption"
    }
  ]
}
```
