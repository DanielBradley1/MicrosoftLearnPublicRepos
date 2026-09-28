<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userregistrationfeaturecount?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# userRegistrationFeatureCount resource type

Namespace: microsoft.graph

Represents the number of users registered or capable for multifactor authentication, self-service password reset, and passwordless authentication.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| feature | authenticationMethodFeature | Number of users registered or capable for multifactor authentication, self-service password reset, and passwordless authentication. The possible values are: `ssprRegistered`, `ssprEnabled`, `ssprCapable`, `passwordlessCapable`, `mfaCapable`, `unknownFutureValue`. |
| userCount | Int64 | Number of users. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userRegistrationFeatureCount",
  "feature": "String",
  "userCount": "Int64"
}
```
