<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-02 -->

# profile resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents properties that are descriptive of a user in a tenant; for example, anniversaries and education activities. These properties are surfaced in shared people experiences across Microsoft 365 and third-party services and experiences via Microsoft Graph.

Programmatically, these properties are expressed as [relationships](#relationships) of the **profile** resource. To get one of these navigation properties or create an instance of these properties for the user, use the corresponding GET or POST method on that property, where applicable. For more details, see the [Methods](#methods) section.

In addition to the navigation properties in the [Relationships](#relationships) section, other properties exclusive to first-party applications, such as user pronouns, aren't exposed on Microsoft Graph.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get profile](https://learn.microsoft.com/en-us/graph/api/profile-get?view=graph-rest-beta) | [profile](https://learn.microsoft.com/en-us/graph/api/resources/profile?view=graph-rest-beta) | Read properties and relationships of the profile object. |
| [Delete profile](https://learn.microsoft.com/en-us/graph/api/profile-delete?view=graph-rest-beta) | None | Delete a **profile** object. |
| [Create userAccountInformation](https://learn.microsoft.com/en-us/graph/api/profile-post-accounts?view=graph-rest-beta) | [userAccountInformation](https://learn.microsoft.com/en-us/graph/api/resources/useraccountinformation?view=graph-rest-beta) | Create a new **userAccountInformation** object by posting to the accounts collection. |
| [List accounts](https://learn.microsoft.com/en-us/graph/api/profile-list-accounts?view=graph-rest-beta) | [userAccountInformation](https://learn.microsoft.com/en-us/graph/api/resources/useraccountinformation?view=graph-rest-beta) collection | Get a **userAccountInformation** object collection. |
| [Create itemAddress](https://learn.microsoft.com/en-us/graph/api/profile-post-addresses?view=graph-rest-beta) | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) | Create a new **itemAddress** by posting to the addresses collection. |
| [List addresses](https://learn.microsoft.com/en-us/graph/api/profile-list-addresses?view=graph-rest-beta) | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) collection | Get an **itemAddress** object collection. |
| [Create personAnniversary](https://learn.microsoft.com/en-us/graph/api/profile-post-anniversaries?view=graph-rest-beta) | [personAnniversary](https://learn.microsoft.com/en-us/graph/api/resources/personanniversary?view=graph-rest-beta) | Create a new **personAnniversary** by posting to the anniversaries collection. |
| [List anniversaries](https://learn.microsoft.com/en-us/graph/api/profile-list-anniversaries?view=graph-rest-beta) | [personAnniversary](https://learn.microsoft.com/en-us/graph/api/resources/personanniversary?view=graph-rest-beta) collection | Get a **personAnniversary** object collection. |
| [Create personAward](https://learn.microsoft.com/en-us/graph/api/profile-post-awards?view=graph-rest-beta) | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) | Create a new **personAward** object by posting to the awards collection. |
| [List awards](https://learn.microsoft.com/en-us/graph/api/profile-list-awards?view=graph-rest-beta) | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) collection | Get a **personAward** object collection. |
| [Create personCertification](https://learn.microsoft.com/en-us/graph/api/profile-post-certifications?view=graph-rest-beta) | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) | Create a new **personCertification** object by posting to the certifications collection. |
| [List certifications](https://learn.microsoft.com/en-us/graph/api/profile-list-certifications?view=graph-rest-beta) | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) collection | Get a **personCertification** object collection. |
| [Create educationalActivity](https://learn.microsoft.com/en-us/graph/api/profile-post-educationalactivities?view=graph-rest-beta) | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) | Create a new **educationalActivity** by posting to the **educationalActivities** collection. |
| [List educationalActivities](https://learn.microsoft.com/en-us/graph/api/profile-list-educationalactivities?view=graph-rest-beta) | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) collection | Get an **educationalActivity** object collection. |
| [Create itemEmail](https://learn.microsoft.com/en-us/graph/api/profile-post-emails?view=graph-rest-beta) | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) | Create a new **itemEmail** by posting to the emails collection. |
| [List emails](https://learn.microsoft.com/en-us/graph/api/profile-list-emails?view=graph-rest-beta) | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) collection | Get an **itemEmail** object collection. |
| [Create personInterest](https://learn.microsoft.com/en-us/graph/api/profile-post-interests?view=graph-rest-beta) | [personInterest](https://learn.microsoft.com/en-us/graph/api/resources/personinterest?view=graph-rest-beta) | Create a new **personInterest** by posting to the interests collection. |
| [List interests](https://learn.microsoft.com/en-us/graph/api/profile-list-interests?view=graph-rest-beta) | [personInterest](https://learn.microsoft.com/en-us/graph/api/resources/personinterest?view=graph-rest-beta) collection | Get a **personInterest** object collection. |
| [Create languageProficiency](https://learn.microsoft.com/en-us/graph/api/profile-post-languages?view=graph-rest-beta) | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) | Create a new **languageProficiency** by posting to the languages collection. |
| [List languages](https://learn.microsoft.com/en-us/graph/api/profile-list-languages?view=graph-rest-beta) | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) collection | Get a **languageProficiency** object collection. |
| [Create personName](https://learn.microsoft.com/en-us/graph/api/profile-post-names?view=graph-rest-beta) | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) | Create a new **personName** object by posting to the names collection. |
| [List names](https://learn.microsoft.com/en-us/graph/api/profile-list-names?view=graph-rest-beta) | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) collection | Get a **personName** object collection. |
| [Create personAnnotation](https://learn.microsoft.com/en-us/graph/api/profile-post-notes?view=graph-rest-beta) | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) | Create a new **personAnnotation** object by posting to the notes collection. |
| [List notes](https://learn.microsoft.com/en-us/graph/api/profile-list-notes?view=graph-rest-beta) | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) collection | Get a **personAnnotation** object collection. |
| [Create itemPatent](https://learn.microsoft.com/en-us/graph/api/profile-post-patents?view=graph-rest-beta) | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) | Create a new **itemPatent** object by posting to the patents collection. |
| [List patents](https://learn.microsoft.com/en-us/graph/api/profile-list-patents?view=graph-rest-beta) | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) collection | Get an **itemPatent** object collection. |
| [Create itemPhone](https://learn.microsoft.com/en-us/graph/api/profile-post-phones?view=graph-rest-beta) | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) | Create a new itemPhone by posting to the phones collection. |
| [List phones](https://learn.microsoft.com/en-us/graph/api/profile-list-phones?view=graph-rest-beta) | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) collection | Get an **itemPhone** object collection. |
| [Create workPosition](https://learn.microsoft.com/en-us/graph/api/profile-post-positions?view=graph-rest-beta) | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) | Create a new workPosition by posting to the positions collection. |
| [List positions](https://learn.microsoft.com/en-us/graph/api/profile-list-positions?view=graph-rest-beta) | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) collection | Get a **workPosition** object collection. |
| [Create projectParticipation](https://learn.microsoft.com/en-us/graph/api/profile-post-projects?view=graph-rest-beta) | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) | Create a new **projectParticipation** by posting to the projects collection. |
| [List projects](https://learn.microsoft.com/en-us/graph/api/profile-list-projects?view=graph-rest-beta) | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) collection | Get a **projectParticipation** object collection. |
| [Create itemPublication](https://learn.microsoft.com/en-us/graph/api/profile-post-publications?view=graph-rest-beta) | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) | Create a new **itemPublication** object by posting to the publications collection. |
| [List publications](https://learn.microsoft.com/en-us/graph/api/profile-list-publications?view=graph-rest-beta) | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) collection | Get an **itemPublication** object collection. |
| [Create personResponsibility](https://learn.microsoft.com/en-us/graph/api/profile-post-responsibilities?view=graph-rest-beta) | [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) | Create a new **personResponsibility** object by posting to the responsibilities collection. |
| [List responsibilities](https://learn.microsoft.com/en-us/graph/api/profile-list-responsibilities?view=graph-rest-beta) | [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) collection | Get a **personResponsibility** object collection. |
| [Create skillProficiency](https://learn.microsoft.com/en-us/graph/api/profile-post-skills?view=graph-rest-beta) | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) | Create a new **skillProficiency** by posting to the skills collection. |
| [List skills](https://learn.microsoft.com/en-us/graph/api/profile-list-skills?view=graph-rest-beta) | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) collection | Get a **skillProficiency** object collection. |
| [Create webAccount](https://learn.microsoft.com/en-us/graph/api/profile-post-webaccounts?view=graph-rest-beta) | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) | Create a new **webAccount** by posting to the webAccounts collection. |
| [List webAccounts](https://learn.microsoft.com/en-us/graph/api/profile-list-webaccounts?view=graph-rest-beta) | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) collection | Get a **webAccount** object collection. |
| [Create personWebsite](https://learn.microsoft.com/en-us/graph/api/profile-post-websites?view=graph-rest-beta) | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) | Create a new **personWebsite** by posting to the websites collection. |
| [List websites](https://learn.microsoft.com/en-us/graph/api/profile-list-websites?view=graph-rest-beta) | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) collection | Get a **personWebsite** object collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accounts | [userAccountInformation](https://learn.microsoft.com/en-us/graph/api/resources/useraccountinformation?view=graph-rest-beta) collection | Represents information specifically tied to a user's account. |
| addresses | [itemAddress](https://learn.microsoft.com/en-us/graph/api/resources/itemaddress?view=graph-rest-beta) collection | Represents details of addresses associated with the user. |
| anniversaries | [personAnniversary](https://learn.microsoft.com/en-us/graph/api/resources/personanniversary?view=graph-rest-beta) collection | Represents the details of meaningful dates associated with a person. |
| awards | [personAward](https://learn.microsoft.com/en-us/graph/api/resources/personaward?view=graph-rest-beta) collection | Represents the details of awards or honors associated with a person. |
| certifications | [personCertification](https://learn.microsoft.com/en-us/graph/api/resources/personcertification?view=graph-rest-beta) collection | Represents the details of certifications associated with a person. |
| educationalActivities | [educationalActivity](https://learn.microsoft.com/en-us/graph/api/resources/educationalactivity?view=graph-rest-beta) collection | Represents data that a user has supplied related to undergraduate, graduate, postgraduate or other educational activities. |
| emails | [itemEmail](https://learn.microsoft.com/en-us/graph/api/resources/itememail?view=graph-rest-beta) collection | Represents detailed information about email addresses associated with the user. |
| interests | [personInterest](https://learn.microsoft.com/en-us/graph/api/resources/personinterest?view=graph-rest-beta) collection | Provides detailed information about interests the user has associated with themselves in various services. |
| languages | [languageProficiency](https://learn.microsoft.com/en-us/graph/api/resources/languageproficiency?view=graph-rest-beta) collection | Represents detailed information about languages that a user has added to their profile. |
| names | [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) collection | Represents the names a user has added to their profile. |
| notes | [personAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/personannotation?view=graph-rest-beta) collection | Represents notes that a user has added to their profile. |
| patents | [itemPatent](https://learn.microsoft.com/en-us/graph/api/resources/itempatent?view=graph-rest-beta) collection | Represents patents that a user has added to their profile. |
| phones | [itemPhone](https://learn.microsoft.com/en-us/graph/api/resources/itemphone?view=graph-rest-beta) collection | Represents detailed information about phone numbers associated with a user in various services. |
| positions | [workPosition](https://learn.microsoft.com/en-us/graph/api/resources/workposition?view=graph-rest-beta) collection | Represents detailed information about work positions associated with a user's profile. |
| projects | [projectParticipation](https://learn.microsoft.com/en-us/graph/api/resources/projectparticipation?view=graph-rest-beta) collection | Represents detailed information about projects associated with a user. |
| publications | [itemPublication](https://learn.microsoft.com/en-us/graph/api/resources/itempublication?view=graph-rest-beta) collection | Represents details of any publications a user has added to their profile. |
| responsibilities | [personResponsibility](https://learn.microsoft.com/en-us/graph/api/resources/personresponsibility?view=graph-rest-beta) collection | Represents details of responsibilities a user has added to their profile. |
| skills | [skillProficiency](https://learn.microsoft.com/en-us/graph/api/resources/skillproficiency?view=graph-rest-beta) collection | Represents detailed information about skills associated with a user in various services. |
| webAccounts | [webAccount](https://learn.microsoft.com/en-us/graph/api/resources/webaccount?view=graph-rest-beta) collection | Represents web accounts the user has indicated they use or has added to their user profile. |
| websites | [personWebsite](https://learn.microsoft.com/en-us/graph/api/resources/personwebsite?view=graph-rest-beta) collection | Represents detailed information about websites associated with a user in various services. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "id": "String (identifier)"
}
```
