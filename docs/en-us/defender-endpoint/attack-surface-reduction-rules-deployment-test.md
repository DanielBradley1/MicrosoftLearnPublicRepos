<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-test -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Test your attack surface reduction \(ASR\) rules deployment

This article is part of the [Attack surface reduction rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment).

Testing attack surface reduction \(ASR\) rules is a critical step in your deployment. You need to determine if any ASR rules will block your line-of-business apps. By starting with a small, controlled group, you can limit potential work disruptions as you expand the deployment across your organization.

Note

Before you begin the testing phase of your ASR rules deployment, disable any related ASR rules that are currently enabled in **Block** or **Warn** mode \(if applicable\). For information about using the report to find enabled ASR rules, see [Attack surface reduction rules reports](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report).

As illustrated in the following diagram, begin your ASR rules deployment with ring 1 \(the initial small pilot group of devices used for testing\).

> [![Diagram of the ASR rules testing steps: audit rules, review data, and configure exclusions.](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-testing-steps.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-testing-steps.png#lightbox)

## Assess and evaluate rules before deployment

If you have Defender for Endpoint Plan 2 \(which includes advanced vulnerability management and hunting capabilities\), [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) surfaces ASR rule–related security recommendations that can provide high-level impact indicators \(for example, whether audit activity was observed across devices\).

In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Exposure management** > **Recommendations** \(or directly to the **Security recommendations** page at [https://security.microsoft.com/exposure-recommendations](https://security.microsoft.com/exposure-recommendations)\). On the **Security recommendations** page, select an ASR rule to open the details flyout, and then select the **Devices** tab. The **User impact** value shows the percentage of devices that can accept a new policy enabling the rule in block mode without adversely affecting productivity.

[![Screenshot of the Devices tab of an ASR rule security recommendation showing user impact.](https://learn.microsoft.com/en-us/defender-endpoint/media/asrrecommendation.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/asrrecommendation.png#lightbox)

Note

To accurately assess the potential effect of an ASR rule before enabling it in **Block** or **Warn** mode, you must review **Audit** mode data and detailed reporting, such as the [Attack surface reduction rule report](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report) or [Advanced hunting data](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor#asr-rule-events-in-advanced-hunting).

## Step 1: Test all ASR rules in Audit mode

Note

As described in [ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#asr-rules), you can typically enable the standard protection rules in **Block** or **Warn** mode without testing.

Typically, enable all ASR rules in **Audit** mode at the same time so you can determine which rules are triggered by everyday business activities. Start with your ASR rule champions or devices in ring 1.

ASR rules in **Audit** mode don't affect users. But the rules generate logged events that you can evaluate.

If your organization has Microsoft Intune \(included in subscriptions like Microsoft 365 E5 or available as an add-on\), use the **Attack surface reduction** endpoint security policy in Intune to configure and distribute ASR rules in **Audit** mode. For instructions, see [Configure ASR rules and exclusions in Intune using endpoint security policies](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-exclusions-in-intune-using-endpoint-security-policies).

If you don't have Intune, other ASR rule deployment methods are available:

- [Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-global-asr-rule-exclusions-in-microsoft-configuration-manager)
- [Any MDM solution using the Policy CSP](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-in-any-mdm-solution-using-the-policy-csp)
- [Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-in-group-policy)
- [PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-in-powershell)

Tip

The deployment method you use for ASR rules doesn't affect reporting data, as long as the devices are enrolled in Defender for Endpoint.

## Step 2: Review ASR rule data and assess impact

After ASR rules are deployed in **Audit** mode, review the triggered events to assess their effects and identify potential exclusions. The reporting methods available to you depend on your product and plan: the ASR rules report and device timeline require Defender for Endpoint Plan 2 or Microsoft Defender for Business, Advanced hunting requires Defender for Endpoint Plan 2, and Windows Event Viewer is available with any plan. Use one or more of the following methods:

In Defender for Endpoint Plan 2 or Microsoft Defender for Business, use the **Attack surface reduction rules report** in the Microsoft Defender portal. For complete information, see [Attack surface reduction \(ASR\) rules report](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report).

In Defender for Endpoint Plan 2, use Advanced hunting to find ASR rule events. For more information, see [ASR rule events in Advanced Hunting](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-monitor#asr-rule-events-in-advanced-hunting).

In Defender for Endpoint Plan 2 or Defender for Business, use the Defender for Endpoint device timeline. For more information, see [Microsoft Defender for Endpoint device timeline](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines#investigate-device-timeline).

Otherwise, ASR rule events are available only in Windows Event Viewer on the local device. But you can use [Windows Event Forwarding](https://learn.microsoft.com/en-us/windows/security/operating-system-security/device-management/use-windows-event-forwarding-to-assist-in-intrusion-detection) to centralize the ASR rule data collection.

Specifically, look for **Event ID 1122** in the **Applications and Services Logs** > **Microsoft** > **Windows** > **Windows Defender** > **Operational** log \(events for rules in **Audit** mode\). For a complete list of ASR rule event IDs and detailed steps, see [View attack surface reduction events in Windows Event Viewer](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-windows-events#browse-attack-surface-reduction-events-in-windows-event-viewer).

## Step 3: Configure ASR rule exclusions

After you review ASR rule data from **Audit** mode, you might find that some ASR rules block legitimate business apps or activity \(known as *false positives*\). You can add exclusions to prevent ASR rules from evaluating the affected files or folders.

For an overview of supported exclusion types for ASR rules, see [File and folder exclusions for ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#file-and-folder-exclusions-for-asr-rules).

If you used an **Attack surface reduction** endpoint security policy in Microsoft Intune to deploy the ASR rules, use the same policy to configure ASR rule exclusions. For instructions, see [Configure ASR rules and exclusions in Intune using endpoint security policies](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-exclusions-in-intune-using-endpoint-security-policies).

If you used a different method to deploy the ASR rules, use the same method to configure ASR rule exclusions:

- [Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-global-asr-rule-exclusions-in-microsoft-configuration-manager)
- [Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-exclusions-in-group-policy)
- [Any MDM solution using the Policy CSP](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-global-asr-rule-exclusions-in-any-mdm-solution-using-the-policy-csp)
- [PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-global-asr-rule-exclusions-in-powershell)

Tip

Rule exclusions are better than turning off rules or switching them back to **Audit** mode. Take advantage of **Warn** mode in available rules to limit disruptions without disabling the rule entirely. For more information, see [Modes for ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#modes-for-asr-rules).

## Related content

- [Attack surface reduction \(ASR\) rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment)
- [Plan your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-plan)
- [Enable attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-implement)
- [Manage and monitor your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-operationalize)
- [Attack surface reduction \(ASR\) rules report](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-report)
- [Troubleshoot attack surface reduction rules](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-asr)
- [Attack surface reduction \(ASR\) rules reference](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference)
