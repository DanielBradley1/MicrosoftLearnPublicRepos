<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-customsubjectalternativename?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# customSubjectAlternativeName resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Custom Subject Alternative Name definition

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
  "@odata.type": "#microsoft.graph.customSubjectAlternativeName",
  "sanType": "String",
  "name": "String"
}
```
