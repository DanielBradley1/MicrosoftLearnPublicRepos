<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-tuning-document-summary-template -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Copilot Tuning Document Summary agent template \(early access preview\)

The **Document Summary** agent template helps you generate summaries that reflect your organization's voice, priorities, and quality standards. By using Copilot Tuning, you can configure the agent to adapt summaries to specific audiences, purposes, tones, and lengths without rewriting prompts every time.

This capability is useful for scenarios such as executive briefings, legal and compliance reviews, education, healthcare documentation, internal communications, and business development. By standardizing how teams produce summaries, they can save time, improve decision-making, and deliver consistent results.

Important

Microsoft Copilot Tuning is currently available to a limited set of customers through early access programs. Access through [Frontier](https://adoption.microsoft.com/copilot/frontier-program/) is planned for April 2026. Features and requirements are subject to change.

## What the agent can do

By using the Document Summary agent template, you can:

- Generate summaries from supported files based on instructions you provide for tone, audience, purpose, length, and focus areas.
- Create specialized summarization agents by tuning goals and context.
- Further fine-tune the agent by using your organization's own data to improve relevance, consistency, and summary quality for your scenario.

[![Screenshot that shows the agent can generate summaries, create summarization agents, and fine-tune based on organizational data.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/what-agent-can-do.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/what-agent-can-do.png#lightbox)

When you enable fine-tuning, the agent can:

- Learn what information is most important based on high-quality examples.
- Apply your summarization goals and rubrics consistently across documents.

[![Screenshot that shows the agent can learn what's important and apply goals and rubrics.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/what-agent-can-do-2.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/what-agent-can-do-2.png#lightbox)

## Supported inputs and outputs

The agent supports the following inputs and outputs:

- **Supported file types**: Word \(.docx\) and PDF \(.pdf\)
- **Input scope**: Single files or folders containing multiple files
- **Outputs**:

  - A summary generated in the Copilot conversation
  - A draft summary document delivered by email

[![Screenshot that shows supported file types, input scopes, and outputs.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/inputs-and-outputs.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/inputs-and-outputs.png#lightbox)

## Use the agent for inference

Before you fine-tune the agent, test it by running inference with sample prompts. Prompts must reference one or more input files.

**Example prompt**:

Summarize the key profit drivers and growth areas based on EarningsStatement2024.docx and EarningsStatement2025.docx.

### Supported prompt patterns

The Document Summary agent template supports single file and multiple file prompt patterns.

- **Single file:** Summarize the key highlights and lowlights for a leadership review based on ProjectStatus.docx.
- **Multiple files:** Summarize project risks based on TeamA\_Status.docx, TeamB\_Status.docx, and TeamC\_Status.docx.

[![Screenshot that shows supported prompt patterns are single file and multiple files.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/supported-prompt-patterns.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/copilot-tuning-document-summary-template/supported-prompt-patterns.png#lightbox)

## Why tune?

Different teams need summaries that optimize for different outcomes. For example, executives might want concise decision-ready briefs, legal teams might want precise risk-focused summaries, and project managers might want action-oriented recaps. Tuning helps the agent learn which details matter most for your scenario and apply those priorities consistently.

You can tune agents in two stages. Choose the appropriate stage based on your scenario:

- **Tune Context:** Define persistent goals, rubrics, and expectations for summarization without model training.
- **Tune Model:** Further improve relevance and consistency by using your organization's data.

Tunable agents support goal-based evaluations, so you can measure success using metrics aligned to your organization's summarization priorities rather than generic quality scores.

## Prerequisites

Document Summary uses a goals- and rubric-based training approach. Unlike other tuning recipes, you don't need to provide ideal output examples upfront.

Before you begin context tuning, prepare the following items:

1. **Clear goals** that describe what a high-quality summary should look like.
2. **Context inputs** such as purpose, audience, length, tone, and focus sections.
3. **Sample input files** that represent the documents you want summarized.
4. A process to review and refine clarifying questions and evaluation metrics.

Note

This recipe uses reasoning-based fine-tuning. During tuning, the model learns to reason over input content by using your goals, clarifying questions, evaluation metrics, and representative examples as rubrics for quality.

## Context tuning

By using context tuning, you can set the default behavior for the agent, regardless of the runtime prompt.

### Define goals and tasks

Start by defining your summarization goals. These goals describe the agent's role, priorities, and quality expectations.

The following example shows a goal:

- You're an expert project manager at Contoso. Create purpose-driven, audience-appropriate summaries for busy readers who care about key risks and mitigations.

You can optionally include **guidelines** to act as rubrics, such as:

- Follow all user instructions.
- Honor the stated purpose of the summary.
- Adapt content to the specified audience.
- Match the requested tone \(for example, neutral or legal\).
- Respect approximate length requirements.
- Include or exclude sections as specified.
- Reflect the full intent of the user's instructions.

### Select business categories

Specify one or more business categories or industries \(for example, Project Management, Legal, or HR\). These categories help the system better interpret your goals and context.

### Upload sample input files

Upload one or more files that represent typical inputs for this agent. The system uses these files to simulate evaluations during tuning. You don't need to provide sample summaries at this stage.

### Review clarifying questions

The system generates clarifying questions based on your goals and inputs. Review and edit these questions to ensure they align with the task you want the agent to perform.

### Review metrics

Review the metrics used to evaluate the agent's performance. The system generates a benchmark using your sample inputs and estimates output quality.

Add, remove, or edit metrics to better reflect your real-world success criteria.

### Finalize context tuning

After the evaluations complete, you receive an email notification. If the metrics meet your expectations, you can publish the agent or proceed to model tuning to further improve results.

## Tune Model

Tune Model is the most advanced customization option for the Document Summary agent template. It fine-tunes the underlying model by using your organization's data so the agent can better learn what information to prioritize, how to adapt summaries to your audience and purpose, and how to apply your summarization rubrics more consistently across documents.

Use Tune Model when:

- You need more consistent summarization quality across complex or high-stakes documents.
- Your scenario depends on nuanced prioritization that Tune Context alone doesn't reliably achieve.
- You want the agent to learn from representative high-quality summary outcomes for your organization.
- You have sufficient high-quality training data for your scenario.

### Required data

To use Tune Model, prepare a folder that contains at least 20 high-quality example output files, each at least one page long, that represent ideal summaries for your scenario.

- Select a folder rather than individual files.
- Supported file types include Word \(.docx\) and PDF \(.pdf\).
- Using a larger and more representative dataset typically improves model-tuning results.
- Use examples that reflect the same audiences, purposes, tones, and document types you expect at runtime.

### What a model-tuned agent can do

A model-tuned agent can:

- Generate summaries that more consistently reflect your organization's priorities and rubrics.
- Improve relevance by learning which details matter most across representative examples.
- Better adapt summaries for common audience and purpose combinations used by your teams.
- Provide a reusable tuned summarization experience that you can share across the organization.

### Use Tune Model with a Document Summary agent

To use Tune Model with a Document Summary agent:

1. **Tune agent:** Choose **Tune agent** in the specialized Document Summary agent that you created from the Document Summary agent template, and then go to the **Tune Model** option.
2. **Provide preferred outputs:** Select a folder that contains at least 20 high-quality ideal summary outputs, each at least 1 page long, that represents the type of summarization quality you want the agent to learn.
3. **Review access:** Choose one or more Microsoft Entra security groups or restrict access to yourself, based on who should be allowed to use the fine-tuned agent.
4. **Start fine-tuning:** Follow the in-product instructions to start fine-tuning. The tuning process runs asynchronously while you continue to use the existing agent.
5. **Review evaluation metrics and decide to publish:** After fine-tuning completes, review the updated evaluation metrics, compare results with the previous stage, and publish the tuned model if the results meet your expectations.

Note

Complete Tune Context first so your goals, clarifying questions, and evaluation metrics are already defined before you start model tuning.

### Use a model-tuned agent

To use a model-tuned agent:

- Chat with your tuned agent and provide one or more supported input files.
- You don't need to restate the same summarization priorities in every prompt because the tuned model already reflects the behavior learned during training.
- The agent can still follow runtime instructions, but its default behavior is shaped by the trained summarization patterns and evaluation goals.
- You can review evaluation results and publish the tuned model when it is ready for broader use.

### Limitations of model-tuned agents

Model-tuned agents have the following limitations:

- You can't select individual files for model tuning; provide a folder instead.
- Model-tuned agents depend on the quality and representativeness of the examples you provide.
- Only Word and PDF file types are supported.
- You should review evaluation results before publishing a tuned model for broad use.

## Evaluating tunable agents

At each tuning stage, you can evaluate the agent with customized criteria based on your organization's expectations for summarization quality.

- **Goals:** Define the agent's summarization task and priorities.
- **Sample files:** Provide representative input documents for evaluation.
- **Clarifying questions:** Review and refine the generated questions that shape evaluation scenarios.
- **Metrics:** Add, remove, or edit the evaluation criteria used to measure quality.
- **Evaluation results:** Review scores and insights to decide whether the agent is ready to publish or needs more refinement.

## Related content

- [Copilot Tuning overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-tuning-overview)
