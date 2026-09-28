<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Choose a model for Copilot Cowork

Copilot Cowork ships with many models so you can match the model to the work. Most of the time, leave the picker on **Auto** so Cowork can choose the model for your task.

**For admins**: You can turn off the Anthropic model family in the **Microsoft 365 admin center** under Copilot settings. This model control has no effect on whether a user can access Cowork. The setting is tenant-wide, so it can't be used to grant Anthropic models to a subset of users. When the Anthropic family is off, users keep working with the non-Anthropic models your organization allows. When you select **Auto**, Cowork chooses from the remaining available models.

## Where you pick a model

The default selection is **Auto**. The available model list reflects the models that your organization makes available to you.

When you choose a model, Cowork keeps that selection on the device you're using until you change it. If you switch back to **Auto**, Cowork returns to the default model selection behavior, which includes surfacing your most recent models at the top.

## When to use Auto

Use **Auto** for most work. When you select **Auto**, Cowork picks the model based on the models enabled by your organization. You don't need to choose a model before every request.

## Available models

Your available options are in the **Model** dropdown menu in the chat input box. The options can include the following models and model modes.

| Model | Description | Notes |
| --- | --- | --- |
| **Auto** | For most day-to-day work. | The default. When you select **Auto**, Cowork picks the model based on the models enabled by your organization. |
| **GPT 5.5 \(Frontier\)** | Capable model for medium effort work. | Hosted in Azure AI Foundry. |
| **GPT 5.6 Sol** | Intelligent and efficient for hard work‌. | Provided by OpenAI as a subprocessor. More information: [OpenAI as a subprocessor in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/openai-subprocessor) |
| **GPT 5.6 Terra** | Balanced effort for common tasks‌. | Provided by OpenAI as a subprocessor. More information: [OpenAI as a subprocessor in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/openai-subprocessor) |
| **GPT 6 Astra** | Latest model for tough problems. | Provided by OpenAI as a subprocessor. More information: [OpenAI as a subprocessor in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/openai-subprocessor) |
| **Opus 5** | For complex, high stakes work. | More information: [Anthropic subprocessor](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-faq#does-cowork-connect-to-external-models-for-processing) |
| **Claude Sonnet 5** | For everyday tasks and fast responses such as drafting, quick lookups, and day-to-day work. | Use when you want a shorter response cycle for common tasks. More information: [Anthropic subprocessor](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-faq#does-cowork-connect-to-external-models-for-processing) |
| **Claude Fable 5.1** | Most advanced model for ambitious work. | More information: [Anthropic subprocessor](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-faq#does-cowork-connect-to-external-models-for-processing). Learn about data retention in [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor). |

## How model choice affects responses

Changing the model can affect response speed, response depth, and output style. Some models are optimized for faster drafting, while others spend more time on reasoning and review.

Cowork shows a model badge in the conversation so you can see which model produced a response.

## Set the reasoning effort level to balance quality, speed, and cost

Not every task needs the same level of power. Reasoning effort levels give you more control over how Cowork balances quality, speed, and cost. The level you select persists across future Cowork tasks until you change it.

**Medium** is the default, which gives you a strong balance for everyday work. The default can vary across models to meet the Cowork quality bar. Select **Light** for lighter tasks. Select **High** or **Extra High** when you need deeper analysis, more complex reasoning, or a more thorough response. You can also select **Max** for your hardest work.

Reasoning effort level options are in the dropdown menu next to the [model picker](#available-models) in the chat input box. They're available in Copilot Cowork for web, Windows, and macOS.

Note

Higher reasoning effort is more thorough, but is slower and uses more credits. Usage is based on factors such as model choice, context volume, orchestration, and tools used.

## Data retention

Learn about data retention in [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

## Models hosted by Microsoft

We might deploy other AI models for Microsoft Copilot to use that are hosted and operated by Microsoft. These models are governed by the same contractual and data protection commitments already in place, including that no data leaves Microsoft. Learn more about models that can be used by Copilot in [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview).

## Related content

- [How access to Copilot Cowork is determined](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-access)
- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
- [Manage Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor)
- [Manage preview AI models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-preview-ai-models)
- [Responsible AI FAQ for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/responsible-ai/cowork-responsible-ai-faq)
