<!-- Source: https://learn.microsoft.com/en-us/graph/group-set-options -->
<!-- Sitemap-Last-Modified: 2025-10-09 -->

# Microsoft 365 Group behaviors and provisioning options

On the [group](https://learn.microsoft.com/en-us/graph/api/resources/group) resource in Microsoft Graph, you can use the **resourceBehaviorOptions** property to set specific group behaviors when creating a Microsoft 365 group. The **resourceProvisioningOptions** property on the other hand indicates the specific resources provisioned for the group.

## Resource behavior options

**resourceBehaviorOptions** is a string collection that specifies group behaviors for a Microsoft 365 group. These behaviors can be set only on [group creation](https://learn.microsoft.com/en-us/graph/api/group-post-groups).

| Supported values for resourceBehaviorOptions | Description |
| :--- | :--- |
| `AllowOnlyMembersToPost` | Only group *members* can post conversations to the group; otherwise, any user in the organization can post conversations to the group. |
| `CalendarMemberReadOnly` | Members can view the group calendar in Outlook but can't make changes; otherwise, members can both view and edit the group calendar in Outlook. |
| `ConnectorsDisabled` | Changes made to the group in Exchange Online aren't synced back to on-premises Active Directory. |
| `HideGroupInOutlook` | This group is hidden in Outlook experiences; otherwise, the group is visible and discoverable in Outlook experiences. |
| `SubscribeMembersToCalendarEventsDisabled` | Members aren't subscribed to the group's calendar events in Outlook. |
| `SubscribeNewGroupMembers` | Group members are subscribed to receive group conversations. |
| `WelcomeEmailDisabled` | Welcome emails aren't sent to new members. |
| `SkipExchangeInstantOn` | For internal use only. DO NOT USE. |
| `ProvisionSiteOnDemand` | By default, a SharePoint site is automatically provisioned when a Microsoft 365 group is created. Use this option to override the default behavior so that the site is provisioned on demand. |

## Resource provisioning options

**resourceProvisioningOptions** is a string collection that specifies the resources associated with the Microsoft 365 group.

Caution

Avoid configuring the **resourceProvisioningOptions** property during group creation or update. Let the system manage the property.

| Supported values for resourceProvisioningOptions | Description |
| :--- | :--- |
| `Team` | If set, the Microsoft 365 group is associated with a Teams team. |

## Related content

- [Overview of Microsoft 365 groups in Microsoft Graph](https://learn.microsoft.com/en-us/graph/microsoft365-groups-concept-overview)
- [Microsoft Teams API overview](https://learn.microsoft.com/en-us/graph/teams-concept-overview)
