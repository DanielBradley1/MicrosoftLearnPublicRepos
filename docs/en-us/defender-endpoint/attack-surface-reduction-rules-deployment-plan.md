<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-plan -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Plan your attack surface reduction \(ASR\) rules deployment

This article is part of the [Attack surface reduction rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment).

Before you test or enable attack surface reduction \(ASR\) rules, plan your deployment. This article describes a planning methodology that you can adjust to meet your business needs.

> [![Diagram of the ASR rules planning steps: determine deployment rings, identify champions, inventory apps, and define team roles.](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-planning-steps.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/asr-rules-planning-steps.png#lightbox)

Tip

Typically, you can enable the [standard protection rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#asr-rules) in **Block** or **Warn** mode without testing. You should test other ASR rules in **Audit** mode before you switch them to **Block** or **Warn** mode. For more information, see the [ASR rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment).

## Infrastructure requirements for the deployment guide

Although there are [multiple ways to enable ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure), this deployment guide is based on an infrastructure that uses:

- Microsoft Entra ID
- Microsoft Intune
- Windows 10 and Windows 11 devices
- Microsoft Defender for Endpoint E5 or Windows E5 licenses

To take full advantage of ASR rules and reporting, use a Microsoft 365 E5, Windows E5, or Microsoft 365 A5 license. For more information, see [Minimum requirements for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements).

Note

If you're transitioning from a non-Microsoft host intrusion prevention system \(HIPS\) to Microsoft Defender Antivirus and ASR rules, run the HIPS solution alongside ASR rules until you enable rules in **Block** mode during the [implementation phase](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-implement). Contact the antivirus solution provider for exclusion recommendations.

## Step 1: Identify business units

How you select the first business unit to receive ASR rules in the [testing phase](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-test) depends on the following factors:

- Size of the business unit \(smaller is easier to manage\)
- Availability of ASR rule champions
- Distribution and usage of affected software. For example:

  - Software
  - Shared folders
  - Scripts
  - Office macros

Your business needs might clearly dictate one of the following choices:

- Include multiple business units to get a broad sampling of software, shared folders, scripts, macros, and line of business apps that ASR rules might affect.
- Limit the initial scope to a single business unit, work through all the issues in that business unit, then repeat the rollout to other business units individually.

## Step 2: Identify ASR rule champions

ASR rule champions are people in the affected business units who can help you during the preliminary testing and implementation phases. Typically, a champion has more technical skills and doesn't mind intermittent workflow outages. Champion involvement continues throughout the broader expansion of ASR rules deployment to your organization. Your ASR rule champions are the first to experience each level of the ASR rules rollout.

It's important to provide a feedback and response channel for your ASR rule champions to alert you to work disruptions and to receive ASR rules rollout communications.

## Step 3: Inventory line-of-business apps and understand the business unit processes

A full understanding of the apps and business processes in your organization is critical to a successful ASR rules deployment. It's imperative that you understand how those apps are used within the various business units in your organization.

Take inventory of the approved apps in your organization. You can use tools like the Microsoft 365 Apps admin center to help. For more information, see [Overview of inventory in the Microsoft 365 Apps admin center](https://learn.microsoft.com/en-us/microsoft-365-apps/admin-center/inventory).

Note

Some ASR rules don't work well if you frequently use unsigned, internally developed apps and scripts. It's more difficult to deploy ASR rules if you don't enforce code signing.

## Step 4: Define reporting and response ASR rules team roles and responsibilities

Clearly articulate the roles and responsibilities for monitoring and communicating ASR rule status and activity. Therefore, it's important to determine:

- Who's responsible for gathering reports.
- How and with whom reports are shared.
- How to escalate and address new threats or unwanted blocks by ASR rules.

Typical roles and responsibilities include:

- **IT admins**: Implement ASR rules and manage exclusions. Work with different business units on apps and processes. Create and share reports to stakeholders.
- **Certified security operations center \(CSOC\) analysts**: Investigate high-priority blocked processes.
- **Chief information security officer \(CISO\)**: Responsible for the overall security posture and health of the organization.

## Step 5: Define ASR rule deployment rings

For large enterprises, deploy ASR rules in *rings*. You define rings through the assessment of your business units, ASR rule champions, apps, and processes. After you successfully deploy ASR rules to the first ring, you can transition to the next ring into the testing phase, and so on. If you already defined rings for phased rollout of Windows updates, you can likely use those same rings to deploy ASR rules.

For more information about rings, see [Windows: Create a deployment plan](https://learn.microsoft.com/en-us/windows/deployment/update/create-deployment-plan).

## Related content

- [Attack surface reduction \(ASR\) rules deployment guide](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment)
- [Test your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-test)
- [Enable attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-implement)
- [Manage and monitor your attack surface reduction \(ASR\) rules deployment](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-operationalize)
- [Attack surface reduction \(ASR\) rules reference](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference)
