<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oauthconsentappdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# oAuthConsentAppDetail resource type

Namespace: microsoft.graph

Represents details required for the oAuth technique. Admins can configure the scope, name, and logo for a phish app that is associated to a simulation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScope | oAuthAppScope | App scope. The possible values are: `unknown`, `readCalendar`, `readContact`, `readMail`, `readAllChat`, `readAllFile`, `readAndWriteMail`, `sendMail`, `unknownFutureValue`. |
| displayLogo | String | App display logo. |
| displayName | String | App name. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oAuthConsentAppDetail",
  "appScope": "String",
  "displayLogo": "String",
  "displayName": "String"
}
```
