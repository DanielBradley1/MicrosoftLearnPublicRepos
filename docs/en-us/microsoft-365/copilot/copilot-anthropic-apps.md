<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-anthropic-apps -->
<!-- Sitemap-Last-Modified: 2026-09-03 -->

# Copilot in Microsoft 365 apps with Anthropic models

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. There are no changes to security, compliance, and privacy for organizations.

To provide additional flexibility in model choice for customers in the European Union \(EU\), European Free Trade Association \(EFTA\), and United Kingdom \(UK\), Microsoft Copilot includes an admin setting that enables the use of Anthropic models in Copilot experiences across Word, Excel, and PowerPoint.

This setting allows Microsoft Copilot in supported Microsoft 365 apps to use Anthropic models by default when generating or refining content.

Important

The Anthropic independent processor \(IP\) setting was decommissioned on May 1, 2026. If Anthropic is not enabled as a Microsoft subprocessor, access to Anthropic models and related features is no longer available. Enable Anthropic as a subprocessor in the [Microsoft 365 admin center](https://admin.microsoft.com).

## Anthropic model availability in Microsoft 365 apps

As the admin, you can manage the Anthropic model setting in the Microsoft 365 admin center. When this setting is turned on, Anthropic models are available for use in Copilot experiences across:

- Microsoft Excel
- Microsoft PowerPoint
- Microsoft Word

This setting applies only to Copilot experiences within these apps and does not affect Anthropic model usage in other Microsoft Copilot features or services. It is separate from the [global Anthropic subprocessor setting in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor). Changes to this setting do not modify global subprocessor configurations.

This setting is on by default for tenants in the EU, EFTA, and UK that were created after March 25, 2026. For tenants in the EU, EFTA and UK that existed before March 25, 2026, check the [Message Center](https://go.microsoft.com/fwlink/p/?linkid=2070717) for details on your tenant's default setting.

All tenant administrators are encouraged to check their tenant's setting to make sure it aligns with their company's requirements.

## Data processing and the EU Data Boundary

When Anthropic models are used in Copilot experiences in Word, Excel, or PowerPoint, data processing for these models occurs outside of the Microsoft EU Data Boundary \(EUDB\).

[Anthropic operates as a Microsoft subprocessor](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor) and is subject to Microsoft Product Terms and the Microsoft Data Protection Addendum \(DPA\).

## Manage the setting in the Microsoft 365 admin center

1. Sign in to the Microsoft 365 admin center as an administrator assigned the **AI Administrator** role.
2. Go to **Copilot** -> **Settings** -> **View All** -> **AI providers operating as Microsoft subprocessors**.

   [![Screenshot of the AI providers operating as Microsoft subprocessors page with user and security group options.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ai-providers-operating-as-subprocessors-sec-group.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/ai-providers-operating-as-subprocessors-sec-group.png#lightbox)
3. Confirm the correct setting for your organization.

Note

Support for Anthropic models in Microsoft 365 apps varies based on how the AI providers operating as Microsoft subprocessors setting is scoped in your organization. When the setting is enabled for **All users** or **Specific users and groups**, the Anthropic model use in supported apps setting is unavailable and can't be changed. This setting applies only to Copilot experiences within supported apps and doesn't affect Anthropic model usage in other Microsoft Copilot features or services.
