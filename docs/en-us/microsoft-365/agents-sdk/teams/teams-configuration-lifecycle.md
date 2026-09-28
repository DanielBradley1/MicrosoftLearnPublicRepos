<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-configuration-lifecycle -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Handle Microsoft Teams lifecycle events

## Channels

Handle channel lifecycle events within a team.

```csharp
[TeamsChannelCreatedRoute]
public async Task OnChannelCreatedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.TeamsChannel channel, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync($"Channel created: {channel.Name}", cancellationToken: cancellationToken);
}

[TeamsChannelRenamedRoute]
public async Task OnChannelRenamedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.TeamsChannel channel, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync($"Channel renamed to: {channel.Name}", cancellationToken: cancellationToken);
}

[TeamsChannelDeletedRoute]
public Task OnChannelDeletedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.TeamsChannel channel, CancellationToken cancellationToken)
    => Task.CompletedTask;
```

Available route attributes:

| Attribute | Event |
| --- | --- |
| `TeamsChannelUpdateRoute` | Any channel event |
| `TeamsChannelCreatedRoute` | Channel created |
| `TeamsChannelDeletedRoute` | Channel deleted |
| `TeamsChannelRenamedRoute` | Channel renamed |
| `TeamsChannelSharedRoute` | Channel shared with another team |
| `TeamsChannelUnsharedRoute` | Channel unshared |
| `TeamsChannelRestoredRoute` | Channel restored |
| `TeamsChannelMemberAddedRoute` | Member added to channel |
| `TeamsChannelMemberRemovedRoute` | Member removed from channel |

```javascript
teams.channels
  .onCreated(async (context, state, channel) => {
    await context.sendActivity(`Channel created: ${channel.name}`)
  })
  .onRenamed(async (context, state, channel) => {
    await context.sendActivity(`Channel renamed to: ${channel.name}`)
  })
  .onDeleted(async (context, state, channel) => {
    console.log(`Channel deleted: ${channel.id}`)
  })
  .onRestored(async (context, state, channel) => {
    console.log(`Channel restored: ${channel.name}`)
  })
  .onShared(async (context, state, channel) => {
    console.log(`Channel shared: ${channel.name}`)
  })
  .onUnshared(async (context, state, channel) => {
    console.log(`Channel unshared: ${channel.name}`)
  })
  .onMemberAdded(async (context, state, channel) => {
    console.log('Member added to channel')
  })
  .onMemberRemoved(async (context, state, channel) => {
    console.log('Member removed from channel')
  })
```

To handle any channel event with a single handler, use `onChannelEventReceived`.

Each channel handler receives a `ChannelData` object. The affected channel is on `data.channel`.

```python
from microsoft_teams.api.models import ChannelData

@teams.channels.created
async def on_channel_created(context, state, data: ChannelData):
    await context.send_activity(f"Channel created: {data.channel.name}")

@teams.channels.renamed
async def on_channel_renamed(context, state, data: ChannelData):
    await context.send_activity(f"Channel renamed to: {data.channel.name}")

@teams.channels.deleted
async def on_channel_deleted(context, state, data: ChannelData):
    print(f"Channel deleted: {data.channel.id}")
```

Other channel events are available as `restored`, `shared`, `unshared`, `members_added`, and `members_removed`. To handle any channel event with a single handler, use `@teams.channels.event`.

## Team events

Handle team-level lifecycle events such as archiving or renaming.

```csharp
[TeamsTeamArchivedRoute]
public async Task OnTeamArchivedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.Team team, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync($"Team archived: {team.Name}", cancellationToken: cancellationToken);
}

[TeamsTeamRenamedRoute]
public async Task OnTeamRenamedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.Team team, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync($"Team renamed to: {team.Name}", cancellationToken: cancellationToken);
}

[TeamsTeamUnarchivedRoute]
public Task OnTeamUnarchivedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.Team team, CancellationToken cancellationToken)
    => Task.CompletedTask;

[TeamsTeamDeletedRoute]
public Task OnTeamDeletedAsync(
    ITeamsTurnContext turnContext, ITurnState turnState,
    Microsoft.Teams.Apps.Schema.Team team, CancellationToken cancellationToken)
    => Task.CompletedTask;
```

Available route attributes:

| Attribute | Event |
| --- | --- |
| `TeamsTeamUpdateRoute` | Any team event |
| `TeamsTeamArchivedRoute` | Team archived |
| `TeamsTeamUnarchivedRoute` | Team unarchived |
| `TeamsTeamRenamedRoute` | Team renamed |
| `TeamsTeamRestoredRoute` | Team restored |
| `TeamsTeamDeletedRoute` | Team soft-deleted |

```javascript
teams.teams
  .onArchived(async (context, state, team) => {
    await context.sendActivity(`Team archived: ${team.name}`)
  })
  .onUnarchived(async (context, state, team) => {
    console.log(`Team unarchived: ${team.name}`)
  })
  .onRenamed(async (context, state, team) => {
    await context.sendActivity(`Team renamed to: ${team.name}`)
  })
  .onRestored(async (context, state, team) => {
    console.log(`Team restored: ${team.name}`)
  })
  .onDeleted(async (context, state, team) => {
    console.log(`Team deleted: ${team.id}`)
  })
```

To handle any team event with a single handler, use `onTeamEventReceived`.

Each team handler receives a `ChannelData`; the affected team is on `data.team`:

```python
from microsoft_teams.api.models import ChannelData

@teams.teams.archived
async def on_team_archived(context, state, data: ChannelData):
    await context.send_activity(f"Team archived: {data.team.name}")

@teams.teams.renamed
async def on_team_renamed(context, state, data: ChannelData):
    await context.send_activity(f"Team renamed to: {data.team.name}")

@teams.teams.deleted
async def on_team_deleted(context, state, data: ChannelData):
    print(f"Team deleted: {data.team.id}")
```

Other team events are available as `unarchived` and `restored`. To handle any team event with a single handler, use `@teams.teams.event`.

## Get team details and channels

The Teams API client provides operations for retrieving a team and its channels.

```csharp
var api = turnContext.Client;
var teamId = turnContext.Activity.TeamsGetTeamInfo()?.Id;

var team = await api.Teams.GetByIdAsync(
    teamId!,
    cancellationToken);

var channels = await api.Teams.GetConversationsAsync(
    teamId!,
    cancellationToken);

foreach (var channel in channels)
{
    Console.WriteLine($"{channel.Name}: {channel.Id}");
}
```

```javascript
import { teamsGetTeamInfo } from '@microsoft/agents-hosting-extensions-msteams'

const api = context.client
const teamId = teamsGetTeamInfo(context.activity)?.id

const team = await api.teams.getById(teamId)
const channels = await api.teams.getConversations(teamId)

for (const channel of channels) {
  console.log(`${channel.name}: ${channel.id}`)
}
```

```python
api = context.api_client
team_id = context.activity.get_team_info().id

team = await api.teams.get_by_id(team_id)
channels = await api.teams.get_conversations(team_id)

for channel in channels:
    print(f"{channel.name}: {channel.id}")
```

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Handle meeting events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings)
- [Access conversation members](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-context)
- [Use Adaptive Cards in agents](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards)
