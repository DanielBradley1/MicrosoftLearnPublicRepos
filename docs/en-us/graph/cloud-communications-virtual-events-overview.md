<!-- Source: https://learn.microsoft.com/en-us/graph/cloud-communications-virtual-events-overview -->
<!-- Sitemap-Last-Modified: 2024-11-27 -->

# Choose the right Teams meeting type

Microsoft Teams and Microsoft Graph support multiple types of scheduled real-time voice and video experiences, ranging from ad hoc meetings that are suitable for a few participants to large, structured virtual events like webinars and town halls with thousands of attendees.

Use the following table to choose the right meeting type and Microsoft Graph APIs for your use case.

| Teams meeting type | Microsoft Graph APIs | Use cases |
| --- | --- | --- |
| [Online meeting](https://support.microsoft.com/office/meetings-in-microsoft-teams-e0b0ae21-53ee-4462-a50d-ca9b9e217b67) | [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting)  <br>[attendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport)  <br>[attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord)  <br>[online meeting webhooks](https://learn.microsoft.com/en-us/graph/changenotifications-for-onlinemeeting) | - Hosting a meeting for up to 1,000 participants who can be inside or outside of your organization. Everyone can interact via audio, video, chat, and screen sharing.<br>- Meetings are either scheduled, ad hoc, or channel meetings. |
| [Webinar](https://support.microsoft.com/office/get-started-with-microsoft-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3) | [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar)  <br>[virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration)  <br>[virtualEventWebinarRegistrationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinarregistrationconfiguration)  <br>[virtualEventRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase)  <br>[meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport)  <br>[attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord)  <br>[virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession)  <br>[virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter)  <br>[virtual event webhooks](https://learn.microsoft.com/en-us/graph/changenotifications-for-virtualevent) | - Hosting a meeting where one or several experts \(presenters\) share their ideas or provide training to an audience \(attendees inside or outside of your organization\) with a maximum of 1,000 participants on the call.<br>- Registration is needed before attendees can join the webinar. |
| [Town hall](https://support.microsoft.com/office/get-started-with-town-hall-in-microsoft-teams-33baf0c6-0283-4c15-9617-3013e8d4804f) | [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall)  <br>[virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession)  <br>[virtualEventPresenter](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenter) | - Automatic streaming event for a limited number of presenters to a large group of attendees, capping at 10,000 or 20,000 participants \(with Teams Premium\).<br>- Attendees cannot register for the event. They need to be invited. Attendees use the Q&A feature to engage with presenters and organizers instead of directly interacting via chat or audio. |

To learn more about the differences between each meeting type to choose the one that is best suited for your use case, see the [feature comparison chart](https://learn.microsoft.com/en-us/microsoftteams/meeting-webinar-town-hall-feature-comparison).

## Related content

- [Use online meeting APIs](https://learn.microsoft.com/en-us/graph/cloud-communications-online-meetings)
- [Create solutions with webinar APIs](https://learn.microsoft.com/en-us/graph/cloud-communications-virtual-events-webinar-usecases)
- [Create solutions with town hall APIs](https://learn.microsoft.com/en-us/graph/cloud-communications-virtual-events-townhall-usecases)
- [Use virtual event change notifications](https://learn.microsoft.com/en-us/graph/changenotifications-for-virtualevent)
