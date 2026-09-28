<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Handle Microsoft Teams meeting events

Register handlers for meeting start and end events and for participants joining or leaving. Each handler receives typed meeting data.

Note

Meeting start and end events require the Resource-Specific Consent \(RSC\) permission `OnlineMeeting.ReadBasic.Chat` in your app manifest.

```csharp
[TeamsMeetingStartRoute]
public async Task OnMeetingStartAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    Microsoft.Teams.Apps.Clients.MeetingDetails meeting,
    CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(
        $"Meeting started: {meeting.Id}",
        cancellationToken: cancellationToken);
}

[TeamsMeetingEndRoute]
public async Task OnMeetingEndAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    Microsoft.Teams.Apps.Clients.MeetingDetails meeting,
    CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(
        $"Meeting ended: {meeting.Id}",
        cancellationToken: cancellationToken);
}

[TeamsMeetingParticipantsJoinRoute]
public Task OnParticipantsJoinAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    Microsoft.Teams.Apps.Meetings.MeetingParticipantJoinValue details,
    CancellationToken cancellationToken)
{
    // details.Members contains the joining participants.
    return Task.CompletedTask;
}

[TeamsMeetingParticipantsLeaveRoute]
public Task OnParticipantsLeaveAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    Microsoft.Teams.Apps.Meetings.MeetingParticipantLeaveValue details,
    CancellationToken cancellationToken)
{
    // details.Members contains the leaving participants.
    return Task.CompletedTask;
}
```

```javascript
teams.meetings
  .onStart(async (context, state, details) => {
    await context.sendActivity(`Meeting started: ${details.id}`)
  })
  .onEnd(async (context, state, details) => {
    await context.sendActivity(`Meeting ended: ${details.id}`)
  })
  .onParticipantsJoin(async (context, state, details) => {
    for (const member of details.members) {
      console.log(`${member.user.name} joined (role: ${member.meeting.role})`)
    }
  })
  .onParticipantsLeave(async (context, state, details) => {
    // details.members contains the leaving participants.
  })
```

```python
from microsoft_teams.api.models import MeetingDetails
from microsoft_agents.activity.teams import MeetingParticipantsEventDetails

@teams.meetings.start
async def on_meeting_start(context, state, meeting: MeetingDetails):
    await context.send_activity(f"Meeting started: {meeting.id}")

@teams.meetings.end
async def on_meeting_end(context, state, meeting: MeetingDetails):
    await context.send_activity(f"Meeting ended: {meeting.id}")

@teams.meetings.participants_join
async def on_participants_join(context, state, details: MeetingParticipantsEventDetails):
    for member in details.members or []:
        print(f"{member.user.name} joined (role: {member.meeting.role})")

@teams.meetings.participants_leave
async def on_participants_leave(context, state, details: MeetingParticipantsEventDetails):
    # details.members contains the leaving participants.
    ...
```

## Get meeting and participant details

The Teams API client provides operations for retrieving a meeting or one of its participants.

```csharp
var api = turnContext.Client;
var meetingId = turnContext.Activity.TeamsGetMeetingInfo()?.Id;

var meeting = await api.Meetings.GetByIdAsync(
    meetingId!,
    cancellationToken);

var participant = await api.Meetings.GetParticipantAsync(
    meetingId!,
    turnContext.Activity.From.AadObjectId,
    turnContext.Activity.Conversation.TenantId,
    cancellationToken);
```

```javascript
import { teamsGetMeetingInfo } from '@microsoft/agents-hosting-extensions-msteams'

const api = context.client
const meetingId = teamsGetMeetingInfo(context.activity)?.id

const meeting = await api.meetings.getById(meetingId)
const participant = await api.meetings.getParticipant(
  meetingId,
  context.activity.from?.aadObjectId,
  context.activity.conversation?.tenantId
)
```

```python
api = context.api_client
meeting_id = context.activity.get_meeting_info().id

meeting = await api.meetings.get_by_id(meeting_id)
participant = await api.meetings.get_participant(
    meeting_id,
    context.activity.from_property.aad_object_id,
    context.activity.conversation.tenant_id,
)
```

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Handle Teams messages](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-messages)
- [Collect feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback)
- [Access conversation members](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-context)
