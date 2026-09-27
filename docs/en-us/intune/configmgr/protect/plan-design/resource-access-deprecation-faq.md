<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/resource-access-deprecation-faq -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# Frequently asked questions about resource access deprecation

*Applies to: Configuration Manager \(current branch\)*

Starting in Configuration Manager version 2103, the following company resource access [features are deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures):

- Certificate profiles, including the certificate registration point site system role
- VPN profiles
- Wi-Fi profiles
- Windows Hello for Business settings
- Email profiles
- The co-management resource access workload

Important

If above mentioned resource access profiles are configured in Intune, but the applicability to co-managed devices are controlled through the co-management Resource Access workload setting in Configuration Manager, post 2403 upgrade, the Resource Access workload is moved to Intune and hence all resource access profiles configured in Intune are now applicable and enforced to co-managed devices.

This article answers your frequently asked questions about these deprecated features.

## What happens when you upgrade to CM 2403?

When you upgrade your Configuration Manager site to 2403, the [prerequisite checker displays an error](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/list-of-prerequisite-checks#resource-access-policies-are-no-longer-supported). This blocks upgrade.

**Action required by customer:** Delete all Resource Access profiles and associated deployments and move the co-management workload for Resource Access \(if co-managed\) to Intune. Reevaluate the prerequisite rules, which allows you to proceed with upgrade.

After the upgrade completion, if the cloud attach wizard is configured, the Resource Access workload \(configured to Intune\) remains greyed out in console. If the customer isn't previously cloud attached and configures the cloud attach wizard, during or after upgrade, the Resource Access workload is defaulted to Intune and remains greyed out in the console. **Company Resource Access** node in Asset Management workspace will be removed.

## When will these features removed from Configuration Manager?

Starting in version 2203, these features will still be available in Configuration Manager, but no longer tested or supported. When you upgrade to version 2203, the [prerequisite checker displays a warning](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/list-of-prerequisite-checks#resource-access-policies-are-no-longer-supported).

In version 2207, the creation of new company resource access profiles including the certificate registration point site system role is disabled. Set/New/Import type PowerShell cmdlets for Resource Access features are deprecated as well.

These features will be removed in 2403.

## If I'm still using these features, can I upgrade to version 2207?

Yes. If the site has any of these policies, the 2207 prerequisite checker will display a warning. Before you upgrade to version 2211, replace the functionality of these features, and remove the policies from the site.

If the site has the certificate registration point site system role, you also need to remove it. For more information, see [Remove a site system role](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/uninstall-sites-and-hierarchies#procedure-to-remove-a-site-system-role).

## What functionality is available to replace these features?

Use Microsoft Intune to deploy resource access profiles. For more information, see [Apply features and settings on your devices using device profiles in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

Use [co-management](https://learn.microsoft.com/en-us/intune/configmgr/comanage/overview) to enroll Configuration Manager clients to Intune.

## What do I do if I'm deploying wi-fi profiles with Configuration Manager?

Before you upgrade to Configuration Manager version 2203, [enable co-management](https://learn.microsoft.com/en-us/intune/configmgr/comanage/how-to-enable), and deploy the same wi-fi profiles with Intune. For more information, see [Add and use Wi-Fi settings on your devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi). If you don't take action, the existing wi-fi profiles will persist on devices but are unmanaged.

## What happens if I don't enable co-management?

If you currently use these features, they're not tested or supported in version 2203. When you upgrade to version 2207, they'll cause warning prerequisite checks. You can't create new wi-fi, VPN, Windows Hello for Business, or certificate \(SCEP, PFX, or root CA\) profiles for Configuration Manager clients. Any existing deployed profiles won't be removed from devices and will continue to function. These existing profiles are unmanaged. For example, when a certificate expires, Configuration Manager won't renew it.

## What happens if I've enabled co-management, but haven't switched the resource access workload?

Starting in version 2211, the prerequisite checker will display a warning for co-managed clients if the resource access workload is on Configuration Manager. If the resource access slider is towards Configuration Manager, they aren't tested or supported in version 2203. Co-management behavior is the same as if you used Configuration Manager 2111 or earlier to switch the resource access workload to Intune. This Workload slider will be disabled, and you can only use Microsoft Intune to deploy resource access profiles in upcoming Configuration Manager versions.

## What alternative options are available?

Configuration Manager version 2111 fully supports these features and is supported until June 2023. For more information, see [Supported versions](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates#supported-versions).
