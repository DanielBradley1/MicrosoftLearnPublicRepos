<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-overview -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Agent Evaluations CLI overview

The Microsoft 365 Copilot Agent Evaluations CLI \(@microsoft/m365-copilot-eval\) helps you test, measure, and improve the quality of your agents with structured evaluations and rich result reports with AI-based scoring.

Important

For deployed declarative agents, start with [Work IQ Dev Tools \(preview\)](https://microsoft.github.io/wiqd/extensions/provided/eval/) for a guided workflow. Work IQ Dev Tools manages the compatible Agent Evaluations CLI version and exposes it through `wiqd agent eval`. Use the standalone CLI guidance in this section when you need lower-level command control or maintain an existing `runevals` workflow.

## What you can do

The evaluation tool provides the following capabilities:

- Run batch and interactive evaluations.
- Automatically score responses by using Microsoft Foundry cloud evaluation and built-in metrics.
- Test using JSON datasets, inline prompts, or interactive input.
- Generate reports in HTML, JSON, or CSV formats.

## Evaluation metrics

Each response is scored using standard evaluation metrics.

| Evaluator | Type | Scale | Default Threshold | Default |
| --- | --- | --- | --- | --- |
| Relevance | LLM-based | 1-5 | 3 | Yes |
| Coherence | LLM-based | 1-5 | 3 | Yes |
| Groundedness | LLM-based | 1-5 | 3 | No |
| Similarity | LLM-based | 1-5 | 3 | No |
| RetrievalQuery | Non-LLM | Pass/fail | N/A | No |
| RetrievalResult | Non-LLM | Proportional | 1.0 | No |
| Citations | Count-based | >= 0 | 1 | No |
| ExactMatch | String match | boolean | N/A | No |
| PartialMatch | String match | 0.0-1.0 | 0.5 | No |

For detailed information about each evaluator, including configuration options and sample datasets, see [Evaluators reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-evaluators).

## How the evaluation workflow works

Evaluations follow a consistent workflow:

1. Install and configure the CLI.
2. Provide environment configuration and credentials.
3. Create a dataset of test prompts.
4. Run evaluations against your agent.
5. Review results and iterate.

## Required environment variables

The evaluation tool uses environment variables to authenticate and connect to your tenant and Microsoft Foundry project.

| Variable | Description | Default |
| --- | --- | --- |
| `TENANT_ID` | Microsoft Entra tenant ID where your agent is deployed. | None |
| `AZURE_AI_PROJECT_ENDPOINT` | Microsoft Foundry project endpoint used for cloud evaluation. | None |
| `AZURE_AI_MODEL_NAME` | Model deployment name in your Microsoft Foundry project. | `gpt-5-mini` |
| `M365_TITLE_ID` \(optional\) | Title ID used to auto-detect the Microsoft 365 agent ID for evaluation. | None |
| `M365_AGENT_ID` \(optional\) | Explicit agent ID for evaluation. | Auto-detected from `M365_TITLE_ID` |

These values enable authentication and allow the tool to run LLM-based evaluation scoring by using Microsoft Foundry. For details about how to get these values, see [Get values for environment variables](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-get-env-values).

## Related content

- [Quickstart: Use the Agent Evaluations CLI](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-quickstart)
- [Dataset schema and test design](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-create-tests)
- [Evaluators reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-evaluators)
- [CLI reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-reference)
- [Troubleshooting and support](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-troubleshooting)
