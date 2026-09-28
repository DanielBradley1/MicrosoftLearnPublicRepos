<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# group resource type

Namespace: microsoft.graph

Represents a Microsoft Entra group, a Microsoft 365 group, or a security group. This resource is an open type that allows additional properties beyond those documented here.

Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

For performance reasons, the [create](https://learn.microsoft.com/en-us/graph/api/group-post-groups?view=graph-rest-1.0), [get](https://learn.microsoft.com/en-us/graph/api/group-get?view=graph-rest-1.0), and [list](https://learn.microsoft.com/en-us/graph/api/group-list?view=graph-rest-1.0) operations return only a subset of more commonly used properties by default. These *default* properties are noted in the [Properties](#properties) section. To get any of the properties not returned by default, specify them in a `$select` OData query option.

This resource supports:

- Adding your data to custom properties as [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).
- Subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview).
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/group-delta?view=graph-rest-1.0) function.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | List group objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/group-post-groups?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Create a new group. It can be a Microsoft 365 group, dynamic group, or security group. |
| [Get](https://learn.microsoft.com/en-us/graph/api/group-get?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Read properties of a group object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/group-update?view=graph-rest-1.0) | None | Update the properties of a group object. |
| [Upsert](https://learn.microsoft.com/en-us/graph/api/group-upsert?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Create a new group if it doesn't exist, or update the properties of an existing group. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/group-delete?view=graph-rest-1.0) | None | Delete group object. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/group-delta?view=graph-rest-1.0) | group collection | Get incremental changes for groups. |
| **Group management** |  |  |
| [List members](https://learn.microsoft.com/en-us/graph/api/group-list-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the direct members of this group from the **members** navigation property. |
| [Add members](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0) | None | Add a member to this group by posting to the **members** navigation property \(supported for security groups and Microsoft 365 groups only\). |
| [Remove member](https://learn.microsoft.com/en-us/graph/api/group-delete-members?view=graph-rest-1.0) | None | Remove a member from a Microsoft 365 group or a security group through the **members** navigation property. |
| [List owners](https://learn.microsoft.com/en-us/graph/api/group-list-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the owners of the group from the **owners** navigation property. |
| [Add owners](https://learn.microsoft.com/en-us/graph/api/group-post-owners?view=graph-rest-1.0) | None | Add a new owner for the group by posting to the **owners** navigation property \(supported for security groups and Microsoft 365 groups only\). |
| [Remove owner](https://learn.microsoft.com/en-us/graph/api/group-delete-owners?view=graph-rest-1.0) | None | Remove an owner from a Microsoft 365 group or a security group through the **owners** navigation property. |
| [List memberships](https://learn.microsoft.com/en-us/graph/api/group-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups, admin roles, and and administrative units that this group is a direct member of from the memberOf navigation property. |
| [List transitive members](https://learn.microsoft.com/en-us/graph/api/group-list-transitivemembers?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the users, groups, and devices that are members, including nested members of this group. |
| [List transitive memberships](https://learn.microsoft.com/en-us/graph/api/group-list-transitivememberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | List the groups that this group is a member of. This operation is transitive and includes the groups that this group is a nested member of. |
| [List group lifecycle policies](https://learn.microsoft.com/en-us/graph/api/group-list-grouplifecyclepolicies?view=graph-rest-1.0) | [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) collection | List group lifecycle policies. |
| [Assign license](https://learn.microsoft.com/en-us/graph/api/group-assignlicense?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Add or remove subscriptions for the group. You can also enable and disable specific plans associated with a subscription. |
| [Renew](https://learn.microsoft.com/en-us/graph/api/group-renew?view=graph-rest-1.0) | Boolean | Renews a group's expiration. Renewing extends the group expiration by the number of days defined in the policy. |
| [Validate properties](https://learn.microsoft.com/en-us/graph/api/group-validateproperties?view=graph-rest-1.0) | JSON | Validate that a Microsoft 365 group's display name or mail nickname complies with naming policies. |
| **App role assignments** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the apps and app roles assigned to this group. |
| [Add](https://learn.microsoft.com/en-us/graph/api/group-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Assign an app role to this group. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/group-delete-approleassignments?view=graph-rest-1.0) | None. | Remove an app role assignment from this group. |
| **Calendar** |  |  |
| [Get calendar](https://learn.microsoft.com/en-us/graph/api/calendar-get?view=graph-rest-1.0) | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Get the group's calendar. |
| [Update calendar](https://learn.microsoft.com/en-us/graph/api/calendar-update?view=graph-rest-1.0) | None | Update the group's calendar. |
| [List events](https://learn.microsoft.com/en-us/graph/api/group-list-events?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | Get an event object collection. |
| [Create event](https://learn.microsoft.com/en-us/graph/api/group-post-events?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Create a new event by posting to the events collection. |
| [Get event](https://learn.microsoft.com/en-us/graph/api/group-get-event?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Read properties of an event object. |
| [Update event](https://learn.microsoft.com/en-us/graph/api/group-update-event?view=graph-rest-1.0) | None | Update the properties of an event object. |
| [Delete event](https://learn.microsoft.com/en-us/graph/api/group-delete-event?view=graph-rest-1.0) | None | Delete event object. |
| [List calendar view](https://learn.microsoft.com/en-us/graph/api/group-list-calendarview?view=graph-rest-1.0) | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | Get a collection of events in a specified time window. |
| **Conversations** |  |  |
| [List conversations](https://learn.microsoft.com/en-us/graph/api/group-list-conversations?view=graph-rest-1.0) | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) collection | Get a conversation object collection. |
| [Create conversation](https://learn.microsoft.com/en-us/graph/api/group-post-conversations?view=graph-rest-1.0) | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Create a new conversation by posting to the conversations collection. |
| [Get conversation](https://learn.microsoft.com/en-us/graph/api/group-get-conversation?view=graph-rest-1.0) | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Read properties of a conversation object. |
| [Delete conversation](https://learn.microsoft.com/en-us/graph/api/group-delete-conversation?view=graph-rest-1.0) | None | Delete conversation object. |
| [List threads](https://learn.microsoft.com/en-us/graph/api/group-list-threads?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) collection | Get all the threads of a group. |
| [Create thread](https://learn.microsoft.com/en-us/graph/api/group-post-threads?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) | Create a new conversation thread. |
| [Get thread](https://learn.microsoft.com/en-us/graph/api/group-get-thread?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) | Read properties of a thread object. |
| [Update thread](https://learn.microsoft.com/en-us/graph/api/group-update-thread?view=graph-rest-1.0) | None | Update properties of a thread object. |
| [Delete thread](https://learn.microsoft.com/en-us/graph/api/group-delete-thread?view=graph-rest-1.0) | None | Delete thread object. |
| [List accepted senders](https://learn.microsoft.com/en-us/graph/api/group-list-acceptedsenders?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get a list of users or groups that are in the accepted-senders list for this group. |
| [Add accepted sender](https://learn.microsoft.com/en-us/graph/api/group-post-acceptedsenders?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add a User or Group to the acceptSenders collection. |
| [Remove accepted sender](https://learn.microsoft.com/en-us/graph/api/group-delete-acceptedsenders?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Remove a User or Group from the acceptedSenders collection. |
| [List rejected senders](https://learn.microsoft.com/en-us/graph/api/group-list-rejectedsenders?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get a list of users or groups that are in the rejected-senders list for this group. |
| [Add rejected sender](https://learn.microsoft.com/en-us/graph/api/group-post-rejectedsenders?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add a new User or Group to the rejectedSenders collection. |
| [Remove rejected sender](https://learn.microsoft.com/en-us/graph/api/group-delete-rejectedsenders?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Remove new User or Group from the rejectedSenders collection. |
| **Directory objects** |  |  |
| [List deleted items](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve the groups deleted in the tenant in the last 30 days. |
| [Get deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a deleted group by ID. |
| [Restore deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Restore a group deleted in the tenant in the last 30 days. |
| [Permanently delete item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Permanently delete a deleted group from the tenant. |
| [List deleted items owned by user](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-getuserownedobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve the user's groups deleted in the tenant in the last 30 days. |
| [Check member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmembergroups?view=graph-rest-1.0) | String collection | Check for membership in a list of groups. The function is transitive. |
| [Get member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmembergroups?view=graph-rest-1.0) | String collection | Return all the groups that the group is a member of. The function is transitive. |
| [Check member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Check for membership in a list of group, directory role, or administrative unit objects. The function is transitive. |
| [Get member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmemberobjects?view=graph-rest-1.0) | String collection | Return all of the groups and administrative units that the group is a member of. The function is transitive. |
| **Drive** |  |  |
| [Get drive](https://learn.microsoft.com/en-us/graph/api/drive-get?view=graph-rest-1.0) | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | Retrieve the properties and relationships of a Drive resource. |
| [List children](https://learn.microsoft.com/en-us/graph/api/driveitem-list-children?view=graph-rest-1.0) | [DriveItems](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Return a collection of DriveItems in the children relationship of a DriveItem. |
| **Group settings** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list-settings?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) collection | List properties of all setting objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/group-post-settings?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) | Create a setting object based on a groupSettingTemplate. The POST request must provide settingValues for all the settings defined in the template. Only groups specific templates can be used for this operation. |
| [Get](https://learn.microsoft.com/en-us/graph/api/groupsetting-get?view=graph-rest-1.0) | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) | Read properties of a specific setting object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/groupsetting-update?view=graph-rest-1.0) | None | Update a setting object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/groupsetting-delete?view=graph-rest-1.0) | None | Delete a setting object. |
| [List setting template](https://learn.microsoft.com/en-us/graph/api/groupsettingtemplate-list?view=graph-rest-1.0) | None | List properties of all setting templates. |
| [Get setting template](https://learn.microsoft.com/en-us/graph/api/groupsettingtemplate-get?view=graph-rest-1.0) | None | Read properties of a setting template. |
| **Notes** |  |  |
| [List notebooks](https://learn.microsoft.com/en-us/graph/api/onenote-list-notebooks?view=graph-rest-1.0) | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) collection | Retrieve a list of notebook objects. |
| [Create notebook](https://learn.microsoft.com/en-us/graph/api/onenote-post-notebooks?view=graph-rest-1.0) | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) | Create a new OneNote notebook. |
| **Profile photo** |  |  |
| [Get](https://learn.microsoft.com/en-us/graph/api/profilephoto-get?view=graph-rest-1.0) | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | Get the specified profilePhoto or its metadata \(profilePhoto properties\). |
| [Update](https://learn.microsoft.com/en-us/graph/api/profilephoto-update?view=graph-rest-1.0) | None | Update the photo for any user in the tenant including the signed-in user, or the specified group or contact. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/profilephoto-delete?view=graph-rest-1.0) | None | Delete the photo for any user in the tenant including the signed-in user or the specified group. |
| **Planner** |  |  |
| [List plans](https://learn.microsoft.com/en-us/graph/api/plannergroup-list-plans?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) collection | Get plans assigned to the group. |
| **Posts** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/conversationthread-list-posts?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) collection | Get posts in a conversation thread. |
| [Get](https://learn.microsoft.com/en-us/graph/api/post-get?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Get a specific post. |
| [Reply to post](https://learn.microsoft.com/en-us/graph/api/post-reply?view=graph-rest-1.0) | None | Reply to a post. |
| [Forward post](https://learn.microsoft.com/en-us/graph/api/post-forward?view=graph-rest-1.0) | None | Forward a post. |
| **Other group resources** |  |  |
| [List permission grants](https://learn.microsoft.com/en-us/graph/api/group-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List permissions that are granted to apps to access the group. |
| **User settings** |  |  |
| [Add favorite](https://learn.microsoft.com/en-us/graph/api/group-addfavorite?view=graph-rest-1.0) | None | Add the group to the list of the signed-in user's favorite groups. Supported for only Microsoft 365 groups. |
| [Remove favorite](https://learn.microsoft.com/en-us/graph/api/group-removefavorite?view=graph-rest-1.0) | None | Remove the group from the list of the signed-in user's favorite groups. Supported for only Microsoft 365 groups. |
| [List member of](https://learn.microsoft.com/en-us/graph/api/group-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups and administrative units that this user is a direct member of, from the **memberOf** navigation property. |
| [List joined teams](https://learn.microsoft.com/en-us/graph/api/user-list-joinedteams?view=graph-rest-1.0) | [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) collection | Get the Microsoft Teams that the user is a direct member of. |
| [List associated teams](https://learn.microsoft.com/en-us/graph/api/associatedteaminfo-list?view=graph-rest-1.0) | [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) collection | Get the list of [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) objects in Microsoft Teams that a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) is associated with. |
| [Subscribe by mail](https://learn.microsoft.com/en-us/graph/api/group-subscribebymail?view=graph-rest-1.0) | None | Set the isSubscribedByMail property to `true`. Enabling the signed-in user to receive email conversations. Supported for only Microsoft 365 groups. |
| [Unsubscribe by mail](https://learn.microsoft.com/en-us/graph/api/group-unsubscribebymail?view=graph-rest-1.0) | None | Set the isSubscribedByMail property to `false`. Disabling the signed-in user from receive email conversations. Supported for only Microsoft 365 groups. |
| [Reset unseen count](https://learn.microsoft.com/en-us/graph/api/group-resetunseencount?view=graph-rest-1.0) | None | Reset the unseenCount to 0 of all the posts that the signed-in user hasn't seen since their last visit. Supported for only Microsoft 365 groups. |

## Properties

Important

Specific usage of `$filter` and the `$search` query parameter is supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#group-properties).

| Property | Type | Description |
| :--- | :--- | :--- |
| accessType | [groupAccessType](https://learn.microsoft.com/en-us/graph/api/resources/groupaccesstype?view=graph-rest-1.0) | Indicates the type of access to the group. The possible values are: `none`, `private`, `secret`, `public`, `unknownFutureValue`. Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| allowExternalSenders | Boolean | Indicates if people external to the organization can send messages to the group. The default value is `false`.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| assignedLabels | [assignedLabel](https://learn.microsoft.com/en-us/graph/api/resources/assignedlabel?view=graph-rest-1.0) collection | The list of sensitivity label pairs \(label ID, label name\) associated with a Microsoft 365 group or a cloud security group. Requires a Microsoft Entra ID P1 license.  <br>  <br>Requires `$select` to retrieve. This property can be specified during group creation or update. However, for cloud security groups, it's immutable once set. This property can be updated only in delegated scenarios where the caller requires both the Microsoft Graph permission and [a supported administrator role](https://learn.microsoft.com/en-us/purview/get-started-with-sensitivity-labels#permissions-required-to-create-and-manage-sensitivity-labels). See [Key differences from Microsoft 365 group labeling](https://learn.microsoft.com/en-us/entra/identity/users/groups-sensitivity-labels#key-differences-from-microsoft-365-group-labeling) to learn more about managing this property for Microsoft 365 vs. cloud security groups. |
| assignedLicenses | [assignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/assignedlicense?view=graph-rest-1.0) collection | The licenses that are assigned to the group.  <br>  <br>Requires `$select` to retrieve. Supports `$filter` \(`eq`\). Read-only. |
| autoSubscribeNewMembers | Boolean | Indicates if new members added to the group are autosubscribed to receive email notifications. You can set this property in a PATCH request for the group; don't set it in the initial POST request that creates the group. Default value is `false`.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| classification | String | Describes a classification for the group \(such as low, medium, or high business impact\). Valid values for this property are defined by creating a ClassificationList [setting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) value, based on the [template definition](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate?view=graph-rest-1.0).  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `startsWith`\). |
| createdDateTime | DateTimeOffset | Timestamp of when the group was created. The value can't be modified and is automatically populated when the group is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Returned by default. Read-only. |
| deletedDateTime | DateTimeOffset | For some Microsoft Entra objects \(user, group, application\), if the object is deleted, it's first logically deleted, and this property is updated with the date and time when the object was deleted. Otherwise this property is `null`. If the object is restored, this property is updated to `null`. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). |
| description | String | An optional description for the group.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `startsWith`\) and `$search`. |
| displayName | String | The display name for the group. This property is required when a group is created and can't be cleared during updates. Maximum length is 256 characters.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\), `$search`, and `$orderby`. |
| expirationDateTime | DateTimeOffset | Timestamp of when the group is set to expire. It's `null` for security groups, but for Microsoft 365 groups, it represents when the group is set to expire as defined in the [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0). The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\). Read-only. |
| groupTypes | String collection | Specifies the group type and its membership.  <br>  <br>If the collection contains `Unified`, the group is a Microsoft 365 group; otherwise, it's either a security group or a distribution group. For details, see [groups overview](https://learn.microsoft.com/en-us/graph/api/resources/groups-overview?view=graph-rest-1.0).  <br>  <br>If the collection includes `DynamicMembership`, the group has dynamic membership; otherwise, membership is static.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `not`\). |
| hasMembersWithLicenseErrors | Boolean | Indicates whether there are members in this group that have license errors from its group-based license assignment.  <br>  <br>This property is never returned on a GET operation. You can use it as a $filter argument to get groups that have members with license errors \(that is, filter for this property being true\). See an [example](https://learn.microsoft.com/en-us/graph/api/group-list?view=graph-rest-1.0).  <br>  <br>Supports `$filter` \(`eq`\). |
| hideFromAddressLists | Boolean | True if the group isn't displayed in certain parts of the Outlook UI: the **Address Book**, address lists for selecting message recipients, and the **Browse Groups** dialog for searching groups; otherwise, false. The default value is `false`.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| hideFromOutlookClients | Boolean | True if the group isn't displayed in Outlook clients, such as Outlook for Windows and Outlook on the web; otherwise, false. The default value is `false`.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| id | String | The unique identifier for the group.  <br>  <br>Returned by default. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Key. Not nullable. Read-only.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| isArchived | Boolean | When a group is associated with a team, this property determines whether the team is in read-only mode.  <br>To read this property, use the `/group/{groupId}/team` endpoint or the [Get team](https://learn.microsoft.com/en-us/graph/api/team-get?view=graph-rest-1.0) API. To update this property, use the [archiveTeam](https://learn.microsoft.com/en-us/graph/api/team-archive?view=graph-rest-1.0) and [unarchiveTeam](https://learn.microsoft.com/en-us/graph/api/team-unarchive?view=graph-rest-1.0) APIs. |
| isAssignableToRole | Boolean | Indicates whether this group can be assigned to a Microsoft Entra role. Optional.  <br>  <br>This property can only be set while creating the group and is immutable. If set to `true`, the **securityEnabled** property must also be set to `true`, **visibility** must be `Hidden`, and the group can't be a dynamic group \(that is, **groupTypes** can't contain `DynamicMembership`\).  <br>  <br>Only callers with at least the Privileged Role Administrator role can set this property. The caller must also be assigned the *RoleManagement.ReadWrite.Directory* permission to set this property or update the membership of such groups. For more, see [Using a group to manage Microsoft Entra role assignments](https://go.microsoft.com/fwlink/?linkid=2103037)  <br>  <br>Using this feature requires a Microsoft Entra ID P1 license. Returned by default. Supports `$filter` \(`eq`, `ne`, `not`\). |
| isFavorite | Boolean | Indicates whether the user marked the group as favorite. Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| isManagementRestricted | Boolean | Indicates whether the group is a member of a restricted management administrative unit. If not set, the default value is `null` and the default behavior is false. Read-only.  <br>  <br>To manage a group member of a restricted management administrative unit, the administrator or calling app must be assigned a Microsoft Entra role at the scope of the restricted management administrative unit.  <br>  <br>Requires `$select` to retrieve. |
| isSubscribedByMail | Boolean | Indicates whether the signed-in user is subscribed to receive email conversations. The default value is `true`.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| licenseProcessingState | String | Indicates the status of the group license assignment to all group members. The default value is `false`. Read-only. Possible values: `QueuedForProcessing`, `ProcessingInProgress`, and `ProcessingComplete`.  <br>  <br>Requires `$select` to retrieve. Read-only. |
| mail | String | The SMTP address for the group, for example, "serviceadmins@contoso.com".  <br>  <br>Returned by default. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\). |
| mailEnabled | Boolean | Specifies whether the group is mail-enabled. Required.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`\). |
| mailNickname | String | The mail alias for the group, unique for Microsoft 365 groups in the organization. Maximum length is 64 characters. This property can contain only characters in the [ASCII character set 0 - 127](https://learn.microsoft.com/en-us/office/vba/language/reference/user-interface-help/character-set-0127) except the following characters: ` @ () \\ [] " ; : <> , SPACE`.  <br>  <br>Required. Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\). |
| membershipRule | String | The rule that determines members for this group if the group is a dynamic group \(groupTypes contains `DynamicMembership`\). For more information about the syntax of the membership rule, see [Membership Rules syntax](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership).  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `startsWith`\). |
| membershipRuleProcessingState | String | Indicates whether the dynamic membership processing is on or paused. Possible values are `On` or `Paused`.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| onPremisesDomainName | String | Contains the on-premises **domain FQDN**, also called **dnsDomainName** synchronized from the on-premises directory. The property is only populated for customers synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect.  <br>  <br>Returned by default. Read-only. |
| onPremisesExtensionAttributes | [onPremisesExtensionAttributes](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes?view=graph-rest-1.0) | Complex type containing extension attributes 1-15 for the group, synchronized from on-premises Active Directory. Returned only on `$select`. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| onPremisesLastSyncDateTime | DateTimeOffset | Indicates the last time at which the group was synced with the on-premises directory. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Returned by default. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\). |
| onPremisesNetBiosName | String | Contains the on-premises **netBios name** synchronized from the on-premises directory. The property is only populated for customers synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect.  <br>  <br>Returned by default. Read-only. |
| onPremisesProvisioningErrors | [onPremisesProvisioningError](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesprovisioningerror?view=graph-rest-1.0) collection | Errors when using Microsoft synchronization product during provisioning.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `not`\). |
| onPremisesSamAccountName | String | Contains the on-premises **SAM account name** synchronized from the on-premises directory. The property is only populated for customers synchronizing their on-premises directory to Microsoft Entra ID via Microsoft Entra Connect.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`\). Read-only. |
| onPremisesSecurityIdentifier | String | Contains the on-premises security identifier \(SID\) for the group synchronized from on-premises to the cloud. Read-only.  <br>  <br>Returned by default. Supports `$filter` \(`eq` including on `null` values\). |
| onPremisesSyncEnabled | Boolean | `true` if this group is synced from an on-premises directory; `false` if this group was originally synced from an on-premises directory but is no longer synced; **null** if this object has never synced from an on-premises directory \(default\).  <br>  <br>Returned by default. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`, and `eq` on `null` values\). |
| preferredDataLocation | String | The preferred data location for the Microsoft 365 group. By default, the group inherits the group creator's preferred data location. To set this property, the calling app must be granted the *Directory.ReadWrite.All* permission and the user be assigned at least one of the following [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json):  <br><br><br>- Directory Writer<br>- Exchange Administrator<br>- SharePoint Administrator<br><br>  <br>For more information about this property, see [OneDrive Online Multi-Geo](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-introduction).  <br>  <br>Nullable. Returned by default. |
| preferredLanguage | String | The preferred language for a Microsoft 365 group. Should follow ISO 639-1 Code; for example, `en-US`.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\). |
| proxyAddresses | String collection | Email addresses for the group that direct to the same group mailbox. For example: `["SMTP: bob@contoso.com", "smtp: bob@sales.contoso.com"]`. The **any** operator is required to filter expressions on multi-valued properties.  <br>  <br>Returned by default. Read-only. Not nullable. Supports `$filter` \(`eq`, `not`, `ge`, `le`, `startsWith`, `endsWith`, `/$count eq 0`, `/$count ne 0`\). |
| renewedDateTime | DateTimeOffset | Timestamp of when the group was last renewed. This value can't be modified directly and is only updated via the [renew service action](https://learn.microsoft.com/en-us/graph/api/group-renew?view=graph-rest-1.0). The Timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\). Read-only. |
| resourceBehaviorOptions | String collection | Specifies the group behaviors that can be set for a Microsoft 365 group during creation. This property can be set only as part of creation \(POST\). For the list of possible values, see [Microsoft 365 group behaviors and provisioning options](https://learn.microsoft.com/en-us/graph/group-set-options). |
| resourceProvisioningOptions | String collection | Specifies the group resources that are associated with the Microsoft 365 group. The possible value is `Team`. For more information, see [Microsoft 365 group behaviors and provisioning options](https://learn.microsoft.com/en-us/graph/group-set-options).  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `not`, `startsWith`\). |
| securityEnabled | Boolean | Specifies whether the group is a security group. Required.  <br>  <br>Returned by default. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| securityIdentifier | String | Security identifier of the group, used in Windows scenarios. Read-only.  <br>  <br>Returned by default. |
| serviceProvisioningErrors | [serviceProvisioningError](https://learn.microsoft.com/en-us/graph/api/resources/serviceprovisioningerror?view=graph-rest-1.0) collection | Errors published by a federated service describing a nontransient, service-specific error regarding the properties or link from a group object.  <br>  <br>Supports `$filter` \(`eq`, `not`, for isResolved and serviceInstance\). |
| theme | string | Specifies a Microsoft 365 group's color theme. Possible values are `Teal`, `Purple`, `Green`, `Blue`, `Pink`, `Orange`, or `Red`.  <br>  <br>Returned by default. |
| uniqueName | String | The unique identifier that can be assigned to a group and used as an alternate key. Immutable. Read-only. |
| unseenConversationsCount | Int32 | Count of conversations that have had one or more new posts delivered since the signed-in user's last visit to the group. This property is the same as **unseenCount**.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| unseenCount | Int32 | Count of conversations that have received new posts since the signed-in user last visited the group. This property is the same as **unseenConversationsCount**.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| unseenMessagesCount | Int32 | Count of new posts that have been delivered to the group's conversations since the signed-in user's last visit to the group.  <br>  <br>Requires `$select` to retrieve. Supported only on the Get group API \(`GET /groups/{ID}`\). |
| visibility | String | Specifies the group join policy and group content visibility for groups. The possible values are: `Private`, `Public`, or `HiddenMembership`. `HiddenMembership` can be set only for Microsoft 365 groups when the groups are created. It can't be updated later. Other values of visibility can be updated after group creation.  <br>If visibility value isn't specified during group creation on Microsoft Graph, a security group is created as `Private` by default, and the Microsoft 365 group is `Public`. Groups assignable to roles are always `Private`. To learn more, see [group visibility options](#group-visibility-options).  <br>  <br>Returned by default. Nullable. |

### Group visibility options

| Value | Description |
| :--- | --- |
| Public | Anyone can join the group without needing owner permission.  <br>Anyone can view the attributes of the group.  <br>Anyone can see the members of the group. |
| Private | Owner permission is needed to join the group.  <br>Anyone can view the attributes of the group.  <br>Anyone can see the members of the group. |
| HiddenMembership | Owner permission is needed to join the group.  <br>Guests can't view the attributes of the group.  <br>Nonmembers can't see the members of the group. This setting doesn't affect visibility of group owners.  <br>Administrators \(global, company, user, and helpdesk\) can view the membership of the group.  <br>The group appears in the global address book \(GAL\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| acceptedSenders | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The list of users or groups allowed to create posts or calendar events in this group. If this list is nonempty, then only users or groups listed here are allowed to post. |
| appRoleAssignments | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Represents the app roles granted to a group for an application. Supports `$expand`. |
| calendar | [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | The group's calendar. Read-only. |
| calendarView | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | The calendar view for the calendar. Read-only. |
| conversations | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) collection | The group's conversations. |
| createdOnBehalfOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The user \(or application\) that created the group. NOTE: This property isn't set if the user is an administrator. Read-only. |
| drive | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | The group's default drive. Read-only. |
| drives | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) collection | The group's drives. Read-only. |
| events | [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection | The group's calendar events. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the group. Read-only. Nullable. |
| groupLifecyclePolicies | [groupLifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/grouplifecyclepolicy?view=graph-rest-1.0) collection | The collection of lifecycle policies for this group. Read-only. Nullable. |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Groups that this group is a member of. HTTP Methods: GET \(supported for all groups\). Read-only. Nullable. Supports `$expand`. |
| members | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The members of this group, who can be users, devices, other groups, or service principals. Supports the [List members](https://learn.microsoft.com/en-us/graph/api/group-list-members?view=graph-rest-1.0), [Add member](https://learn.microsoft.com/en-us/graph/api/group-post-members?view=graph-rest-1.0), and [Remove member](https://learn.microsoft.com/en-us/graph/api/group-delete-members?view=graph-rest-1.0) operations. Nullable.  <br>Supports `$expand` including nested `$select`. For example, `/groups?$filter=startsWith(displayName,'Role')&$select=id,displayName&$expand=members($select=id,userPrincipalName,displayName)`. |
| membersWithLicenseErrors | [User](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | A list of group members with license errors from this group-based license assignment. Read-only. |
| onenote | [Onenote](https://learn.microsoft.com/en-us/graph/api/resources/onenote?view=graph-rest-1.0) | Read-only. |
| owners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The owners of the group who can be users or service principals. Limited to 100 owners. Nullable.<br><br><li>If this property isn&#39;t specified when creating a Microsoft 365 group the calling user (admin or non-admin) is automatically assigned as the group owner. </li><br><br><li>A non-admin user can&#39;t explicitly add themselves to this collection when they&#39;re creating the group. For more information, see the related <a href="https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update" data-linktype="absolute-path">known issue</a>. </li><br><br><li>For security groups, the admin user isn&#39;t automatically added to this collection. For more information, see the related <a href="https://learn.microsoft.com/en-us/graph/known-issues#non-admin-user-cant-add-self-as-group-owner-during-group-creation-or-update" data-linktype="absolute-path">known issue</a>.<br><br> Supports <code>$filter</code> (<code>/$count eq 0</code>, <code>/$count ne 0</code>, <code>/$count eq 1</code>, <code>/$count ne 1</code>); Supports <code>$expand</code> including nested <code>$select</code>. For example, <code>/groups?$filter=startsWith(displayName,&#39;Role&#39;)&amp;$select=id,displayName&amp;$expand=owners($select=id,userPrincipalName,displayName)</code>.</li> |
| photo | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) | The group's profile photo |
| photos | [profilePhoto](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto?view=graph-rest-1.0) collection | The profile photos owned by the group. Read-only. Nullable. |
| planner | [plannerGroup](https://learn.microsoft.com/en-us/graph/api/resources/plannergroup?view=graph-rest-1.0) | Entry-point to Planner resource that might exist for a Unified Group. |
| rejectedSenders | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The list of users or groups not allowed to create posts or calendar events in this group. Nullable |
| settings | [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting?view=graph-rest-1.0) collection | Settings that can govern this group's behavior, like whether members can invite guests to the group. Nullable. |
| sites | [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) collection | The list of SharePoint sites in this group. Access the default site with /sites/root. |
| team | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | The team associated with this group. |
| threads | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) collection | The group's conversation threads. Nullable. |
| transitiveMemberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The groups that a group is a member of, either directly or through nested membership. Nullable. |
| transitiveMembers | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The direct and transitive members of a group. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "accessType": "String",
  "allowExternalSenders": "Boolean",
  "acceptedSenders": [{ "@odata.type": "microsoft.graph.directoryObject" }],
  "assignedLicenses": [{ "@odata.type": "microsoft.graph.assignedLicense" }],
  "autoSubscribeNewMembers": "Boolean",
  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "calendarView": [{ "@odata.type": "microsoft.graph.event" }],
  "classification": "String",
  "conversations": [{ "@odata.type": "microsoft.graph.conversation" }],
  "createdDateTime": "String (timestamp)",
  "createdOnBehalfOf": { "@odata.type": "microsoft.graph.directoryObject" },
  "deletedDateTime":  "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "events": [{ "@odata.type": "microsoft.graph.event" }],
  "groupTypes": ["String"],
  "hasMembersWithLicenseErrors": "Boolean",
  "hideFromAddressLists": "Boolean",
  "hideFromOutlookClients": "Boolean",
  "id": "String (identifier)",
  "isAssignableToRole": "Boolean",
  "isFavorite": "Boolean",
  "isManagementRestricted": "Boolean",
  "isSubscribedByMail": "Boolean",
  "licenseProcessingState": "String",
  "mail": "String",
  "mailEnabled": "Boolean",
  "mailNickname": "String",
  "memberOf": [{ "@odata.type": "microsoft.graph.directoryObject" }],
  "members": [{ "@odata.type": "microsoft.graph.directoryObject" }],
  "membersWithLicenseErrors": [{ "@odata.type": "microsoft.graph.user" }],
  "onPremisesDomainName": "String",
  "onPremisesExtensionAttributes": { "@odata.type": "microsoft.graph.onPremisesExtensionAttributes" },
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesNetBiosName": "String",
  "onPremisesProvisioningErrors": [
    { "@odata.type": "microsoft.graph.onPremisesProvisioningError" }
  ],
  "onPremisesSecurityIdentifier": "String",
  "onPremisesSyncEnabled": "Boolean",
  "owners": [{ "@odata.type": "microsoft.graph.directoryObject" }],
  "preferredDataLocation": "String",
  "proxyAddresses": ["String"],
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "photos": [{ "@odata.type": "microsoft.graph.profilePhoto" }],
  "rejectedSenders": [{ "@odata.type": "microsoft.graph.directoryObject" }],
  "renewedDateTime": "String (timestamp)",
  "resourceBehaviorOptions": ["String"],
  "resourceProvisioningOptions": ["String"],
  "securityEnabled": "Boolean",
  "securityIdentifier": "String",
  "serviceProvisioningErrors": [
    { "@odata.type": "microsoft.graph.serviceProvisioningXmlError" }
  ],
  "sites": [{ "@odata.type": "microsoft.graph.site" }],
  "threads": [{ "@odata.type": "microsoft.graph.conversationThread" }],
  "uniqueName": "String",
  "unseenConversationsCount": "Int32",
  "unseenCount": "Int32",
  "unseenMessagesCount": "Int32",
  "visibility": "String"
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
