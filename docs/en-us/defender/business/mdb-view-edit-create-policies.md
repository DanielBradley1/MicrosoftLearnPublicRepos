<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies -->
<!-- Sitemap-Last-Modified: 2026-06-25 -->

# View or edit policies in Microsoft Defender for Business

In Defender for Business, you configure security settings through policies that are applied to devices. To help simplify your setup and configuration experience, Defender for Business includes several preconfigured policies. These policies help protect your company's devices as soon as you onboard them. You can also create other types of policies. For more information, see [Set up, review, and edit your security policies and settings in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings).

This article describes how to view, edit, and create security policies in Defender for Business.

This article includes:

- [A list of default policies that are included in Defender for Business](#default-policies-in-defender-for-business) \(Next-generation protection and firewall\)
- [Extra policies that you can set up in Defender for Business](#policies-to-set-up-in-defender-for-business) \(Web content filtering, controlled folder access, and attack surface reduction rules\)
- [How to view existing policies](#view-your-existing-policies)
- [How to edit an existing policy](#edit-an-existing-policy)
- [How to create a new policy](#create-a-new-policy)

## Default policies in Defender for Business

In Defender for Business, there are two main types of default policies that are designed to protect your company's devices as soon as you onboard them:

- *Next-generation protection policies* determine how Microsoft Defender Antivirus and other threat protection features are configured.

  Next-generation protection includes robust antivirus and anti-malware protection for computers and mobile devices. The default policies are designed to protect your devices and users without hindering productivity. You can customize your policies to suit your business needs. For more information, see [Review or edit your next-generation protection policies](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection).
- *Firewall policies* determine what network traffic is permitted to flow to and from your company's devices.

  Firewall policies help secure devices by establishing rules that determine what network traffic is permitted to flow to and from devices. You can use firewall protection to specify whether to allow or to block connections on devices in various locations. For example, your firewall settings can allow inbound connections on devices that are connected to your company's internal network, but prevent connections when the device is on a network with untrusted devices. For more information, see [Firewall in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-firewall).

## Policies to set up in Defender for Business

In addition to next-generation protection and firewall policies, there are three other types of policies to configure for the best protection with Defender for Business:

- [Web content filtering](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering), which enables your security team to track and regulate access to websites based on content categories. Examples of categories include adult content, high bandwidth content, and legal liability content. When you set up your web content filtering policy, you enable web protection for your organization. For more information, see [Web content filtering](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering).
- [Controlled folder access](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview) \(CFA\) allows only trusted apps to access protected folders on Windows devices. Think of this capability as ransomware mitigation. For more information, see [Deployment and configuration methods for CFA](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#deployment-and-configuration-methods-for-cfa).
- [Attack surface reduction](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview) \(ASR\) rules target software behaviors that are considered risky because attackers commonly abuse these behaviors through malware. Examples include launching executable files and scripts that attempt to download or run files. Attack surface reduction rules can constrain software-based risky behaviors and help keep your organization safe. At a minimum, we recommend configuring the [standard protection rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#asr-rules) to help protect your network without causing disruption for users. For more information, see [Deployment and configuration methods for ASR rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#deployment-and-configuration-methods-for-asr-rules).

## View your existing policies

You can view your existing policies in either [Microsoft Defender portal](https://security.microsoft.com) or the [Intune admin center](https://intune.microsoft.com) if you use Intune.

- [**Microsoft Defender portal**](#tabpanel_1_M365D)
- [**Intune admin center**](#tabpanel_1_intune)

1. Go to the [Microsoft Defender portal](https://security.microsoft.com), and sign in.
2. In the navigation pane, select **Configuration management** > **Device configuration**. Policies are organized by operating system, such as **Windows client**, and policy type, such as **Next-generation protection** and **Firewall**.
3. Select an operating system tab, for example, **Windows clients**. Review the policies under each category, such as **Next-generation protection** and **Firewall**.
4. To view more details about a policy, select its name. A side pane opens that provides more information about that policy, such as which devices are protected by that policy.

1. On the **Endpoint security \| Overview** page of the [Microsoft Intune admin center](https://intune.microsoft.com/#view/Microsoft_Intune_Workflows/SecurityManagementMenu/%7E/overview), select the policy type from the **Manage** section of the navigation pane, for example, **Antivirus**, **Firewall**, or **Attack surface reduction**.
2. You see any existing policies for the policy type you selected. To view more details about a policy, select its name.

## Edit an existing policy

You can edit your existing policies in either [Microsoft Defender portal](https://security.microsoft.com) or the [Intune admin center](https://intune.microsoft.com) if you use Intune.

- [**Microsoft Defender portal**](#tabpanel_2_M365D)
- [**Intune admin center**](#tabpanel_2_intune)

1. Go to the [Microsoft Defender portal](https://security.microsoft.com), and sign in.
2. In the navigation pane, choose **Device configuration**. You see policies organized by operating system, such as **Windows client**, and policy type, such as **Next-generation protection** and **Firewall**.
3. Select an operating system tab, for example, **Windows clients**. Review the policies under the **Next-generation protection** and **Firewall** categories.
4. To edit a policy, select its name, and then select **Edit**.
5. On the **General information** tab, review the information. If necessary, edit the description. Then select **Next**.
6. On the **Device groups** tab, determine which device groups should receive this policy.

   - To keep the selected device group as it is, select **Next**.
   - To remove a device group from the policy, select **Remove**.
   - To set up a new device group, select **Create new group**, and then set up your device group. For help with this task, see [Device groups](https://learn.microsoft.com/en-us/defender-business/mdb-create-edit-device-groups).
   - To apply the policy to another device group, select **Use existing group**.


   After you specify which device groups should receive the policy, choose **Next**.

7. On the **Configuration settings** tab, review the settings. If necessary, edit the settings for your policy. For help with this task, see:

   - [Understand next-generation configuration settings](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection)
   - [Firewall in Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-firewall)


   After you specify your next-generation protection settings, select **Next**.

8. On the **Review your policy** tab, review the general information, targeted devices, and configuration settings.

   - Make any needed changes by selecting **Edit**.
   - When you're ready to proceed, select **Update policy**.

To edit an existing endpoint security policy, such as **Antivirus**, **Firewall**, or **Attack surface reduction**, in the Intune admin center, see [Modify existing policies](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#modify-existing-policies). This link opens in a new tab in the Intune documentation.

## Create a new policy

- [**Microsoft Defender portal**](#tabpanel_3_M365D)
- [**Intune admin center**](#tabpanel_3_intune)

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Device configuration**. You see policies organized by operating system, such as **Windows client**, and policy type, such as **Next-generation protection** and **Firewall**.
3. Select an operating system tab, for example, **Windows clients**. Review the **Next-generation protection** policies.
4. Under **Next-generation protection** or **Firewall**, select **+ Add**.
5. On the **General information** tab, take the following steps:

   1. Specify a name and description. This information helps you and your team identify the policy later on.
   2. Review the policy order, and edit it if necessary. For more information, see [Policy order](https://learn.microsoft.com/en-us/defender-business/mdb-policy-order).
   3. Select **Next**.

6. On the **Device groups** tab, either create a new device group, or use an existing group. You assign policies to devices through device groups. Here are some things to keep in mind:

   - Initially, you might only have your default device group, which includes the devices people in your company use to access company data and email. You can keep and use your default device group.
   - Create a new device group to apply a policy with specific settings that are different from the default policy.
   - When you set up your device group, you specify certain criteria, such as the operating system version. Devices that meet the criteria are included in that device group, unless you exclude them.
   - Microsoft Entra ID stores all device groups, including the default and custom device groups that you define.


   To learn more about device groups, see [Device groups](https://learn.microsoft.com/en-us/defender-business/mdb-create-edit-device-groups).

7. On the **Configuration settings** tab, specify the settings for your policy, and then select **Next**. For more information about the individual settings, see [Configuration settings for Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection).
8. On the **Review your policy** tab, review the general information, targeted devices, and configuration settings.

   - Make any needed changes by selecting **Edit**.
   - When you're ready to proceed, select **Create policy**.

To configure a policy by using Microsoft Intune endpoint security policies, see [Create an endpoint security policy](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#create-endpoint-security-policies). This link opens in a new tab in the Intune documentation. When you create the policy, select the **Policy type**, **Platform**, and **Profile** for the protection you want to configure. For the list of policy types, supported platforms, and available profiles, see [Available endpoint security policy types](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy#available-endpoint-security-policy-types).

Important

Microsoft Defender for Endpoint management supports device objects only. Targeting users isn't supported. Assign the policy to Microsoft Entra device groups, not user groups.

The following profiles are the most relevant for Defender for Business:

- **Antivirus**: Set up your [next-generation protection policy](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection), define [exclusions for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/configure-exclusions-microsoft-defender-antivirus), or turn on [tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview).
- **Firewall**: Set up your [firewall protection policy](https://learn.microsoft.com/en-us/defender-business/mdb-firewall), including [custom rules](https://learn.microsoft.com/en-us/defender-business/mdb-firewall#manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business).
- **Attack surface reduction**: Set up [attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-and-exclusions-in-intune-using-endpoint-security-policies) or [controlled folder access \(CFA\)](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-configure#configure-cfa-in-intune-using-endpoint-security-policies).

## Related content

- [Understand policy order](https://learn.microsoft.com/en-us/defender-business/mdb-policy-order)
- [Set up your security policies and settings](https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings)
