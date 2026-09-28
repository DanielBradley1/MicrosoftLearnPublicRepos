<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/parentalcontrolsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-11 -->

# parentalControlSettings resource type

Namespace: microsoft.graph

Specifies parental control settings for an application. These settings control the consent experience.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| countriesBlockedForMinors | String collection | Specifies the [two-letter ISO country codes](https://www.iso.org/iso-3166-country-codes.html). Access to the application will be blocked for minors from the countries specified in this list. |
| legalAgeGroupRule | String | Specifies the legal age group rule that applies to users of the app. Can be set to one of the following values:<br><br>\| Value \| Description \|<br>\| --- \| --- \|<br>\| Allow \| Default. Enforces the legal minimum. This means parental consent is required for minors in the European Union and Korea. \|<br>\| RequireConsentForPrivacyServices \| Enforces the user to specify date of birth to comply with COPPA rules. \|<br>\| RequireConsentForMinors \| Requires parental consent for ages below 18, regardless of country/region minor rules. \|<br>\| RequireConsentForKids \| Requires parental consent for ages below 14, regardless of country/region minor rules. \|<br>\| BlockMinors \| Blocks minors from using the app. \| |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "countriesBlockedForMinors": [ "String" ],
  "legalAgeGroupRule": "String"
}
```
