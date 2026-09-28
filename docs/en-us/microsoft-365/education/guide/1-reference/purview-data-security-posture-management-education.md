<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/purview-data-security-posture-management-education -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Microsoft Purview DSPM Sensitive Information Policy Deployment Guide for Education

This guide provides a school-district–appropriate deployment approach for using Microsoft Purview Data Security Posture Management \(DSPM\) with Microsoft Purview Data Loss Prevention \(DLP\) to reduce the risk that Microsoft Copilot and prebuilt agents process or surface sensitive information. The recommended pattern is to enable DSPM setup tasks and auditing, identify relevant sensitive information types \(SITs\) and sensitivity labels, and then create DLP policies that either block sensitive prompts, block external web search when prompts contain sensitive data, or exclude labeled files and emails from Copilot processing.

## Overview and purpose

School districts increasingly want the productivity benefits of Microsoft Copilot and agents, but the same grounding data that powers those experiences can also increase exposure to oversharing, data loss, and insider-risk scenarios if it's not governed.

- Central IT: turn on DSPM setup tasks, validate audit and analytics, and create tenant-wide policies that prevent Copilot and prebuilt agents from processing sensitive prompts or sensitive labeled content.
- School IT: review simulation results, DLP activity, and DSPM recommendations before enforcing policies broadly.
- Teachers: continue using approved Copilot experiences, but prompts that contain configured sensitive information types can be blocked, and files or emails with selected sensitivity labels can be excluded from response generation.

## Architecture overview

This solution follows a centralized governance model because the documented controls are configured in Microsoft Purview and apply at the tenant scope for the Microsoft Copilot and Copilot Chat policy location. DSPM surfaces posture insights and setup tasks, while DLP provides the enforceable policy controls.

| **Level** | **Role** | **Capability** |
| --- | --- | --- |
| District Tenant | Central IT / Purview Admin | Enable DSPM setup tasks, confirm auditing, manage tenant-wide AI data security controls. |
| Security and Compliance Operations | DLP / Information Protection / Insider Risk admins | Define SITs and labels, create DLP rules for Copilot, review activity explorer and policy outcomes. |
| End-User Productivity Layer | Staff using Microsoft Copilot and prebuilt agents | Use approved Copilot experiences subject to policy restrictions for prompts, web search, and labeled content. |

Note

**Key Principle:** This is an IT-administered deployment. The documented DLP location for Microsoft Copilot and Copilot Chat doesn't support Administrative Units, so policy administration should remain centrally governed rather than delegated to school-level teachers or office staff. *Direct reference: /purview/dlp-microsoft365-copilot-location-learn-about*

## Prerequisites

| **Requirement** | **Details** |
| --- | --- |
| Licensing | Supporting license for Microsoft Purview Data Security Posture Management is required, and users of Microsoft Copilot and agents require a Microsoft Copilot license. Exact education SKU for the tenant is TBD and should be validated against current Microsoft licensing guidance. |
| Required roles | Examples include Microsoft Entra AI Admin, Purview Data Security AI Admin, Purview Compliance Administrator, Purview Information Protection Admin, Purview Security Administrator, or Microsoft Entra Global Admin. Use least privilege. |
| Foundational data controls | Identify built-in and custom Sensitive Information Types \(SITs\), configure a sensitivity labeling schema, and define an Insider Risk Management program. |
| Admin portals | Primary portal: [https://purview.microsoft.com](https://purview.microsoft.com). DSPM setup tasks are surfaced from DSPM > Actions > Setup tasks. DLP policies are created from Data Loss Prevention > Policies. |
| Audit / analytics | Confirm Microsoft Purview Audit is enabled and review DSPM setup tasks before enabling enforcement. |
| Browser / device prerequisites | Required only if the district extends protections to non-Microsoft AI apps. In those cases, onboarding devices to Microsoft Purview and installing the Purview browser extension might be required. |
| Printing / physical distribution | Not applicable for this IT-only control set. |

## Phase 1 – Enable the Sensitive Information Protection Foundation \(Central IT\)

This is a one-time tenant-wide configuration performed by Central IT.

### Phase 1 - Step-by-step portal navigation

1. Sign in to Microsoft Purview at [https://purview.microsoft.com](https://purview.microsoft.com) with an appropriately privileged admin account.
2. Open DSPM and go to **Actions** > **Setup tasks**.
3. Confirm **Activate Microsoft Purview Audit** is complete.
4. Review setup tasks that are relevant to the district AI governance program, including **Protect your data with sensitivity labels**, **Secure interactions from enterprise AI apps**, and **Secure interactions in Microsoft Copilot experiences**.
5. Validate the district’s SITs, sensitivity labels, and Insider Risk Management foundation so DSPM has the context it needs to generate actionable recommendations.

| **Setting** | **Recommended Value \(Education\)** | **Reason** |
| --- | --- | --- |
| Microsoft Purview Audit | Enabled / validated | Audit provides the visibility foundation for agent and Copilot interaction monitoring. |
| Sensitive information types \(SITs\) | Identify built-in SITs first; add custom SITs for district-specific patterns as needed | Built-in SITs are a strong starting point and custom SITs fill district-specific gaps. |
| Sensitivity labeling schema | Implement before broad Copilot rollout | Labels are extremely helpful for DSPM recommendations and later DLP protection. |
| Initial DSPM setup task review | Review all setup tasks under **DSPM** > **Actions** > **Setup tasks** | Setup tasks include policy-creation shortcuts and prerequisite guidance. |
| Security Copilot in DSPM | TBD / Optional | Optional for deeper investigation capabilities. |

## Phase 2 – Create the Sensitive Information Policy for Agents \(Central IT\)

This phase creates the enforceable DLP policy that protects Microsoft Copilot and prebuilt agents from processing sensitive prompts or sensitive labeled content.

### Phase 2 - Step-by-step portal navigation

1. In Microsoft Purview, go to **Data Loss Prevention > Policies**.
2. Select **+ Create policy**.
3. Choose **Custom template**, then **Custom policy**.
4. On the **Locations** page, turn on **Microsoft Copilot** and **Copilot Chat**.
5. Create separate rules for each protection pattern needed. Don't combine Sensitive information types and Sensitivity labels in the same rule.

### Protection pattern A — Block sensitive prompts

1. Add a rule.
2. Set the condition to **Content contains > Sensitive information types**.
3. Choose the relevant SITs for the district.
4. Set the action to Prevent Copilot from processing content > Processing prompts.
5. Save the rule and policy.

### Protection pattern B — Block external web search when prompts contain sensitive data

1. Add a separate rule in the same policy or a separate policy, depending on governance preference.
2. Set the condition to Content contains > Sensitive information types.
3. Choose the relevant SITs.
4. Set the action to **Prevent Copilot from processing content > Performing Web Searches**.
5. Save the rule and policy.

### Protection pattern C — Exclude labeled files and emails from Copilot processing

1. Add another rule.
2. Set the condition to **Content contains > Sensitivity labels**.
3. Select the labels the district wants excluded from Copilot processing.
4. Set the action to **Prevent Copilot from processing content**.
5. Save the rule and policy.

| **Setting** | **Recommended Value \(Education\)** | **Reason** |
| --- | --- | --- |
| Policy template | Custom policy | Required because the Microsoft Copilot and Copilot Chat location is available only in the Custom template. |
| Policy mode at first deployment | Simulation mode first | Allows the district to understand user impact and tune false positives before enforcement. |
| Prompt protection | Enable for highest-risk SITs first | Reduces friction while protecting the most sensitive scenarios first. |
| Web-search protection | Enable for SITs that should never be sent to external web services | Prevents sensitive prompts from being sent to external web search providers. |
| Labeled content exclusion | Enable for top sensitivity labels used for highly sensitive content | Excludes the most sensitive content from Copilot processing. |
| Rule design | Separate SIT and sensitivity-label rules | These conditions can't be combined in the same rule. |
| Incident reports | Turn on and add security team recipients | Helps the security team monitor attempted sensitive information sharing patterns. |

## Phase 3 – Validate and tune the policy \(Central IT / Security Operations\)

1. Confirm grounding-data sources used with agents have appropriate sensitivity labels applied in SharePoint and, where applicable, Microsoft Dataverse.
2. Open a Microsoft Copilot interaction that references labeled content and confirm the conversation displays the most restrictive label from the referenced content.
3. Review DLP activity explorer to understand which files, emails, or prompts are affected before enforcement.
4. If the district uses the default Copilot DLP policy as a starting point, review it carefully because it begins in simulation mode and only logs the event until switched to enforcement.
5. Refine the set of SITs, users, or groups if simulation results show excessive false positives.

Tip

Use [DSPM data-risk assessments](https://learn.microsoft.com/en-us/purview/data-security-posture-management-oversharing) in parallel with DLP tuning. These assessments help identify oversharing in SharePoint and OneDrive, and those insights surface under the objective Prevent oversharing of sensitive data.

## Phase 4 – Operate the policy \(daily IT or security workflow\)

Because this policy set is IT-controlled, the day-to-day workflow involves operational review rather than teacher-issued actions.

1. Review DSPM recommendations, posture summaries, and setup-task state from the Microsoft Purview portal.
2. Review DLP activity explorer for affected prompts, files, and emails.
3. Review Insider Risk Management policy outcomes if the Risky AI usage template is enabled.
4. Adjust SIT or sensitivity-label scope only after reviewing evidence from simulation, alerts, or activity trends.

Note

**Best Practice:** Microsoft recommends least privilege for administrators and starting Copilot DLP controls in simulation mode so schools can understand operational impact before user-facing enforcement. Learn more about the [default data loss prevention policy for Microsoft Copilot location](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-default-policy) and [using Microsoft Purview Data Loss Prevention to protect interactions with Microsoft Copilot and Copilot Chat](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about).

## Phase 5 – End-user experience

### Web experience

- If a prompt contains a configured Sensitive Information Type, Microsoft Copilot can block the prompt from being processed, and the user sees a message that the request can't be completed because it contains sensitive information that the organization blocked Copilot from using.
- If the district chooses the web-search restriction action instead, Copilot can continue generating a response by using allowed internal Microsoft 365 data, while external web search is blocked as a grounding source for that prompt.
- If a file or email carries a configured sensitivity label, the item can still appear in citations, but the content of that item isn't processed or used in the Copilot response summary.

### App experience

- These protections are documented for Microsoft Copilot, Copilot Chat, and Copilot experiences in Word, Excel, and PowerPoint.
- If a file is open in Word, Excel, or PowerPoint and has a sensitivity label covered by a DLP policy that prevents Copilot processing, the Copilot skills in those apps are disabled. If the label is applied mid-session, enforcement begins the next time the file is opened.

## Phase 6 – Automation \(Optional\)

Microsoft documentation retrieved for this task references automation options, but it doesn't provide a complete, ready-to-run code example for creating the exact Copilot DLP policy used in this guide. The exact rule syntax and parameters required for this scenario are therefore marked TBD.

- Policy as code / change control: use PowerShell or approved automation to standardize DLP rule creation after validating the exact syntax from current Microsoft documentation. TBD: exact command examples for this deployment.
- Reporting automation: TBD: exact API or reporting approach for exporting DSPM recommendations and DLP activity relevant to Copilot prompt blocking in the tenant.

TBD: Add approved PowerShell or API examples after validating current Microsoft Learn syntax for:

- New-DlpComplianceRule
- Copilot DLP rule creation / modification
- Incident report configuration
- Scheduled export of DLP activity / DSPM posture data

## Security best practices

| **Practice** | **Recommendation** |
| --- | --- |
| Start in simulation mode | Begin with simulation mode to understand user impact and tune false positives before enforcement. |
| Use least privilege for admins | Assign the least-privileged role required to create and manage these policies; avoid overuse of Global Administrator. |
| Separate rule logic | Keep SIT-based prompt and web-search rules separate from sensitivity-label exclusion rules. |
| Review DLP activity regularly | Use DLP activity explorer to identify false positives, validate which items are being restricted, and confirm expected behavior before broad enforcement. |
| Maintain labeling hygiene | Apply and maintain a district labeling schema so Copilot exclusions can align to actual content sensitivity. |
| Monitor oversharing | Use DSPM data-risk assessments to identify overshared content in SharePoint and OneDrive before it becomes grounding data for Copilot and agents. |
| Review risky AI usage | If enabled, review Insider Risk Management detections for risky AI interaction patterns. |
| Handle updates carefully | DLP policy updates can take up to four hours to reflect in Microsoft Copilot and Copilot Chat, so plan communications and validation accordingly. |

## Role responsibility matrix

Because this control set is IT-administered, Teacher \(Scoped\) and Student don't perform configuration tasks in this design.

| **Task** | **Student** | **Teacher \(Scoped\)** | **School IT** | **Central IT** |
| --- | --- | --- | --- | --- |
| Enable DSPM setup tasks | ❌ | ❌ | ✅ | ✅ |
| Validate audit / analytics | ❌ | ❌ | ✅ | ✅ |
| Define SITs / sensitivity labels | ❌ | ❌ | ✅ | ✅ |
| Create Copilot DLP policy | ❌ | ❌ | ✅ | ✅ |
| Review simulation / DLP activity | ❌ | ❌ | ✅ | ✅ |
| Enforce production policy changes | ❌ | ❌ | ❌ | ✅ |
| Use Copilot subject to policy | ✅ | ✅ | ✅ | ✅ |

## Known limitations and considerations

- The Microsoft Copilot and Copilot Chat DLP policy location is available only in the Custom policy template.
- When you select that location, all other locations for that policy are disabled.
- Sensitive information types and Sensitivity labels cannot be used in the same rule; separate rules are required.
- DLP policy updates can take up to four hours to reflect in Microsoft Copilot and Copilot Chat.
- The policy location doesn't support Administrative Units.
- DLP doesn't scan the content of files uploaded directly into prompts; it checks only the text typed into the prompt itself.
- Sensitivity-label exclusion support for email covers emails sent on or after January 1, 2025; calendar invites aren't supported.
- Some capabilities in the retrieved materials are marked preview, including prompt blocking and external email controls. Validate production readiness in the tenant before broad enforcement.
- Detailed step-by-step policy behavior for other custom or third-party agents is TBD from the retrieved source set and requires validation against current product-specific Microsoft Learn pages.

## Recommended migration timeline

| **Timeline** | **Milestone** |
| --- | --- |
| Week 0–1 | Confirm licensing, validate admin roles, confirm audit, and review DSPM setup tasks. |
| Week 1–2 | Validate district SITs, review sensitivity label taxonomy, and identify the first set of high-risk labels and SITs for Copilot protection. |
| Week 2–3 | Create the Copilot DLP policy in simulation mode and enable incident reports to the security team. |
| Week 3–4 | Review simulation results, DLP activity, and DSPM oversharing insights; tune rules and scope. |
| Week 4+ | Move the policy to enforcement for validated SITs and labels, then continue regular operational review. |
| District-specific calendar | TBD: align pilot, teacher communication, summer change windows, and full rollout to the local district training and governance calendar. |

## Reference Links

- [Secure and govern Microsoft Copilot agents](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-deployment)
- [Step 2: Protect sensitive info in grounding data](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-step2)
- [Step 3: Protect interactions](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-sc-agents-step3)
- [Learn about using Microsoft Purview Data Loss Prevention to protect interactions with Microsoft Copilot and Copilot Chat](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about)
- [Learn about the default data loss prevention policy for Microsoft Copilot location](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-default-policy)
- [Setup tasks for Data Security Posture Management](https://learn.microsoft.com/en-us/purview/data-security-posture-management-setup)
- [Deploy and use Data Security Posture Management](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-intro)
- [Step 1: Establish foundational elements](https://learn.microsoft.com/en-us/purview/deploymentmodels/depmod-dspm-step1)
- [Learn about Data Security Posture Management](https://learn.microsoft.com/en-us/purview/data-security-posture-management-learn-about)
- [Considerations for Microsoft Purview Data Security Posture Management](https://learn.microsoft.com/en-us/purview/data-security-posture-management-considerations)
- [Prevent oversharing with data risk assessments from Data Security Posture Management](https://learn.microsoft.com/en-us/purview/data-security-posture-management-oversharing)
- [Use Microsoft Purview to manage data security and compliance for AI agents](https://learn.microsoft.com/en-us/purview/ai-agents)
- [Microsoft Purview data security and compliance protections for generative AI apps](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview)
- [Configure Data Security Posture Management \(DSPM\) for AI for custom AI apps](https://learn.microsoft.com/en-us/purview/developer/configurepurview)
