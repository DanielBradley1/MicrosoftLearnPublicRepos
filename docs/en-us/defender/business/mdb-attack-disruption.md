<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-attack-disruption -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# Automatic attack disruption in Microsoft Defender for Business

A human-operated attack is an active attack with the following goals:

- Infiltrate the organization.
- Elevate their privileges.
- Navigate the network.
- Deploy ransomware or steal information.

These types of attacks can be catastrophic to business operations. They tend to be difficult to address and sometimes continue to threaten business operations after the initial encounter. For more information, see [Human-operated ransomware attacks](https://learn.microsoft.com/en-us/security/ransomware/human-operated-ransomware#human-operated-ransomware-attacks).

Automatic attack disruption is designed to:

- Contain advanced attacks that are in progress.
- Limit the effect and progression of attacks on your devices.
- Provide more time for your security team to fully remediate an attack.

This article describes how automatic attack disruption works in Microsoft Defender for Business, how to view details about an attack, and how to get these capabilities.

## How automatic attack disruption works

Automatic attack disruption uses insights from Microsoft Security researchers and advanced AI models to counteract the complexities of advanced attacks. It limits an attacker's progress early on and dramatically reduces the overall effect of an attack, from associated costs to loss of productivity. See some examples at the [Microsoft Security Blog](https://aka.ms/ContainUserSecBlog).

By using automatic attack disruption, as soon as a human-operated attack is detected on a device, the system takes steps to contain the affected device and user accounts on the device. The system creates an incident in the Microsoft Defender portal: [https://security.microsoft.com](https://security.microsoft.com). Your IT or security team can view details about the risk and containment status of compromised assets during and after the process. An **Incident** page provides details about the attack and up-to-date status of affected assets.

Automated response actions include:

- Containing a device by blocking incoming or outgoing communication
- Containing a user account by disconnecting current user connections at the device level

Important

- To view information about a detected advanced attack, you must have an appropriate role, such as Security Reader or Security Administrator.
- To take remediation actions, release a contained device/user, or re-enable a user account, you must have the Security Administrator role.

For more information, see [Security roles and permissions in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-roles-permissions).

## View details about an attack in the Microsoft Defender portal

1. In the Microsoft Defender portal, go to **Incidents**.
2. Select an incident that's tagged with *Attack Disruption*.
3. Review the incident graph. You can get the entire attack story and assess the attack disruption effect and status.
4. When you're ready to release a contained device or user account, or re-enable a user account, take one of the following steps:

   - To release a contained device, select the device, and then select **Release from containment**.
   - To release a contained user, select the user account, and then, in the side pane, select **Undo**.

Disrupted incidents include a tag for `Attack Disruption` and the specific threat type identified, such as ransomware. If your IT or security team receives [incident email notifications](https://learn.microsoft.com/en-us/defender-business/mdb-email-notifications), these tags also appear in the emails.

When an incident is disrupted, highlighted text appears below the incident title. Contained devices or user accounts are listed with a label that indicates their status.

## Track attack disruption actions in the Action center

The [Action center](https://learn.microsoft.com/en-us/defender-business/mdb-review-remediation-actions) brings together all remediation and response actions, whether those actions were taken automatically or manually. You can view all automatic attack disruption actions in the Action center. After your IT or security team mitigates the risk and completes the investigation of an incident, they can release contained assets.

1. In the Microsoft Defender portal, go to **Actions & submissions** > **Action center**.
2. Select the **History** tab.
3. Select an action, such as **Contain user** or **Contain device**, and then choose **Undo**.

For more information, see [Review remediation actions in the Action center](https://learn.microsoft.com/en-us/defender-business/mdb-review-remediation-actions).

## How to get automatic attack disruption

Automatic attack disruption is built into Defender for Business. You don't have to explicitly turn on these capabilities. It's important to [onboard all your organization's devices](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices) \(computers, phones, and tablets\) to Defender for Business so that they're protected as soon as possible.

Additionally, sign up to receive [preview features](https://learn.microsoft.com/en-us/defender-xdr/preview) so that you get the latest and greatest capabilities as soon as they're available.

## Next step

[Respond to and mitigate threats](https://learn.microsoft.com/en-us/defender-business/mdb-respond-mitigate-threats)
