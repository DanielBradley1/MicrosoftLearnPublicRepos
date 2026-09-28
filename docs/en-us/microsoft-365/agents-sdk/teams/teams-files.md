<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-files -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Handle files and file consent in Microsoft Teams

## Receive files

Files you send to an agent arrive as attachments on a message activity. How you download and expose the files to a route handler depends on the SDK language.

Register the built-in downloaders during startup. `AddAgentM365AttachmentDownloader` handles authenticated Microsoft 365 and Teams attachment URLs:

```csharp
builder.AddAgentDefaults()
    .AddAgentAttachmentDownloader()
    .AddAgentM365AttachmentDownloader()
    .AddAgent<MyAgent>();
```

Before `AgentApplication` invokes a route, each configured `IInputFileDownloader` downloads matching attachments and adds the resulting `InputFile` objects to `turnState.Temp.InputFiles`. Read the downloaded content from turn state instead of downloading `Activity.Attachments` yourself:

```csharp
[TeamsMessageRoute]
public Task OnMessageAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    CancellationToken cancellationToken)
{
    foreach (var file in turnState.Temp.InputFiles)
    {
        var filename = file.Filename;
        var contentType = file.ContentType;
        var content = file.Content.ToArray();

        // Process or persist the downloaded content.
    }

    return Task.CompletedTask;
}
```

```javascript
app.onMessage(async (context, state) => {
  for (const attachment of context.activity.attachments ?? []) {
    const downloadUrl = attachment.contentUrl
    const contentType = attachment.contentType

    // Securely download and store the file before the URL expires.
  }
})
```

```python
@AGENT_APP.activity("message")
async def on_message(context, state):
    for attachment in context.activity.attachments or []:
        download_url = attachment.content_url
        content_type = attachment.content_type

        # Securely download and store the file before the URL expires.
```

## File consent

When your agent requests permission to upload a file to a user's OneDrive, Teams shows a consent card. Register handlers for the user accepting or declining.

File consent works only in personal chats. In the `manifest.json` file in your Microsoft 365 app package, locate the object in the `bots` array whose `botId` is your agent's Microsoft app ID. Include the `personal` scope and set `supportsFiles` to `true` on that same bot object:

```json
{
  "bots": [
    {
      "botId": "{{BOT_ID}}",
      "scopes": [
        "personal"
      ],
      "supportsFiles": true
    }
  ]
}
```

After updating the manifest, rebuild and upload the app package to Teams. The `supportsFiles` setting declares support for the Teams personal-chat file APIs; it doesn't grant Microsoft Graph permissions or enable file consent in channels or group chats. To work with files in those conversation types, use Microsoft Graph with the appropriate user authorization.

```csharp
[TeamsFileConsentAcceptRoute]
public async Task OnFileConsentAcceptedAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    Microsoft.Teams.Apps.Files.FileConsentValue response,
    CancellationToken cancellationToken)
{
    var uploadUrl = response.UploadInfo?.UploadUrl;
    // Upload the file using HttpClient, then notify the user.
    await turnContext.SendActivityAsync(
        "File uploaded successfully!",
        cancellationToken: cancellationToken);
}

[TeamsFileConsentDeclineRoute]
public async Task OnFileConsentDeclinedAsync(
    ITeamsTurnContext turnContext,
    ITurnState turnState,
    Microsoft.Teams.Apps.Files.FileConsentValue response,
    CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(
        "File upload was declined.",
        cancellationToken: cancellationToken);
}
```

```javascript
teams.fileConsent
  .onAccept(async (context, state, response) => {
    const uploadUrl = response.uploadInfo?.uploadUrl
    // Upload the file using an HTTP client, then notify the user.
    await context.sendActivity('File uploaded successfully!')
  })
  .onDecline(async (context, state, response) => {
    await context.sendActivity('File upload was declined.')
  })
```

```python
from microsoft_teams.api.models import FileConsentCardResponse

@teams.file_consent.accept
async def on_file_consent_accepted(context, state, file_consent: FileConsentCardResponse):
    upload_url = file_consent.upload_info.upload_url if file_consent.upload_info else None
    # Upload the file using an HTTP client, then notify the user.
    await context.send_activity("File uploaded successfully!")

@teams.file_consent.decline
async def on_file_consent_declined(context, state, file_consent: FileConsentCardResponse):
    await context.send_activity("File upload was declined.")
```

The Teams API client doesn't provide file upload or download operations. In .NET, use `turnState.Temp.InputFiles` for downloaded inbound files. Use the upload URL from the file consent response or Microsoft Graph for uploads.

For the complete send and receive flow, including incoming file attachments, upload URLs, and Microsoft Graph options, see [Send and receive files in Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/bots/how-to/bots-filesv4).

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Use task modules](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-task-modules)
- [Collect feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback)
- [Add OAuth user authorization](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-oauth-configuration)
