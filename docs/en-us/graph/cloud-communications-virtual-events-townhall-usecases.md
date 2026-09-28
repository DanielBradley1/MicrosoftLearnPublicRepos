<!-- Source: https://learn.microsoft.com/en-us/graph/cloud-communications-virtual-events-townhall-usecases -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# Virtual events town hall API use cases

Microsoft Graph virtual events town hall APIs allow you to get Teams town hall data and programmatically create, update, and cancel a Teams town hall.

For you to make the best use of the Microsoft Graph virtual events town hall APIs, it’s helpful to understand the personas for the users who access the Teams town hall experience:

- **Organizers** are employees \(in your organization\) who manage the town hall. They're the authority on when town halls take place and who participates. They configure town hall details such as title, theme, attendee experience, and email rules.
- **Presenters** are employees \(in your organization\) or guests who lead the town hall.
- **Attendees** are either employees \(in your organization\) or guests who join the town hall and are either invited via email or the link to the town hall event is shared with them.
- **Teams tenant administrator** must authorize custom applications with appropriate permissions.

You can use the following resource types to build your town hall solution:

- [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall) – Used to create, get, update, publish, and cancel a Teams town hall.
- [virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter) – Used to create, get, list, update, and delete a presenter for a Teams town hall.
- [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession) – A town hall created via Microsoft Graph APIs has one session that inherits the properties of online meetings.

## Solutions you can build

The following table lists some solutions you can build by using the Teams client and Microsoft Graph town hall APIs and webhooks.

| Solutions | Description |
| --- | --- |
| [Create/update/cancel](#createupdatecancel) | Programmatically create, update, and cancel Teams town hall. |
| [Data sync](#data-sync) | Pull Teams town hall data in a custom application. |
| [Email communication](#email-communication) | Use your own email infrastructure to send town hall-related notification emails. |

Note

To build any Microsoft Graph solutions, you need to register and give the right permissions to your application. For more information, see [Authentication and authorization basics](https://learn.microsoft.com/en-us/graph/auth/auth-concepts).

### Resource-specific consent \(RSC\) for virtual events

Resource-specific consent \(RSC\) allows apps to request permissions scoped to a specific webinar or town hall instead of requiring global admin privileges. The RSC permissions improves security, simplifies consent flows, and enables developers to build integrations that respect organizational boundaries.

#### Enabled Microsoft Graph virtual events APIs and RSC permissions

| RSC permission | APIs | Description |
| :--- | :--- | :--- |
| VirtualEvent.Read.Chat | [Webinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar) and [town hall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall) | Read information for this webinar or town hall, including schedules, speakers, event settings, and webinar registrations. |
| OnlineMeetingArtifact.Read.Chat | [Attendance report](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport) and [attendance record](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord) | Read attendance reports and attendance records for this webinar or town hall. |
| VirtualEventRegistration-Anon.ReadWrite.Chat | [Virtual event registrations](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration) | Register attendees and cancel registrations for this webinar or town hall. |

#### Traditional authentication flow

If RSC isn't required or feasible, you can use the following traditional OAuth flows:

- *App-only token flow*: Use it for backend services or automation scenarios where the app acts without user context.
- *Delegated \(user\) token flow*: Use when actions require user context and consent.

#### When to use RSC vs. traditional token flow

| Scenario | Recommended approach |
| :--- | :--- |
| App needs access to a specific webinar or town hall only | RSC |
| App requires tenant-wide access to multiple events | App-only token flow |
| User-driven actions like organizer managing events | Delegated token flow |
| Compliance or security mandates require least privilege | RSC |

#### Getting started using RSC permissions

The following steps describe how to get started with setting up your app and using RSC permissions:

1. Register your app and define RSC permissions in the app manifest.
2. Publish your app via the Teams developer portal or partner center.
3. Admin grants RSC in the Teams admin center.
4. Use the Microsoft Graph APIs for webinars and town halls with scoped permissions.

### Create/update/cancel

- Use the [Create townhall API](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-post-townhalls) to create a draft of the event, followed by the [Publish townhall API](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-publish) to complete the creation and make it visible to its audience.

  - The town hall created via Microsoft Graph APIs is a Teams town hall event that’s visible and editable in the Teams client.
  - Just like in Teams, only the organizer can create, publish, and cancel town halls. The create townhall API only supports delegated permissions on behalf of the organizer.

- Like in Teams, coorganizers can update town halls. To update a town hall, use the [Update townhall API](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-update) with delegated permissions on behalf of the coorganizer.

### Data sync

- Use the [Get townhall API](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-get) to pull data regarding a specific town hall, such as who is invited, who created the town hall, and who are the coorganizers.
- [List all the town halls in a tenant](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-list-townhalls), including the town halls for which the user is an organizer or coorganizer. This scenario is supported for [delegated](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-getbyuserrole) and [application](https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-getbyuseridandrole) permissions. These APIs are currently only available in the beta endpoint.

### Email communication

You can turn off email communications to attendees when you [create the town hall](https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-post-townhalls). In the **settings** property, set `isAttendeeEmailNotificationEnabled` to `false`.Emails are still sent to organizers, coorganizers, and presenters \(internal and external\).
