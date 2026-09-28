<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# calendarPermission resource type

Namespace: microsoft.graph

The permissions of a user with whom the calendar has been shared or delegated in an Outlook client.

List, create, get, update, and delete of calendar permissions is supported on behalf of only the calendar owner.

Getting the calendar permissions of a calendar on behalf of a recipient or delegate returns an empty calendar permissions collection.

Once a share recipient or delegate has been set up for a calendar, you can [update](https://learn.microsoft.com/en-us/graph/api/calendarpermission-update?view=graph-rest-1.0) only the **role** property to change the permissions of a recipient or delegate. You can't **update** the **allowedRoles**, **emailAddress**, **isInsideOrganization**, or **isRemovable** property. To change these properties, you should [delete](https://learn.microsoft.com/en-us/graph/api/calendarpermission-delete?view=graph-rest-1.0) the corresponding **calendarPermission** object and create another recipient or delegate in an Outlook client.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/calendar-list-calendarpermissions?view=graph-rest-1.0) | [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) | Get a collection of calendarPermission objects that describe the identity and roles of users with whom the specified calendar has been shared or delegated. |
| [Create](https://learn.microsoft.com/en-us/graph/api/calendar-post-calendarpermissions?view=graph-rest-1.0) | [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) | Create calendarPermission object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/calendarpermission-get?view=graph-rest-1.0) | [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) | Read properties and relationships of calendarPermission object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/calendarpermission-update?view=graph-rest-1.0) | [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) | Update calendarPermission object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/calendarpermission-delete?view=graph-rest-1.0) | None | Delete calendarPermission object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedRoles | [calendarRoleType](#calendarroletype-values) collection | List of allowed sharing or delegating permission levels for the calendar. The possible values are: `none`, `freeBusyRead`, `limitedRead`, `read`, `write`, `delegateWithoutPrivateEventAccess`, `delegateWithPrivateEventAccess`, `custom`. |
| emailAddress | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-1.0) | Represents a share recipient or delegate who has access to the calendar. For the "My Organization" share recipient, the **address** property is null. Read-only. |
| id | String | The unique identifier of the user \(recipient or delegate\) with whom the calendar has been shared. Read-only. |
| isInsideOrganization | Boolean | True if the user in context \(recipient or delegate\) is inside the same organization as the calendar owner. |
| isRemovable | Boolean | `True` if the user can be removed from the list of recipients or delegates for the specified calendar, `false` otherwise. The "My organization" user determines the permissions other people within your organization have to the given calendar. You can't remove "My organization" as a share recipient to a calendar. |
| role | [calendarRoleType](#calendarroletype-values) | Current permission level of the calendar share recipient or delegate. |

### calendarRoleType values

| Member | Description |
| :--- | :--- |
| none | Calendar isn't shared with the user. |
| freeBusyRead | User is a recipient who can view free/busy status of the owner on the calendar. |
| limitedRead | User is a recipient who can view free/busy status, and titles and locations of the events on the calendar. |
| read | User is a recipient who can view all the details of the events on the calendar, except for the owner's private events. |
| write | User is a recipient who can view all the details \(except for private events\) and edit events on the calendar. |
| delegateWithoutPrivateEventAccess | User is a delegate who has write access but can't view information of the owner's private events on the calendar. |
| delegateWithPrivateEventAccess | User is a delegate who has write access and can view information of the owner's private events on the calendar. |
| custom | User has custom permissions to the calendar. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowedRoles": ["string"],
  "emailAddress": {"@odata.type": "microsoft.graph.emailAddress"},
  "id": "String (identifier)",
  "isInsideOrganization": "boolean",
  "isRemovable": "boolean",
  "role": "string"
}
```
