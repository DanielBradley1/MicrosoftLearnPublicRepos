<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestenumeratedmailboxlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# subjectRightsRequestEnumeratedMailboxLocation resource type

Namespace: microsoft.graph

Represents the properties for a subject rights request that defines specific mailboxes \(Exchange mailboxes and individual or group Microsoft Teams chats\) as a search location.

Inherits from [subjectRightsRequestMailboxLocation](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestmailboxlocation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userPrincipalNames | String collection | Collection of mailboxes that should be included in the search. Includes the user principal name \(UPN\) of each mailbox, for example, `Monica.Thompson@contoso.com`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectRightsRequestEnumeratedMailboxLocation",
  "userPrincipalNames": ["String"]
}
```
