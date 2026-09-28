<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-task-modules -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Use task modules in Microsoft Teams

Task modules \(also called dialogs\) open a modal window in Teams. The window can show an adaptive card or load a webpage. The route value corresponds to a key in the activity payload, set by the adaptive card button's `data.task` field.

Use `[TeamsTaskFetchRoute]` to display the dialog and `[TeamsTaskSubmitRoute]` to process the submitted data:

```csharp
using Microsoft.Teams.Apps.Schema;
using Microsoft.Teams.Apps.TaskModules;
using System.Text.Json;

[TeamsExtension]
public partial class TaskModulesAgent(AgentApplicationOptions options) : AgentApplication(options)
{
    [TeamsTaskFetchRoute("simple_form")]
    public Task<TaskModuleResponse> OnSimpleFormFetchAsync(
        ITeamsTurnContext turnContext,
        ITurnState turnState,
        TaskModuleRequest request,
        CancellationToken cancellationToken)
    {
        var cardJson = """
        {
            "type": "AdaptiveCard",
            "version": "1.4",
            "body": [
                { "type": "TextBlock", "text": "Simple Form", "size": "Large", "weight": "Bolder" },
                { "type": "Input.Text", "id": "name", "label": "Name", "isRequired": true }
            ],
            "actions": [{"type": "Action.Submit", "title": "Submit", "data": {"task": "simple_form"}}]
        }
        """;

        var response = TaskModuleResponse.CreateBuilder()
            .WithType(TaskModuleResponseTypes.Continue)
            .WithCard(new TeamsAttachment
            {
                ContentType = AttachmentContentTypes.AdaptiveCard,
                Content = JsonSerializer.Deserialize<JsonElement>(cardJson)
            })
            .WithTitle("Simple Form")
            .WithHeight(TaskModuleSizes.Small)
            .WithWidth(TaskModuleSizes.Small)
            .Build()
            .Body
            ?? throw new InvalidOperationException("The task module response builder returned no body.");

        return Task.FromResult(response);
    }

    [TeamsTaskSubmitRoute("simple_form")]
    public async Task<TaskModuleResponse> OnSimpleFormSubmitAsync(
        ITeamsTurnContext turnContext,
        ITurnState turnState,
        TaskModuleRequest request,
        CancellationToken cancellationToken)
    {
        var name = request.GetDataString("name", "Unknown");
        await turnContext.SendActivityAsync($"Hi {name}!", cancellationToken: cancellationToken);
        return TaskModuleResponse.CreateBuilder()
            .WithType(TaskModuleResponseTypes.Message)
            .WithMessage("Form submitted")
            .Build()
            .Body
            ?? throw new InvalidOperationException("The task module response builder returned no body.");
    }
}
```

Chain task modules by returning another response with type `Continue` from a submit handler instead of type `Message`. Teams replaces the current dialog with the new card.

Use `onFetch` to display the dialog and `onSubmit` to process the submitted data:

```javascript
import { CardFactory } from '@microsoft/agents-hosting'

teams.taskModules
  .onFetch('simple_form', async (context, state, request) => {
    const formCard = {
      type: 'AdaptiveCard',
      version: '1.4',
      body: [
        { type: 'TextBlock', text: 'Simple Form', size: 'Large', weight: 'Bolder' },
        { type: 'Input.Text', id: 'name', label: 'Name', isRequired: true }
      ],
      actions: [{ type: 'Action.Submit', title: 'Submit', data: { task: 'simple_form' } }]
    }

    return {
      task: {
        type: 'continue',
        value: {
          title: 'Simple Form',
          height: 'small',
          width: 'small',
          card: CardFactory.adaptiveCard(formCard)
        }
      }
    }
  })
  .onSubmit('simple_form', async (context, state, request) => {
    const name = typeof request.data?.name === 'string' ? request.data.name : 'Unknown'
    await context.sendActivity(`Hi ${name}!`)
    return { task: { type: 'message', value: 'Form submitted' } }
  })
```

Chain task modules by returning a `continue` response from a submit handler instead of a `message`. Teams replaces the current dialog with the new card.

Use `fetch` to display the dialog and `submit` to process the submitted data. Both match on the `verb` carried in the adaptive card's `data`:

```python
from microsoft_teams.api.models import TaskModuleRequest, TaskModuleResponse

@teams.task_modules.fetch("simple_form")
async def on_simple_form_fetch(context, state, request: TaskModuleRequest) -> TaskModuleResponse:
    card = {
        "type": "AdaptiveCard",
        "version": "1.4",
        "body": [
            {"type": "TextBlock", "text": "Simple Form", "size": "Large", "weight": "Bolder"},
            {"type": "Input.Text", "id": "name", "label": "Name", "isRequired": True},
        ],
        "actions": [{"type": "Action.Submit", "title": "Submit", "data": {"verb": "simple_form"}}],
    }
    return TaskModuleResponse.model_validate(
        {
            "task": {
                "type": "continue",
                "value": {
                    "title": "Simple Form",
                    "height": "small",
                    "width": "small",
                    "card": {
                        "contentType": "application/vnd.microsoft.card.adaptive",
                        "content": card,
                    },
                },
            }
        }
    )

@teams.task_modules.submit("simple_form")
async def on_simple_form_submit(context, state, request: TaskModuleRequest) -> TaskModuleResponse:
    data = request.data if isinstance(request.data, dict) else {}
    name = data.get("name", "Unknown")
    await context.send_activity(f"Hi {name}!")
    return TaskModuleResponse.model_validate({"task": {"type": "message", "value": "Form submitted"}})
```

Chain task modules by returning a `continue` response from a submit handler instead of a `message`. Teams replaces the current dialog with the new card.

## Related content

- [Teams extension overview](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-extension)
- [Handle meeting events](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-meetings)
- [Collect feedback](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-feedback)
- [Use message extensions](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/teams/teams-message-extensions)
- [Use Adaptive Cards in agents](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adaptive-cards)
