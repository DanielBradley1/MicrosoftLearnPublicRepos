<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Teams extension for the Agents SDK

The **Teams extension** enables you to build agents that go beyond basic messaging in Microsoft Teams. It provides structured, event-driven access to the full range of Teams platform capabilities, including meetings, message extensions, task modules, channels, and team lifecycle events. The extension lets you create deeply integrated, interactive agent experiences without managing low-level protocol details.

## Why use the Teams extension?

Teams is a rich platform. Without the extension, your agent handles generic activities and must manually inspect raw payloads to detect Teams-specific events. The Teams extension eliminates that friction:

- **Purpose-built APIs** for each Teams feature area: Write handlers for exactly what you care about
- **Typed models** for Teams data: No manual JSON parsing or guesswork
- **Automatic routing**: Incoming activities are matched to the right handler by event type, command ID, or pattern
- **Built-in invoke handling**: Teams requires specific response shapes for interactive invocations. The extension manages those details for you.
- **Fluent and attribute-based registration**: Configure handlers in the style that fits your architecture
- **Full Teams API access**: A Teams API client is available on every turn for advanced scenarios beyond what built-in helpers cover.

## Feature areas

The Teams extension groups capabilities into submodules:

| Feature Area | Description |
| --- | --- |
| [Meetings](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings) | Meeting start and end, participants join and leave, and meeting API operations. |
| [Task modules](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-task-modules) | Modal dialogs with an Adaptive Card or webpage. |
| [Feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback) | AI citations, thumbs-up, thumbs-down, text feedback, and message reactions. |
| [Message extensions](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-message-extensions) | Search, action, and link-unfurl commands. |
| [Files and file consent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-files) | File upload consent and file handling guidance. |
| [Messages](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-messages) | Targeted messages, slash commands, formatting, and suggested actions. |
| [Channels](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-configuration-lifecycle) | Channel creation, renaming, deletion, and member events. |
| [Teams](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-configuration-lifecycle) | Team lifecycle events and team API operations. |
| [Conversation members](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-context) | Roster lookups through the Teams API client. |

Standard `AgentApplication` capabilities, such as message routing, Adaptive Cards, OAuth, proactive messaging, and AI integration, continue to work alongside the extension. When a feature has related Teams API client operations, its feature guide includes those operations.

## Set up the Teams extension

### Use the `TeamsExtension` attribute \(recommended\)

Apply `TeamsExtension` to a `partial` subclass of `AgentApplication`. A source generator adds a `Teams` property of type `TeamsAgentExtension` and registers the extension automatically.

Register handlers by decorating methods with route attributes. Each feature area has its own set of attributes, such as `TeamsMeetingStartRoute`, `TeamsQueryRoute`, and `TeamsTaskFetchRoute`.

```csharp
using Microsoft.Agents.Builder.App;
using Microsoft.Agents.Extensions.MSTeams;
using Microsoft.Agents.Extensions.MSTeams.App;
using Microsoft.Agents.Extensions.MSTeams.Meetings;

[TeamsExtension]
public partial class MyAgent(AgentApplicationOptions options) : AgentApplication(options)
{
    [TeamsMeetingStartRoute]
    public async Task OnMeetingStartAsync(
        ITeamsTurnContext turnContext,
        ITurnState turnState,
        Microsoft.Teams.Apps.Clients.MeetingDetails meeting,
        CancellationToken cancellationToken)
    {
        await turnContext.SendActivityAsync($"Meeting started: {meeting.Id}", cancellationToken: cancellationToken);
    }

    [TeamsMeetingEndRoute]
    public async Task OnMeetingEndAsync(
        ITeamsTurnContext turnContext,
        ITurnState turnState,
        Microsoft.Teams.Apps.Clients.MeetingDetails meeting,
        CancellationToken cancellationToken)
    {
        await turnContext.SendActivityAsync($"Meeting ended: {meeting.Id}", cancellationToken: cancellationToken);
    }
}
```

The handler method signatures are identical whether you register handlers via route attributes or use the `Teams` fluent methods \(for example, `Teams.Meetings.OnStart`\). You can use either style.

### Manual registration

If you can't use a `partial` class or prefer explicit control, construct a `TeamsAgentExtension` and register it by using `RegisterExtension`:

```csharp
public class MyAgent : AgentApplication
{
    public MyAgent(AgentApplicationOptions options) : base(options)
    {
        var teams = new TeamsAgentExtension(this);
        RegisterExtension(teams);

        teams.Meetings.OnStart(OnMeetingStartAsync);
    }
}
```

Create a `TeamsAgentExtension` instance and register it with your `AgentApplication`. Register handlers inside the `registerExtension` callback:

```javascript
import { AgentApplication, MemoryStorage, TurnState } from '@microsoft/agents-hosting'
import { startServer } from '@microsoft/agents-hosting-express'
import { TeamsAgentExtension } from '@microsoft/agents-hosting-extensions-msteams'

const app = new AgentApplication({ storage: new MemoryStorage() })

const teamsExt = new TeamsAgentExtension(app)

app.registerExtension(teamsExt, (teams) => {
  // Register Teams-specific handlers here
  teams.meetings.onStart(async (context, state, details) => {
    await context.sendActivity(`Meeting started: ${details.id}`)
  })
})

startServer(app)
```

All handler methods return the submodule instance for fluent chaining:

```javascript
teams.meetings
  .onStart(handleStart)
  .onEnd(handleEnd)
  .onParticipantsJoin(handleJoin)
  .onParticipantsLeave(handleLeave)
```

Construct a `TeamsAgentExtension` from your `AgentApplication`. The extension automatically wires its before-turn hook, and you register handlers by using the decorator on each feature-area property:

```python
from microsoft_agents.hosting.core import AgentApplication, MemoryStorage, TurnState
from microsoft_agents.hosting.msteams import TeamsAgentExtension
from microsoft_teams.api.models import MeetingDetails

AGENT_APP = AgentApplication[TurnState](storage=MemoryStorage())
teams = TeamsAgentExtension[TurnState](AGENT_APP)

@teams.meetings.start
async def on_meeting_start(context, state, meeting: MeetingDetails):
    await context.send_activity(f"Meeting started: {meeting.id}")

@teams.meetings.end
async def on_meeting_end(context, state, meeting: MeetingDetails):
    await context.send_activity(f"Meeting ended: {meeting.id}")
```

Every handler receives a Teams-aware `context` \(a `TeamsTurnContext`\), the turn `state`, and a typed payload. The extension exposes feature areas as properties: `message_extensions`, `task_modules`, `meetings`, `file_consent`, `channels`, and `teams`.

## Migrate an existing Bot Framework bot

For the general migration process, see [Migrate from Bot Framework SDK to the Microsoft 365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-guidance).

Important

`Microsoft.Agents.Extensions.MSTeams` doesn't support bots that derive from the Bot Framework SDK `TeamsActivityHandler`. Migrate the bot to `AgentApplication`, and then register Teams routes by using the extension's route attributes or fluent builders.

## Explore Teams extension capabilities

- [Handle meeting events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings) and retrieve meeting or participant details.
- [Open task modules](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-task-modules) with Adaptive Cards or webpages.
- [Add AI citations and collect feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback), including message reactions.
- [Build message extensions](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-message-extensions) for search, actions, link unfurling, previews, and settings.
- [Handle files and file consent](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-files).
- [Handle messages](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-messages), including targeted messages, slash commands, formatting, and suggested actions.
- [Handle lifecycle events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-configuration-lifecycle) and retrieve team or channel data.
- [Access conversation members](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-context) through the Teams API client.

## Related content

- [AgentApplication](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-application)
- [Agents SDK overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agents-sdk-overview)
- [Use Adaptive Cards in agents](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards)
- [Microsoft 365 app manifest schema reference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/?view=m365-app-1.30&preserve-view=true)
- [Use device capabilities in a Teams app](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/device-capabilities/device-capabilities-overview)
