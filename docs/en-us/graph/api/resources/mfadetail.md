<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mfadetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# mfaDetail resource type

Namespace: microsoft.graph

Indicates MFA details for a specific sign-in. It includes the authentication method used for signing in and auth details \(for example: Phone, SMS, or voicemail\)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authDetail | String | Indicates the MFA auth detail for the corresponding sign-in activity when the MFA Required is "Yes". |
| authMethod | String | Indicates the MFA Auth methods \(SMS, Phone, Authenticator App are some of the values\) for the corresponding sign-in activity when the MFA Required field is "Yes". |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "authDetail": "String",
  "authMethod": "String"
}
```
