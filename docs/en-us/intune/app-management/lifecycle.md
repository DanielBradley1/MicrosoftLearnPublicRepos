<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/lifecycle -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Overview of the App Lifecycle in Microsoft Intune

The Microsoft Intune app lifecycle begins when an app is added and progresses through additional phases until you remove the app. By understanding these phases, you'll have the details you need to get started with app management in Intune.

![The app lifecycle - Add, deploy, configure, protect and retire.](https://learn.microsoft.com/en-us/intune/app-management/media/lifecycle/app-lifecycle.png "the Intune app lifecycle")

## Add

The first step in app deployment is to add the apps, which you want to manage and assign, to Intune. While you can work with many different app types, the basic procedures are the same. With Intune you can add different app types, including apps written in-house \(line-of-business\), apps from the store, apps that are built in, and apps on the web. For more information about each of these app types, see [How to add an app to Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/).

## Deploy

After you've added the app to Intune, you can then [assign it to users and devices that you manage](https://learn.microsoft.com/en-us/intune/app-management/deployment/assign-groups). Intune makes this process easy, and after the app is deployed, you can [monitor the success](https://learn.microsoft.com/en-us/intune/app-management/monitor-assignments) of the deployment from the Intune within the portal. Additionally, in some app stores, such as the [Apple](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-vpp-apple) app store, you can purchase app licenses in bulk for your company. Intune can synchronize data with these stores so that you can deploy and track license usage for these types of apps right from the Intune administration console.

## Configure

As part of the app lifecycle, new versions of apps are regularly released. Intune provides tools to easily [update apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/) that you have deployed to a newer version. Additionally, you can configure extra functionality for some apps, for example:

- [iOS/iPadOS app configuration policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-ios) supply settings for compatible iOS/iPadOS apps that are used when the app is run. For example, an app might require specific branding settings or the name of a server to which it must connect.
- [Microsoft Edge management policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android) help you configure settings for [Microsoft Edge](https://learn.microsoft.com/en-us/intune/app-management/ref-protected-apps#microsoft-apps), which replaces the default device browser and lets you restrict the websites that your users can visit.

## Protect

Intune gives you many ways to help protect the data in your apps. The main methods are:

- [Conditional Access](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/overview), which controls access to email and other services based on conditions that you specify. Conditions include device types or compliance with a [device compliance policy](https://learn.microsoft.com/en-us/intune/device-security/compliance/overview) that you deployed.
- [App protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/overview) works with individual apps to help protect the company data that they use. For example, you can restrict copying data between unmanaged apps and apps that you manage, or you can prevent apps from running on devices that have been jailbroken or rooted.

## Retire

Eventually, it's likely that apps that you deployed become outdated and need to be removed. Intune makes it easy to uninstall apps. For more information, see [Uninstall an app](https://learn.microsoft.com/en-us/intune/app-management/deployment/#uninstall-an-app).

## Next steps

- Learn about [app management in Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/overview)
