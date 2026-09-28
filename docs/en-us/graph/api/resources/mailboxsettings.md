<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mailboxsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mailboxSettings resource type

Namespace: microsoft.graph

Settings for the primary mailbox of a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0).

You can [get](https://learn.microsoft.com/en-us/graph/api/user-get-mailboxsettings?view=graph-rest-1.0) or [update](https://learn.microsoft.com/en-us/graph/api/user-update-mailboxsettings?view=graph-rest-1.0) a user's mailbox settings by querying the user's **mailboxSettings** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archiveFolder | string | Folder ID of an archive folder for the user. |
| automaticRepliesSetting | [automaticRepliesSetting](https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliessetting?view=graph-rest-1.0) | Configuration settings to automatically notify the sender of an incoming email with a message from the signed-in user. |
| dateFormat | string | The date format for the user's mailbox. |
| delegateMeetingMessageDeliveryOptions | delegateMeetingMessageDeliveryOptions | If the user has a calendar delegate, this specifies whether the delegate, mailbox owner, or both receive meeting messages and meeting responses. The possible values are: `sendToDelegateAndInformationToPrincipal`, `sendToDelegateAndPrincipal`, `sendToDelegateOnly`. |
| language | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-1.0) | The locale information for the user, including the preferred language and country/region. |
| timeFormat | string | The time format for the user's mailbox. |
| timeZone | string | The default time zone for the user's mailbox. |
| userPurpose | [userPurpose](#userpurpose-values) | The purpose of the mailbox. Differentiates a mailbox for a single user from a shared mailbox and equipment mailbox in Exchange Online. The possible values are: `user`, `linked`, `shared`, `room`, `equipment`, `others`, `unknownFutureValue`. Read-only. |
| workingHours | [workingHours](https://learn.microsoft.com/en-us/graph/api/resources/workinghours?view=graph-rest-1.0) | The days of the week and hours in a specific time zone that the user works. |

### userPurpose values

| Member | Description |
| :--- | :--- |
| user | A user account with a mailbox in the local forest. |
| linked | A mailbox linked to a user account in another forest. |
| shared | A mailbox shared by two or more user accounts. |
| room | A mailbox that represents a conference room. |
| equipment | A mailbox that represents a piece of equipment. |
| others | A mailbox was found but the user purpose is different from the ones specified in the previous scenarios. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "archiveFolder": "string",
  "automaticRepliesSetting": {"@odata.type": "microsoft.graph.automaticRepliesSetting"},
  "dateFormat": "string",
  "delegateMeetingMessageDeliveryOptions": "String",
  "language": {"@odata.type": "microsoft.graph.localeInfo"},
  "timeFormat": "string",
  "timeZone": "string",
  "userPurpose": "String",
  "workingHours": {"@odata.type": "microsoft.graph.workingHours"}
}
```
