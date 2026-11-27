<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/protect-ai-agents-from-trusted-identity-attacks -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Protect AI agents from trusted-identity attacks \(preview\)

Important

This feature is currently in public preview. The Microsoft Defender preview terms apply to features that are in public preview.

Microsoft Defender helps security teams detect and disrupt identity-compromise patterns that attackers use to weaponize trusted agent workflows. This article explains the device-code phishing scenario targeting GitHub Copilot CLI and how to investigate and disrupt it in Microsoft Defender.

## Overview

AI agents introduce a new way for attackers to turn identity compromise into autonomous action.

A compromised identity can drive a trusted agent to perform malicious actions with legitimate authority. Identity is the attack path through which an agent can be weaponized. To investigate and disrupt these attacks, defenders need end-to-end visibility into where the attacker entered, which agent was involved, what identity the agent operated under, which identities or credentials it exercised, and what downstream resources were affected. Our goal is to protect customers from attackers weaponizing trusted agents to turn identity compromise into downstream resource abuse.

Microsoft Defender addresses this objective by focusing first on the earliest and most actionable entry point in this attack chain: compromise of the identity invoking the agent.

This article focuses on the device code phishing scenario against GitHub Copilot CLI and shows how Defender detects and disrupts this identity-compromise pattern before it expands into downstream resource abuse.

## Prerequisites

To enable these detections and response workflows, make sure all of the following prerequisites are met:

- You have a Microsoft 365 E5 license, are onboarded to Microsoft Defender for Office 365, and have the Microsoft Defender for Cloud Apps connector for Microsoft 365 connected. For setup guidance, see [Protect Microsoft 365 in Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-office-365).
- Safe Links protection is enabled for the relevant users and workloads \(email and Microsoft Teams\) with **Track user clicks** enabled. For configuration guidance, see [Set up Safe Links policies in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/safe-links-policies-configure).
- You have Microsoft Defender for Cloud Apps GitHub connector connected at enterprise level. For setup guidance, see [Protect your GitHub Enterprise environment](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-github).
- Microsoft Defender can detect this scenario only for GitHub enterprises using **GitHub Enterprise Managed Users \(EMU\)**, because the telemetry required for this detection is currently available only for EMU users.
- Disruption for now works only for GitHub Enterprise Managed Users \(EMU\) federated with Microsoft Entra ID.

## Attack scenario: Device code phishing against GitHub Copilot CLI

This scenario shows how an attacker can abuse a trusted authorization flow to weaponize a compromised identity path in an AI-assisted workflow.

### How the attack works

![Diagram of a device code phishing flow showing request code, send lure, user approves, token issued to attacker, and attacker action with granted OAuth permissions.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/protect-ai-agents-from-trusted-identity-attacks/device-code-phishing-flow.png)

A user approves a legitimate GitHub device-code request that was initiated by the attacker-controlled client. Conceptual illustration.

1. **Initiate:** The attacker starts a Copilot CLI device-code sign-in request.
2. **Lure:** The attacker sends the short code and GitHub verification link to the user, for example under the pretext of an IT request or a Copilot license check. The verification page is genuinely hosted by GitHub; the legitimate domain alone does not establish who initiated the request.
3. **Approve:** The user opens the GitHub page, signs in if needed, and approves the request. This is the social engineering step.
4. **Sign in:** After approval, the attacker-controlled client completes the sign-in automatically.
5. **Operate:** The attacker can act within the permissions granted to the application and the resources available to the affected account.

### Impact

If successful, this attack can enable **memory poisoning**, abuse of **cloud-synced sessions from past interactions**, unauthorized **repository access**, and malicious actions performed through the compromised trusted agent workflow. Because activity appears to come from a legitimate identity and approved flow, impact can spread quickly unless the compromise is detected and disrupted early.

## Detections

Microsoft Defender currently provides the following detections for this scenario:

| Alert title | MITRE ATT&CK technique | Severity |
| --- | --- | --- |
| **Suspected GitHub Copilot CLI device code phishing via email** | **Initial Access \(T1566.002\), Credential Access \(T1528\)** | High |
| **Suspected GitHub Copilot CLI device code phishing via Microsoft Teams** | **Initial Access \(T1566.002\), Credential Access \(T1528\)** | High |

### Alert description

A user may have been phished into completing GitHub device authorization. Defender observed related OAuth token activity consistent with GitHub Copilot CLI device-code phishing. The impacted account may be a GitHub EMU account.

### Determine whether the alert is True Positive or False Positive

- **True Positive:** If you can confirm the user didn't intentionally initiate the GitHub Copilot CLI device authorization request, or related GitHub OAuth activity is suspicious or unauthorized.

  **Recommended action:** Verify the automatic disruption action. If disruption failed or didn't occur, manually suspend or disable the affected GitHub EMU account.
- **False Positive:** If after investigation, you can confirm the user intentionally initiated the request and the activity matches expected business use.

  **Recommended action:** Dismiss the alert.

### Understand the scope of the breach

- Review related GitHub OAuth authorization/token activity in the alert time window.
- Review all identities and sessions associated with the potentially impacted GitHub EMU account.
- Review whether the same lure indicators were used against additional users.

## SOC experience in Microsoft Defender

The following view shows how SOC can further investigate this issue using the incident graph. Open the alert to review what happened and the recommended actions.

[![Screenshot of the SOC investigation experience for GitHub Copilot CLI device code phishing.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/protect-ai-agents-from-trusted-identity-attacks/security-operations-center-investigation-github-copilot-cli-device-code-phishing.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/protect-ai-agents-from-trusted-identity-attacks/security-operations-center-investigation-github-copilot-cli-device-code-phishing.png#lightbox)

## Disruption

For this scenario, Microsoft Defender XDR automatically takes disruption action when the alert is raised by disabling the affected GitHub Enterprise Managed User \(EMU\). This action suspends the affected managed identity through the organization's identity provider, interrupting attacker access.
