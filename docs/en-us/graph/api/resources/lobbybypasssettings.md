<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/lobbybypasssettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# lobbyBypassSettings resource type

Namespace: microsoft.graph

Specifies which participants can bypass the meeting lobby.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| isDialInBypassEnabled | Boolean | Specifies whether or not to always let dial-in callers bypass the lobby. Optional. |
| scope | [lobbyBypassScope](#lobbybypassscope-values) | Specifies the type of participants that are automatically admitted into a meeting, bypassing the lobby. Optional. |

### lobbyBypassScope values

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following values in this evolvable enum: `invited`, `organizationExcludingGuests`.

| Value | Description |
| --- | --- |
| organizer | Only the organizer is admitted into the meeting and bypassing the lobby. All other participants are placed in the meeting lobby. |
| organization | Only the participants from the same company **and guests** are admitted into the meeting and bypassing the lobby. All other participants are placed in the meeting lobby. |
| organizationAndFederated | Only the participants from the same company or trusted organization and guests are admitted into the meeting and bypassing the lobby. All other participants are placed in the meeting lobby. |
| everyone | Everyone is admitted into the meeting. No participants are placed in the meeting lobby. |
| invited | Only people the organizer invites are admitted into the meeting and bypassing the lobby. All other participants are placed in the meeting lobby. |
| organizationExcludingGuests | Only the participants from the same company are admitted into the meeting and bypassing the lobby. All other participants are placed in the meeting lobby. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "scope": "String",
  "isDialInBypassEnabled": "Boolean",
}
```
