<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-evaluations -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Agent evaluations for the Employee Self-Service declarative agent

Use the [Employee Self-Service Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview) \(ADK\) to generate, validate, review, publish, run, and inspect evaluation test sets for your Employee Self-Service declarative agent. You stay in ADK while Copilot Studio provides the test-set and evaluation services in the background.

Start by describing the evaluation task in natural language in GitHub Copilot Chat. You can also use the `/evaluate` command to start the evaluation workflow directly. For the general ADK workflow, see [What you can do now with the Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-what-you-can-do-now) and the [Agent Developer Kit commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference).

This article describes the more detailed declarative agent workflow first. If you're evaluating an Employee Self-Service custom engine agent, see [Evaluate a custom agent with ADK](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/evaluations) for the complete custom engine agent workflow.

For general evaluation concepts, including test cases, assertions, quality signals, graders, and grounding data, see [Agent evaluation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview). This article focuses on the Employee Self-Service workflow.

## Choose the right evaluation approach

The Agent Developer Kit and Copilot Studio evaluator provide two ways to work with Employee Self-Service evaluations.

| Approach | Use it when | What it provides |
| --- | --- | --- |
| **Agent Developer Kit** | You want an ADK-guided declarative agent evaluation workflow. | Generate from configured Topics or a planned scenario, validate test-set quality, request reviewer comments, publish, run, and return results in ADK. Copilot Studio provides the backend evaluation services. |
| **Copilot Studio evaluator** | You want to manage and run the evaluation directly in Copilot Studio instead of using the ADK-guided workflow. | The evaluation capabilities documented in [About agent evaluation in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-agent-evaluation-intro). |

You can use either approach. If you're new to evaluations or aren't sure which test cases or scenarios to include, start with ADK. ADK uses your configured Topics or a planned scenario to generate a starting test set that you can review and refine before running it. If you already know what you want to test and prefer to manage the full test set directly, use the Copilot Studio evaluator.

## Prerequisites

Before you begin:

- Complete an Agent Developer Kit installation path from [Customize your Employee Self-Service agent with the Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview).
- Run the initial setup command so the kit is connected to your Power Platform environment and has a local copy of the Employee Self-Service agent.
- Open the `ess-maker-skills` workspace in Visual Studio Code and use GitHub Copilot Chat, as described in the [Agent Developer Kit commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference).
- Decide which scenarios you want to test your agent against, such as HR, compensation, or IT support scenarios.
- If a scenario isn't configured yet, describe the scenario or goal that you plan to add so ADK can generate a planning test set before you implement it.
- Sign in to ADK with a work account that can edit the target agent in its Power Platform environment. Publishing and running test sets use that account's Power Platform and Copilot Studio access.
- Before running an evaluation, confirm that the environment has a connected Microsoft Copilot Studio connection and that any connections required by the agent's Tools or actions are available.
- Identify the authoritative HR and IT policies, approved test data, and user profiles required by the scenarios.
- Remove or replace personal, customer, production, or sensitive information before using it in an evaluation dataset.
- Complete the knowledge-source, connector, permission, and content setup required by the scenarios you plan to evaluate.

Note

Existing ADK guidance recommends `/flightcheck` before publishing or when you troubleshoot an environment or integration issue. It isn't part of the standard evaluation sequence. If your evaluation uses integrations, you can run `/flightcheck` to identify broader environment, identity, or integration issues, but still confirm the connections required by the evaluation run.

## Generate test cases in ADK

In GitHub Copilot Chat, describe the evaluation set that you want to generate. For example:

```text
Generate a new eval set for HR scenarios (compensation).
```

ADK recognizes the evaluation request and starts the generation workflow. If your request doesn't identify the scenario or goal, ADK asks for it.

You can also enter `/evaluate` to start the evaluation workflow directly.

ADK can generate the test set from:

- The declarative agent's current Topic configuration. You can scope generation to a full evaluation, a specific area, or a specific test category.
- A planned scenario that you want to add to the declarative agent, even if the scenario isn't configured yet.

For a planned scenario, the generated set helps you define the expected behavior before implementation. Treat the cases as planning drafts until the required Topic, knowledge, Tool or action, workflow, or integrations are configured. They should identify the source or configuration the scenario needs rather than invent an organization-specific answer.

Review the generated cases to confirm that they cover the employee requests, expected behavior, and important boundary conditions for the scenario.

## Validate the quality of the generated test set

ADK automatically validates the generated prompts and expected responses before the test set is pushed. It reports an overall quality-gate result and findings in areas such as assertion quality, diversity, and redundancy. Findings can be required or optional and non-blocking.

This validation evaluates the quality of the **test cases**, not the quality of your agent's responses. The full evaluation run tests the agent later from ADK, with Copilot Studio processing it in the background.

If the quality gate doesn't pass, fix the required findings before you continue. If it passes with optional notes, review the notes and decide whether the cases need changes. After you edit a test case, ADK reruns validation and reports whether the set still passes and whether the change introduced new findings.

A passing quality gate doesn't push the test set. The set remains local until you ask ADK to push it to Copilot Studio.

## Review the generated cases

Once validation of the test set is complete, continue to review the test set. Treat generated cases as a starting point. Review every case before you publish and run the test set.

### Check coverage

Confirm that the generated set covers the scenario you requested, including critical success paths and boundary or negative cases when applicable. You can add, delete, or edit test cases by describing the change in GitHub Copilot Chat. For example:

```text
Add a test case about compensation ratio.
```

### Check the prompt

- Does it represent one clear employee intent?
- Is the wording realistic for your employee population?
- Does the case need role, region, employment type, supported language, permissions, or another user context?
- If the prompt is ambiguous, does the expected behavior require a clarifying question rather than an answer?

### Check the expected response

Define the intended outcome, not one polished sentence, unless exact wording is required.

An intent-focused expected response should identify:

- Required policy facts or task outcome
- Expected architecture-specific component, such as a Topic, workflow, Tool or action, connector, instruction, or knowledge source
- User details that affect the expected response, such as role, region, employment type, or permissions
- Required next step, when applicable
- Required clarification, refusal, or escalation
- Information or actions that must not appear

For example:

> **Prompt:** "Can my contractor request parental leave?"  
> **Expected response:** Applies the approved eligibility policy for contractors in the user's region; doesn't assume eligibility; directs the user to the approved HR path when eligibility can't be determined from available context.

## Request reviewer comments

Automated quality validation and reviewer comments are separate stages:

- **Automated quality validation** checks whether the test set is well constructed.
- **Human review** lets a subject-matter expert or other accountable reviewer confirm that the prompts, expected responses, policy requirements, and escalation behavior are appropriate for your organization.

The reviewer needs access to the same Power Platform environment and permission to pull and push the shared test set.

Use this workflow:

1. **Maker:** Ask ADK to mark the test set as ready for review and push it to Copilot Studio. For example:

   ```text
   Mark the Compensation test set as ready for review and push it to Copilot Studio.
   ```

2. **Reviewer:** Open ADK and ask to pull the test sets that are ready for review. For example:

   ```text
   Pull the test sets that are ready for review.
   ```

3. **Reviewer:** Select the test set, review the prompts and expected responses, and enter comments in natural language. For example:

   ```text
   The expected response for the annual bonus case should explain that eligibility depends on the employee's role and region.
   ```


   ADK saves the comments in the test-set description.

4. **Reviewer:** Ask ADK to mark the review complete and push the test set back to Copilot Studio. For example:

   ```text
   Mark the Compensation test-set review as complete and push it to Copilot Studio.
   ```


   This action saves the comments and updated review state.

5. **Maker or agent owner:** Open ADK and ask to pull the test sets that have been reviewed. For example:

   ```text
   Pull the test sets that have been reviewed.
   ```

6. **Maker:** Review the comments, decide whether to add, delete, or edit test cases, and rerun automated quality validation when the test cases change.

Human review is advisory, not an approval gate. In this workflow, the reviewer provides comments, while the maker retains responsibility for official test-case edits and evaluation execution.

## Publish and run the test set from ADK

After the test set passes the reviews required by your organization, use ADK to publish it and start the evaluation. Copilot Studio stores the published test set and runs the evaluation in the background, but you remain in ADK.

1. Ask ADK to push the reviewed test set. For example:

   ```text
   Push the Compensation test set.
   ```

2. Select the intended test set if ADK presents more than one option.
3. Review the selected test set and confirm the push action.
4. Ask ADK to run the pushed test set. For example:

   ```text
   Run the Compensation test set.
   ```

5. Ask ADK for the run status while Copilot Studio processes the evaluation.
6. Review the returned results in ADK when the run completes.

## Review the evaluation results

When the run finishes, ADK returns:

- The run state, start and end times, and total number of test cases.
- A completion summary with the number of passed and failed cases and the overall pass rate.
- A verdict that compares the pass rate with the reporting target.
- A summary by scenario group.
- Detailed evidence for the individual test cases.

### Mock result summary

The following example is illustrative. Your results depend on the test set and environment.

```text
Compensation scenarios - run completed

State: Completed
Total cases: 6
Completion summary: 5 passed / 1 failed - 83.3% pass rate
Verdict: Below the 95% reporting target
```

| Scenario group | Cases | Passed | Failed | Pass rate |
| --- | ---: | ---: | ---: | ---: |
| Compensation scenarios | 6 | 5 | 1 | 83.3% |

Start with the completion summary, then review the detailed evidence for each failed case. Compare the prompt, expected response, returned response, and any grader result or reason that ADK provides.

ADK returns the evaluation evidence but doesn't establish the root cause of a failed case. Review the evidence before you decide what to change. For more details, you can view the full run results in the Copilot Studio **Evaluate** tab.

### Account for declarative-agent response synthesis

Microsoft 365 Copilot can synthesize the final response to answer the employee's question more directly and leave out details that aren't needed. If a test fails because the wording differs, determine whether the response still answers the employee's question and includes all information required by the test.

If the response is valid, update the expected response or evaluation method so the semantically correct response passes. Avoid exact-match assertions for prose unless exact wording is a requirement.

For general guidance about assertions and graders, see [Write assertions](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-write-assertions).

## Rerun and maintain regression coverage

1. Rerun the failed or affected cases after a change.
2. Run the full test set before publishing the updated agent.
3. Compare the new results with the previous run.
4. Keep fixed defects as regression cases.
5. Add representative cases for reproducible employee-reported problems.
6. Rerun relevant test sets when you change knowledge, instructions, Topics, actions, workflows, connections, or supported user context.

## Limitations and troubleshooting

- ADK doesn't precheck a specific Power Platform or Dataverse security role before publishing or running a test set. Power Platform and Copilot Studio enforce the signed-in account's access when ADK makes the request.
- A run requires a connected Microsoft Copilot Studio connection in the environment. Scenarios that use Tools or actions also require the applicable connections.
- Push and run are separate operations. A successful push doesn't mean that the evaluation ran.
- Evaluation doesn't replace security testing, Responsible AI review, content moderation, user research, or performance testing. See [What evaluation doesn't replace](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview#what-evaluation-doesnt-replace).
- If ADK doesn't recognize your evaluation request, or if `/evaluate` doesn't respond as expected, confirm that the workspace root is `ess-maker-skills`, use a recommended model, and try again. See [Agent Developer Kit commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference#where-commands-look-for-instructions) and [Troubleshoot getting started](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/troubleshoot-getting-started).

## Related content

- [What you can do now with the Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-what-you-can-do-now)
- [Agent Developer Kit commands reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference)
- [Agent evaluation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview)
- [About agent evaluation in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-agent-evaluation-intro)
