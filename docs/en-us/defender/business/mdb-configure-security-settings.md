<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings -->
<!-- Sitemap-Last-Modified: 2026-06-25 -->

# Set up, review, and edit your security policies and settings in Microsoft Defender for Business

This article shows you how to review, create, or edit your security policies, and how to navigate advanced settings in [Microsoft Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-overview).

![Diagram that depicts step 6 - Review and edit security policies in Defender for Business.](https://learn.microsoft.com/en-us/defender-business/media/mdb-setup-step6.png)

When you set up or maintain Defender for Business, an important task is reviewing and configuring device policies:

- **Default policies**:

  - [Next-generation protection](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection)
  - [Firewall protection](https://learn.microsoft.com/en-us/defender-business/mdb-firewall)

- **Other settings**:

  - [Attack surface reduction features](https://learn.microsoft.com/en-us/defender-business/mdb-asr)

- **Settings for advanced features**:

  - [Turn on \(or off\) advanced features](https://learn.microsoft.com/en-us/defender-business/mdb-portal-advanced-feature-settings#view-settings-for-advanced-features)
  - [Specifying which time zone to use in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-business/mdb-portal-advanced-feature-settings#view-and-edit-other-settings-in-the-microsoft-365-defender-portal)
  - [Whether to receive preview features as they become available](https://learn.microsoft.com/en-us/defender-xdr/preview)

## Choose where to manage security policies and devices

Before you create or edit security policies, decide which portal to use:

- [Microsoft Defender portal](https://security.microsoft.com)
- [Microsoft Intune admin center](https://intune.microsoft.com)

The following table explains both options.

| Option | Description |
| --- | --- |
| Defender portal | A one-stop shop for managing company devices, security policies, and security settings in Defender for Business. With a simplified configuration process, you can use the Defender portal to:<br><br>- Onboard devices.<br>- Access your security policies and settings.<br>- Use the [Microsoft Defender Vulnerability Management dashboard](https://learn.microsoft.com/en-us/defender-business/mdb-view-tvm-dashboard).<br>- [View and manage incidents](https://learn.microsoft.com/en-us/defender-business/mdb-view-manage-incidents)<br><br>. |
| Intune admin center | Although Defender for Business doesn't include Microsoft Intune, you can use the Intune admin center to:<br><br>- Manage your company devices and apps, including how they access your company data.<br>- Onboard devices and access your security policies and settings in Intune.<br>- Set up and configure attack surface reduction rules.<br><br>If your company has Intune, you can continue using Intune to manage your devices and security policies. To learn more, see [Manage device security with endpoint security policies in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/endpoint-security-policy). |

If you use Intune, and you attempt to view or edit security policies in the Defender portal by going to **Configuration management** > **Device configuration**, you're prompted to choose whether to continue using Intune, or switch to using the Defender portal, as shown in the following screenshot:

![Screenshot showing the prompt to keep using Intune or switch to the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-business/media/mdb-usingintune-switchquestion.png)

In the preceding screenshot, **Use Defender for Business configuration instead** refers to using the Defender portal. The Defender portal provides a simplified configuration experience designed for small and medium-sized businesses. If you decide to use the Defender portal, you need to delete any existing security policies in Intune to avoid policy conflicts. For more information, see [I need to resolve a policy conflict](https://learn.microsoft.com/en-us/defender-business/mdb-troubleshooting#i-need-to-resolve-a-policy-conflict).

Note

Policies you manage in the Defender portal are listed in the Intune admin center as **Antivirus** or **Firewall** policies. When you view your firewall policies in the Intune admin center, you see two policies listed: one policy for firewall protection and another for custom rules.

You can export your list of policies from the Intune admin center.

## Related content

- [Review or edit your next-generation protection policies](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection)
- [Review or edit your firewall policies](https://learn.microsoft.com/en-us/defender-business/mdb-firewall)
- [Set up your web content filtering policy](https://learn.microsoft.com/en-us/defender-business/mdb-web-content-filtering)
- [Configure controlled folder access \(CFA\)](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview#deployment-and-configuration-methods-for-cfa)
- [Enable your attack surface reduction \(ASR\) rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-overview#deployment-and-configuration-methods-for-asr-rules)
- [Review settings for advanced features and the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-business/mdb-portal-advanced-feature-settings)
