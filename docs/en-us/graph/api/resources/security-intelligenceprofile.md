<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# intelligenceProfile resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

The Microsoft Defender Threat Intelligence Profiles \(Intel Profiles\) API provides the most up-to-date threat actor infrastructure visibility in the industry today, enabling threat intelligence and security operations \(SecOps\) teams to streamline their advanced threat hunting and analysis workflows. These teams have historically struggled to obtain visibility into the full extent of nation state and cybercriminal adversary infrastructures, creating blind spots in detection and response automation, hunting, and analytics. Sophisticated security professionals can use Microsoft Intelligence Profile APIs, along with the [indicators](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) and other associated markers, to automate defense of their organizations and track potentially malicious activity targeting their organization or industry. Users of the Microsoft Defender Threat Intelligence Profiles APIs have access to detailed threat actor intel profiles, including background information and interpretation guidance.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List intelligence profiles](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-intelprofiles?view=graph-rest-1.0) | [microsoft.graph.security.intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0) objects and their properties. |
| [Get intelligence profile](https://learn.microsoft.com/en-us/graph/api/security-intelligenceprofile-get?view=graph-rest-1.0) | [microsoft.graph.security.intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.intelligenceProfile](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofile?view=graph-rest-1.0) object. |
| [List indicators](https://learn.microsoft.com/en-us/graph/api/security-intelligenceprofile-list-indicators?view=graph-rest-1.0) | [microsoft.graph.security.intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) collection | Get a list of **intelligenceProfileIndicator** resources. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aliases | String collection | A list of commonly-known aliases for the threat intelligence included in the **intelligenceProfile**. |
| countriesOrRegionsOfOrigin | [microsoft.graph.security.intelligenceProfileCountryOrRegionOfOrigin](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofilecountryorregionoforigin?view=graph-rest-1.0) collection | The country/region of origin for the given actor or threat associated with this **intelligenceProfile**. |
| description | [microsoft.graph.security.formattedContent](https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0) | A synopsis of the threat actor. This property places the threat actor in wider context, tracing its discovery, history, significant campaigns, targeting, techniques of note, affiliations with governments, law enforcement countermeasures, and any areas of dispute among the security community regarding attribution. |
| firstActiveDateTime | DateTimeOffset | The date and time when this **intelligenceProfile** was first active. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The system generated ID for this **intelligenceProfile**. |
| kind | microsoft.graph.security.intelligenceProfileKind | A categorization of the type of this **intelligenceProfile**. The possible values are: `actor`, `tool`, `unknownFutureValue`. |
| summary | [microsoft.graph.security.formattedContent](https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0) | A short summary of this **intelligenceProfile**. |
| targets | String collection | Known targets related to this **intelligenceProfile**. |
| title | String | The title of this **intelligenceProfile**. |
| tradecraft | [microsoft.graph.security.formattedContent](https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0) | Formatted information featuring a description of the distinctive tactics, techniques, and procedures \(TTP\) of the group, followed by a list of all known custom, commodity, and publicly available implants used by the group. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| indicators | [microsoft.graph.security.intelligenceProfileIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofileindicator?view=graph-rest-1.0) collection | Includes an assemblage of high-fidelity network indicators of compromise. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.intelligenceProfile",
  "aliases": ["String"],
  "description": {
    "@odata.type": "microsoft.graph.security.formattedContent"
  },
  "firstActiveDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "kind": "String",
  "countriesOrRegionsOfOrigin": [
    {
      "@odata.type": "microsoft.graph.security.intelligenceProfileCountryOrRegionOfOrigin"
    }
  ],
  "summary": {
    "@odata.type": "microsoft.graph.security.formattedContent"
  },
  "targets": ["String"],
  "title": "String",
  "tradecraft": {
    "@odata.type": "microsoft.graph.security.formattedContent"
  }
}
```
