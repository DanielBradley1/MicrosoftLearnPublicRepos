<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/person?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# person resource type

Namespace: microsoft.graph

Represents an aggregation of information about a person from across mail and contacts. People can be local contacts or your organization's directory, and people from recent communications \(such as email\).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List people](https://learn.microsoft.com/en-us/graph/api/user-list-people?view=graph-rest-1.0) | **person** | Get a collection of person objects ordered by their relevance to the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| birthday | String | The person's birthday. |
| companyName | String | The name of the person's company. |
| department | String | The person's department. |
| displayName | String | The person's display name. |
| givenName | String | The person's given name. |
| id | String | The person's unique identifier. Read-only. |
| imAddress | String | The instant message voice over IP \(VOIP\) session initiation protocol \(SIP\) address for the user. Read-only. |
| isFavorite | Boolean | `True` if the user has flagged this person as a favorite. |
| jobTitle | String | The person's job title. |
| officeLocation | String | The location of the person's office. |
| personNotes | String | Free-form notes that the user has taken about this person. |
| personType | [personType](https://learn.microsoft.com/en-us/graph/api/resources/persontype?view=graph-rest-1.0) | The type of person. |
| phones | [phone](https://learn.microsoft.com/en-us/graph/api/resources/phone?view=graph-rest-1.0) collection | The person's phone numbers. |
| postalAddresses | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) collection | The person's addresses. |
| profession | String | The person's profession. |
| scoredEmailAddresses | [scoredEmailAddress](https://learn.microsoft.com/en-us/graph/api/resources/scoredemailaddress?view=graph-rest-1.0) collection | The person's email addresses. |
| surname | String | The person's surname. |
| userPrincipalName | String | The user principal name \(UPN\) of the person. The UPN is an Internet-style login name for the person based on the Internet standard [RFC 822](https://www.ietf.org/rfc/rfc0822.txt). By convention, this should map to the person's email name. The general format is alias@domain. |
| websites | [website](https://learn.microsoft.com/en-us/graph/api/resources/website?view=graph-rest-1.0) collection | The person's websites. |
| yomiCompany | String | The phonetic Japanese name of the person's company. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "birthday": "String",
  "companyName": "String",
  "department": "String",
  "displayName": "String",
  "scoredEmailAddresses": [{"@odata.type": "microsoft.graph.scoredEmailAddress"}],
  "givenName": "String",
  "id": "String (identifier)",
  "imAddress": "String",
  "isFavorite": "Boolean",
  "jobTitle": "String",
  "officeLocation": "String",
  "personNotes": "String",
  "personType": {"@odata.type": "microsoft.graph.personType"},
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "postalAddresses": [{"@odata.type": "microsoft.graph.location"}],
  "profession": "String",
  "surname": "String",
  "userPrincipalName": "String",
  "websites": [{"@odata.type": "microsoft.graph.website"}],
  "yomiCompany": "String"
}
```
