<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/siem-defender-create-automation-rules -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Create automation rules with ISOC in Microsoft Defender \(preview\)

Use automation rules with Integrated Security Operations Center \(ISOC\) in Microsoft Defender to trigger automated response actions. Automation rules help standardize response workflows, reduce repetitive work, and run supported actions when alert or incident conditions are met.

Note

This feature is in preview. Capabilities and availability might change during the preview period.

## Prerequisites

Before you begin, make sure the following requirements are met:

- Your tenant is [eligible for ISOC](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview).
- You have the **Automation Rules** Unified RBAC permission with **Read** and **Write** access.
- If the automation rule runs a playbook, you have the **Automation Playbooks** Unified RBAC permission with **Read** and **Write** access.
- To run automation on third-party data ingested through Log Analytics, you have a [Microsoft Sentinel workspace](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard).

## Create an enhanced automation rule

Use an enhanced automation rule to run supported actions when alerts or cases match the conditions you define.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Automation**.
3. Select **Create** > **Automation rule**.
4. Select **Enhanced rule**.

   ![Screenshot showing the option to create an enhanced automation rule.](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-create-automation-rules/create-enhanced-automation-rule.png)
5. In **Name**, enter a name for the rule.
6. Select a **Trigger**.

   ![Screenshot showing trigger options for an enhanced automation rule.](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-create-automation-rules/enhanced-automation-rule-trigger-options.png)

   The trigger determines which fields, conditions, and actions are available for the rule.

   | Trigger | Use when | Rule behavior |
   | --- | --- | --- |
   | **When alert is created** | You want the rule to run when a supported alert is created. | Select the workspaces and Sentinel scope for the rule. Add conditions if needed, and then select a generated playbook to run. |
   | **When case is created** | You want the rule to run when a case is created. | Configure the required **Case type** condition, and then select a supported case action. |
   | **When case is updated** | You want the rule to run when a case is updated. | Configure the required **Case type** condition, and then select a supported case update action. |

7. Configure the trigger settings.

   - For **When alert is created**: Select the **Workspaces** where the rule applies. Under **Sentinel Scope**, select **All available and future Sentinel scopes** or **Specific scoped data**.
   - For **When case is created**: Configure the required **Case type** condition.
   - For **When case is updated**: Configure the required **Case type** condition.

8. Configure the conditions for the selected trigger.

   - For **When alert is created**: You can leave conditions empty or select **Add** to define conditions.
   - For **When case is created** or **When case is updated**: Use the required **Case type** condition to define which case types the rule applies to. If needed, select **Add subgroup** to add more condition logic.

9. Select an action.

   ![Screenshot showing action options for an enhanced automation rule.](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-create-automation-rules/enhanced-automation-rule-action-options.png)

   The available actions depend on the selected trigger.

   - For **When alert is created**: Select **Run generated playbook**, and then select the playbook to run.
   - For **When case is created**: Select an action such as **Send case created email**, **Update case**, or **Create case tasks**.
   - For **When case is updated**: Select a supported case update action, such as **Send case updated email**.

10. If the selected action requires more information, fill in the required fields.
11. If needed, configure **Expiration**.
12. Configure **Status**.

    Select **Active** to enable the rule after creation.
13. Select **Create**.

## Create a standard automation rule

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Automation**.
3. Select **Create** > **Automation rule**.
4. Select **Standard rule**.

   ![Screenshot showing the option to create a standard automation rule.](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-create-automation-rules/create-standard-automation-rule.png)
5. In **Name**, enter a name for the rule.
6. Select a **Trigger**.

   ![Screenshot showing trigger options for a standard automation rule.](https://learn.microsoft.com/en-us/defender-xdr/media/siem-defender-create-automation-rules/standard-automation-rule-trigger-options.png)

   The trigger determines which conditions are available for the rule.

   | Trigger | Use when | Condition behavior |
   | --- | --- | --- |
   | **When incident is created** | You want the rule to run when a new incident is created. | Conditions are optional. Add conditions only when you need to scope the rule. |
   | **When incident is updated** | You want the rule to run when an existing incident changes. | At least one state-change condition is required. Supported properties include **Status**, **Severity**, **Owner**, **Tactics**, **Tag**, **Alerts**, and **Comments**. |

7. Select a **Workspace**.
8. Configure the conditions for the selected trigger.

   - For **When incident is created**: You can leave conditions empty or select **Add** to define conditions.
   - For **When incident is updated**: Select one of the supported state-change properties, such as **Status**, **Severity**, **Owner**, **Tactics**, **Tag**, **Alerts**, or **Comments**.

9. Add one or more actions.

   Available actions include:

   - **Run Logic Apps playbook**
   - **Change status**
   - **Change severity**
   - **Assign owner**
   - **Add tags**
   - **Add task**

10. If needed, configure **Expiration**.
11. If needed, configure **Order**.
12. Select **Create**.

## Edit an existing automation rule

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Automation**.
3. Select the **Automation rules** tab.
4. Select the automation rule you want to update.
5. Update the rule settings, conditions, or actions.
6. Select **Apply**.

## Duplicate an automation rule

Duplicate an existing automation rule to create one or more copies that you can configure separately.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com/).
2. Go to **Automation**.
3. Select the **Automation rules** tab.
4. Select the automation rule you want to duplicate.
5. Select **Duplicate**.
6. In **Number of copies \(1-10\)**, enter the number of copies to create.
7. To create the copies in an inactive state, select **Create copies as inactive**.
8. Select **Duplicate**.

The duplicated rules appear in the automation rules list.

## Review automation rule behavior

After you create, edit, or duplicate an automation rule, review that the rule behaves as expected.

1. Trigger or wait for an alert or incident that matches the rule conditions.
2. Open the related alert or incident.
3. Review the activity details to confirm whether the automation rule ran.
4. If the rule didn't run, review the trigger, conditions, permissions, and workspace requirements.

## Related content

- [Automation with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-automation)
- [Generate playbooks using AI with ISOC](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-generate-playbooks)
- [Automation integrations with ISOC in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-automation-integrations)
