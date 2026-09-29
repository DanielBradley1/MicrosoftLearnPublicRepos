<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/configure-asset-rules -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Create dynamic rules for devices in asset rule management

Important

Some information in this article relates to prereleased products/services that might be substantially modified before they are commercially released. Microsoft makes no warranties, express or implied, for the information provided here.

Dynamic rules for devices can help manage device context by assigning tags and device values automatically based on certain criteria, saving time and ensuring accuracy of the device inventory. Dynamic rules also ensure devices remain relevant by removing tags or updating values when criteria are no longer met.

Maintaining an accurate inventory of devices in a constantly changing corporate environment is a critical task for security and IT teams. Failing to effectively manage device context, such as device value and tags, which many organizations use in their security workflows can lead to security vulnerabilities.

Devices might also require updates, replacements, or reconfigurations due to changing business needs. This can create a significant challenge for security and IT teams who are responsible for the ongoing management of the device inventory, and ensuring devices are effectively tracked and managed over time.

You can create dynamic rules in the **Asset rule management** in the Microsoft Defender portal to help you create steps in managing devices, like tagging devices with a specific OS version or assigning a value to devices with a particular naming convention.

## Create a new dynamic rule

A rule can be based on device name, domain, OS platform, internet facing status, onboarding status and manual device tags. You can select an existing tag or create a new tag. The selected or newly created tag is applied based on the conditions you set.

The following steps guide you on how to create a new dynamic rule in Microsoft Defender XDR:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) as a user who can view and perform actions on all devices.
2. In the navigation pane, select **Settings** > **Microsoft Defender XDR** > **Asset Rule Management**.
3. Select **Create a new rule**.
4. Enter a **Rule name** and **Description**\*.
5. Select **Next** to choose the conditions you want to assign:

   [![Screenshot of the Rule conditions page](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/rule-conditions.png)](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/rule-conditions.png#lightbox)
6. Select **Next** and choose the tag to apply to this rule.

   [![Screenshot of the actions page](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/actions-to-apply.png)](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/actions-to-apply.png#lightbox)
7. Select **Next** to review and finish creating the rule and then select **Submit**.

   Note

   It may take up to 1 hour for changes to be reflected in the portal.

### View dynamic tags in Device Inventory

You can see the dynamic tags assigned on the **Device Inventory** page in the Microsoft Defender portal.

Note

Dynamic tags are not supported by [security baseline assessments](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-baselines).

To see tags on individual devices:

1. In the [Microsoft Defender portal](https://security.microsoft.com), select **Devices** from the **Assets** navigation menu.
2. In the **Device Inventory** page, select the device name that you want to view.
3. Select **Manage tags**.

   [![Screenshot of the machine tags page](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/manage-machine-tags.png)](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/manage-machine-tags.png#lightbox)

### Update an existing dynamic rule

Dynamic tags and device values set by dynamic rules can't be manually updated.

Warning

Deleting a dynamic rule removes it and can affect tag or device value assignments. If you want to keep the rule but stop applying it, select **Turn off** instead of **Delete**.

To edit, delete, or turn off a rule, on the **Asset Rule Management** page, select the rule and then select **Edit**, **Delete**, or **Turn off**.

[![Screenshot of the rule details page](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/update-rule.png)](https://learn.microsoft.com/en-us/defender-xdr/media/configure-asset-rules/update-rule.png#lightbox)
