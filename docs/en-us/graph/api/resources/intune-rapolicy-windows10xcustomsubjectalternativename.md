<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xcustomsubjectalternativename?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows10XCustomSubjectAlternativeName resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Base Profile Type for Authentication Certificates \(SCEP or PFX Create\)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sanType | [subjectAlternativeNameType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-subjectalternativenametype?view=graph-rest-beta) | Custom SAN Type. Possible values are: `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier`. |
| name | String | Custom SAN Name |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10XCustomSubjectAlternativeName",
  "sanType": "String",
  "name": "String"
}
```
