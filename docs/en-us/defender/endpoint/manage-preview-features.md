<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-preview-features -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Manage individual preview features in Microsoft Defender for Endpoint \(preview\)

Important

The preview features page is in public preview. Some information relates to a prerelease product that might be substantially modified before it's released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

The preview features page in the Microsoft Defender portal lets you turn individual Microsoft Defender for Endpoint public preview features on or off. Instead of opting in to every preview feature at once, you choose which features to try, and for some features, which devices get them first.

## Why manage preview features individually

Until now, the **Preview features** setting turned on all Defender for Endpoint public preview features for your whole tenant. For organizations with mission-critical devices, that all-or-nothing choice made it hard to try new capabilities without accepting the risk of every preview at once.

The preview features page gives you more deliberate control over feature adoption:

- **Choose features one at a time.** Turn on only the preview feature\(s\) that matter to your organization, and leave the rest off.
- **Adopt gradually.** Some features can be scoped by safe deployment channel. Start with devices in an early channel, confirm the feature works as expected, and then expand to the rest of your environment.
- **Keep changes predictable.** New preview features are off by default unless your tenant was part of the private preview, so a feature reaches your devices only when you decide it should.
- **Validate before general availability.** Try features in your environment early and share feedback while there's still time to influence the final release.

The preview features page is part of Microsoft's safe deployment practices for Defender for Endpoint, which help you validate changes on a small, intentionally selected population before they reach the rest of your devices.

## Preview features you can manage

Only a subset of all Defender for Endpoint public preview features will be shown here, because this page only contains public preview features you can enable or disable through this experience.

More preview features will be added to the page over time. When a feature becomes generally available, you will no longer be able to interact with it. It will be marked as generally available and is later removed.

## How features are scoped

Each feature on the page uses one of two scopes:

- **Tenant-wide**: The feature is turned on or off for all devices in your tenant.
- **By safe deployment channel**: The feature is turned on only for devices in the channels you select. To use this scope, assign devices to safe deployment channels first. For more information, see [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout).

## Prerequisites

- The **Preview features** setting turned on in **Settings** > **Endpoints** > **Optional features**. The preview features page appears only when this setting is on.
- To scope an eligible feature by channel, you must assign devices to safe deployment channels. If a feature has the ability to be scoped by channel, it will say in the description.

## Turn a preview feature on or off

1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Settings** > **Endpoints** > **Preview features**.
2. Find the feature you want to change.
3. Turn the feature on or off. If the feature supports channel scoping, select the channels that should receive it.

After you turn on a public preview feature, use it as described in that feature's documentation. For example, after you turn on embedded offboarding, go to **Settings** > **Endpoints** > **Offboarding** and select **Offboard** to generate a deployment tool with an offboarding key.

If a feature is not working as expected, ensure the minimum feature requirements are met. If the feature rolls out using safe deployment channels, then you will not see the feature in the channel\(s\) you specified until Microsoft makes the feature available for that channel.

## Default settings

- Preview features on the page are off by default unless your tenant participated in the feature's private preview.
- If your organization used a feature during its private preview, that feature is turned on by default when it reaches public preview.

## How this page relates to the Preview features setting

The **Preview features** setting in **Optional features** continues to control public preview features that you can't manage on the preview features page yet. As more features move to the preview features page, you'll manage them individually there. When the preview features page becomes generally available, it will be available to every tenant, regardless of if you have the Preview features setting enabled in Optional features.

## Related content

- [Microsoft Defender for Endpoint preview features](https://learn.microsoft.com/en-us/defender-endpoint/preview)
- [Use the Microsoft Defender deployment tool for Windows](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows)
- [Manage the gradual rollout process for Microsoft Defender updates](https://learn.microsoft.com/en-us/defender-endpoint/manage-gradual-rollout)
