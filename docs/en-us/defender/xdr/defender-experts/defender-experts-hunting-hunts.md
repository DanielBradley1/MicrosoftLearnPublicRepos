<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-hunts -->
<!-- Sitemap-Last-Modified: 2026-10-05 -->

# Hunts in Microsoft Defender Experts Hunting overview

**Hunts** is an experience in Microsoft Defender Experts Hunting that gives security teams a centralized view of threat hunts Microsoft experts conduct in their environment. Use Hunts to see expert threat hunting activities while they're both in progress to see what threats we're currently tracking, and after completion to review the outcome and supporting details.

Hunts provides a record of proactive hunting activity, including investigations that don't result in uncovering an undetected threat. This visibility helps you understand what Defender Experts hunted, what they found, and whether your team needs to take follow-up action.

Hunts is generally available to Defender Experts customers. Before you use Hunts, your organization must be enrolled in Defender Experts Hunting, Plan 1, or Plan 2, and your account must have at least the **Security Reader** role in Microsoft Defender role-based access control \(RBAC\).

**Applies to:**

- [Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

## Prerequisites

- Your organization must be enrolled in [Microsoft Defender Experts Hunting](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-prerequisites).
- Your account must have the **Security Reader** role in Microsoft Defender RBAC.

## View hunt activity in one place

In the Microsoft Defender portal, select **Defender Experts** > **Hunts** to view hunts conducted in your environment.

The Hunts experience distinguishes investigations that are still in progress from completed investigations. You can monitor an active investigation and return after it concludes to review the final outcome.

[![Screenshot of the Hunts page showing in-progress and completed Defender Experts investigations.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/defender-experts-hunting-hunts/hunts-list.png)](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/defender-experts-hunting-hunts/hunts-list.png#lightbox)

## Understand hunt types

Defender Experts conducts the following types of hunts:

- **Intelligence-based hunts:** Proactive investigations of emerging threats, attacker techniques, campaigns, and other intelligence-driven hypotheses.
- **Suspicious activity hunts:** Investigations that begin when Defender Experts identifies behavior in your environment that warrants deeper analysis.

## Follow a hunt from investigation to outcome

The hunt status helps you distinguish ongoing work from final conclusions.

| Status | What it means |
| --- | --- |
| **In progress** | Defender Experts is still investigating. The available information isn't a final conclusion. |
| **Completed** | The investigation has concluded. You can review the outcome and supporting details, including when the hunt didn't result in an incident. |

When a noteworthy threat is circulating, Hunts lets you see that Defender Experts is investigating it on your behalf. After the hunt is complete, review the findings to determine whether your organization needs to take action.

[![Screenshot of a completed Defender Experts hunt showing the investigation status, summary, and outcome.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/defender-experts-hunting-hunts/completed-hunt-details.png)](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/defender-experts-hunting-hunts/completed-hunt-details.png#lightbox)

## How Hunts works

Defender Experts investigates intelligence-based hypotheses and suspicious activity in your environment. Hunts shows the investigation as it progresses:

1. Defender Experts starts a hunt based on threat intelligence or suspicious behavior.
2. The hunt appears as **In progress** while the investigation continues.
3. Defender Experts completes the investigation and records the outcome.
4. You review the completed hunt and its supporting details to determine whether follow-up action is needed.

## Next steps

- [Start using Microsoft Defender Experts Hunting](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-onboarding)
- [Review the Defender Experts Hunting prerequisites](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-prerequisites)
- [Understand the Defender Experts Hunting report](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-report)
- [Collaborate with experts on demand](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-ask-experts)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
