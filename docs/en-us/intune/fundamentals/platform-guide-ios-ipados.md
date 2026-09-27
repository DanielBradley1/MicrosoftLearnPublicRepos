<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-ios-ipados -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Deployment guide: Manage iOS/iPadOS devices in Microsoft Intune

Intune supports mobile device management \(MDM\) of iPads and iPhones to give users secure access to work email, data, and apps. This guide provides iOS-specific guidance to help you set up enrollment and deploy apps and policies to users and devices.

## Prerequisites

Before you begin, complete these prerequisites to enable iOS/iPadOS device management in Intune. For more detailed information about how to set up, onboard, or move to Intune, see the [Intune setup deployment guide](https://learn.microsoft.com/en-us/intune/fundamentals/setup-migration).

- [Add users](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-users) and [groups](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-groups)
- [Assign licenses to users](https://learn.microsoft.com/en-us/intune/fundamentals/assign-licenses)
- [Set mobile device management authority](https://learn.microsoft.com/en-us/intune/fundamentals/setup-mdm-authority)
- [Set up Apple MDM push \(APNs\) certificate](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/create-mdm-push-certificate)

We recommend you use the least privileged role that's needed to complete tasks. For example, the least privileged role that can complete device enrollment tasks is the built-in **Policy and Profile Manager** Intune role.

For more information on the built-in roles and what they can do, see [Role-based access control \(RBAC\) with Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) and [Built-in role permissions for Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles).

## Plan for your deployment

The [Microsoft Intune planning guide](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide) provides guidance and advice to help you determine goals, use-case scenarios, and requirements. It also describes how to create plans for rollout, communication, support, testing, and validation.

## Create compliance rules

Use compliance policies to define the rules and conditions that users and devices should meet to access your protected resources. If you use Conditional Access, your Conditional Access policies can use your device compliance results to block access to resources from noncompliant devices. For a detailed explanation about compliance policies and how to get started, see [Use compliance policies to set rules for devices you manage with Intune](https://learn.microsoft.com/en-us/intune/device-security/compliance/overview).

| Task | Detail |
| --- | --- |
| [Create a compliance policy](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-policy) | Get step-by-step guidance on how to create and assign a compliance policy to user and device groups. |
| [Add actions for noncompliance](https://learn.microsoft.com/en-us/intune/device-security/compliance/configure-noncompliance-actions) | Choose what happens when devices no longer meet the conditions of your compliance policy. You can add actions for noncompliance when you configure a device compliance policy, or later by editing the policy. |
| Create [a device-based](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-compliance) or [app-based](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/create-app-based-policy) Conditional Access policy | Specify the app or services you want to protect and define the conditions for access. |
| [Block access to apps that don't use modern authentication](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/block-no-modern-auth) | Create an app-based Conditional Access policy to block apps that use authentication methods other than OAuth2; for example, those apps that use basic and form-based authentication. Before you block access, however, sign in to Microsoft Entra ID and review the [authentication methods activity report](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-methods-activity) to see if users are using basic authentication to access essential things you forgot about or are unaware of. For example, things like meeting room calendar kiosks use basic authentication. |

## Configure endpoint security

Use the Intune endpoint security features to configure device security and to manage security tasks for devices at risk.

| Task | Detail |
| --- | --- |
| [Manage devices with endpoint security features](https://learn.microsoft.com/en-us/intune/device-management/manage-endpoint-security-devices) | Use the endpoint security settings in Intune to effectively manage device security and remediate issues for devices. |
| [Enable mobile threat defense \(MTD\) connector for unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/enable-unenrolled-devices) | Enable the MTD connection in Intune so that MTD partner apps can work with Intune and your policies. If you're not using Microsoft Defender for Endpoint, consider enabling the connector so that you can use another mobile threat defense solution. |
| [Create MTD app protection policy](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/create-app-protection-policy) | Create an Intune app protection policy that assesses risk and limits a device's corporate access based on the threat level. |
| [Add MTD apps to unenrolled devices](https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/add-apps-unenrolled-devices) | Make MTD apps available to people in your organization and configure Microsoft Authenticator for iOS/iPadOS. |
| [Use Conditional Access to limit access to Microsoft Tunnel](https://learn.microsoft.com/en-us/intune/device-security/microsoft-tunnel/conditional-access) | Use Conditional Access policies to gate device access to your Microsoft Tunnel VPN gateway. |

## Configure device settings

Use Microsoft Intune to enable or disable settings and features on iOS/iPadOS devices. To configure and enforce these settings, create a device configuration profile and then assign the profile to groups in your organization. Devices receive the profile once they enroll.

| Task | Detail |
| --- | --- |
| [Create a device profile in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile) | Learn about the different types of device profiles you can create for your organization. |
| [Configure device features](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-features-apple) | Configure common iOS/iPadOS features and functionality for a work or school context. For a description of the settings in this area, see the [device features reference](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-features-apple). |
| [Configure Wi-Fi profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wifi) | This profile enables people to find and connect to your organization's Wi-Fi network. For a description of the settings in this area, see the [Wi-Fi settings reference](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-apple). |
| [Configure VPN profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-vpn) | Set up a secure VPN option, such as Microsoft Tunnel, for people connecting to your organization's network. You can also [create a per-app VPN policy](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-per-app-vpn-ios) to require users to sign in to certain apps through a VPN connection. For a description of the settings in this area, see the [VPN settings reference](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-apple). |
| [Configure email profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email) | Configure email settings so that people can connect to a mail server and access their work or school email. For a description of the settings in this area, see the [email settings reference](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-ios). |
| [Restrict device features](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-restrictions) | Protect users from unauthorized access and distractions by limiting the device features they can use at work or school. For a description of the settings in this area, see the [device restrictions reference](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-apple). |
| [Configure custom profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-apple) | Add and assign device settings and features that aren't built into Intune. |
| [Customize branding and enrollment experience](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-company-portal) | Customize the Intune Company Portal and Microsoft Intune app experience with your organization's own words, branding, screen preferences, and contact information. |
| [Managed software updates](https://learn.microsoft.com/en-us/intune/device-updates/apple/) | Schedule automatic OS updates and installations for supervised iOS/iPadOS devices. |

## Set up secure authentication methods

Set up authentication methods in Intune to ensure that only authorized people access your internal resources. Intune supports multi-factor authentication, certificates, and derived credentials. Certificates can also be used for signing and encryption of email using S/MIME.

| Task | Detail |
| --- | --- |
| [Require multi-factor authentication \(MFA\)](https://learn.microsoft.com/en-us/intune/device-enrollment/configure-multifactor-authentication) | Require people to supply two forms of credentials at time of enrollment. |
| [Create a trusted certificate profile](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/trusted-root-profiles) | Create and deploy a trusted certificate profile before you create a SCEP, PKCS, or PKCS imported certificate profile. The trusted certificate profile deploys the trusted root certificate to devices and users using SCEP, PKCS, and PKCS imported certificates. |
| [Use SCEP certificates with Intune](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/scep-infrastructure) | Learn what's needed to use SCEP certificates with Intune, and configure the required infrastructure. After you do that, you can [create a SCEP certificate profile](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/scep-profiles) or [set up a third-party certification authority with SCEP](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/third-party-ca-scep). |
| [Use PKCS certificates with Intune](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/pkcs-profiles) | Configure required infrastructure \(such as on-premises certificate connectors\), export a PKCS certificate, and add the certificate to an Intune device configuration profile. |
| [Use imported PKCS certificates with Intune](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/imported-pfx-profiles) | Set up imported PKCS certificates, which enable you to [set up and use S/MIME to encrypt email](https://learn.microsoft.com/en-us/intune/device-security/certificates/s-mime). |
| [Set up a derived credentials issuer](https://learn.microsoft.com/en-us/intune/device-security/certificates/derived-credentials) | Provision iOS/iPadOS devices with certificates that are derived from user smart cards. |

## Deploy apps

As you set up apps and app policies, think about your organization's requirements, such as the platforms you'll support, the tasks people need to do, the type of apps they need to complete those tasks, and finally, the groups who need those apps. You can use Intune to manage the whole device \(including apps\) or use Intune to manage the apps only.

| Task | Detail |
| --- | --- |
| [Add store apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-store-ios) | Add iOS/iPadOS apps from the App Store to Intune, and assign to groups. |
| [Add web apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-web) | Add web apps to Intune and assign to groups. |
| [Add built-in apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-built-in) | Add built-in apps to Intune and assign to groups. |
| [Add line-of-business apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-lob-ios) | Add iOS/iPadOS line-of-business \(LOB\) apps to Intune, and assign to groups. |
| [Assign apps to groups](https://learn.microsoft.com/en-us/intune/app-management/deployment/assign-groups) | Assign apps to users and devices. |
| [Include and exclude app assignments](https://learn.microsoft.com/en-us/intune/app-management/deployment/configure-assignment-scope) | Control access and availability to an app by including and excluding selected groups from assignment. |
| [Manage iOS/iPadOS apps purchased through Apple Business](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-vpp-apple) | Synchronize, manage, and assign apps purchased through Apple Business. |
| [Manage iOS/iPadOS eBooks purchased through Apple Business](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-ebooks-ios) | Synchronize, manage, and assign books purchased through Apple Business. |
| [Create an iOS/iPadOS app protection policy](https://learn.microsoft.com/en-us/intune/app-management/protection/create-policy) | Keep your organization's data contained within managed apps like Outlook and Word. See [iOS/iPadOS app protection policy settings](https://learn.microsoft.com/en-us/intune/app-management/protection/ref-settings-ios) for details about each setting. |
| [Create an app provisioning profile](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-provisioning-profiles-ios) | Prevent app certificates from expiring by proactively assigning new provisioning profiles to devices that have apps nearing expiry. |
| [Create an app configuration policy](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-ios) | Apply custom configuration settings to iOS/iPadOS apps on enrolled devices. You can also apply these types of policies [to managed apps without device enrollment](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-apps). |
| [Configure Microsoft Edge](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-edge-ios-android) | Use Intune app protection and configuration policies with Edge for iOS/iPadOS to ensure corporate websites are accessed with safeguards in place. |
| [Configure Microsoft Office apps](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-microsoft-365-mobile) | Use Intune app protection and configuration policies with Office apps to ensure that corporate files are accessed with safeguards in place. |
| [Configure Microsoft Teams](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-teams-mobile) | Use Intune app protection and configuration policies with Teams to ensure that collaborative team experiences are accessed with safeguards in place. |
| [Configure Microsoft Outlook](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-outlook) | Use Intune app protection and configuration policies with Outlook to ensure corporate email and calendars are accessed with safeguards in place. |

## Enroll devices

Enrolling devices allows them to receive the policies you create, so have your Microsoft Entra user groups and device groups ready.

For information about each enrollment method and how to choose one that's right for your organization, see the [iOS/iPadOS device enrollment guide for Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/guide-ios-ipados).

| Task | Detail |
| --- | --- |
| [Set up Apple Automated Device Enrollment \(ADE\) in Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-ios) | Set up an out-of-the-box enrollment experience for corporate-owned devices purchased through Apple School Manager or Apple Business. For a detailed walkthrough of this process, see [Tutorial: Use Apple's Corporate Device Enrollment features in Apple Business to enroll iOS/iPadOS devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/tutorial-automated-ios) |
| [Set up Apple School Manager in Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager) | Set up Intune to enroll devices you purchased through the Apple School Manager program. |
| [Set up device enrollment with Apple Configurator](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-configurator-ios) | Create an Apple Configurator profile to enroll corporate-owned devices \(with no user affinity\) via direct enrollment; or to enroll wiped or new devices \(with user affinity\) via Setup Assistant. You'll need to export the Apple Configurator profile from Intune, which requires a USB connection to a Mac computer running Apple Configurator. |
| [Identify devices as corporate-owned](https://learn.microsoft.com/en-us/intune/device-enrollment/add-corporate-identifiers) | Assign corporate-owned status to devices to enable more management and identification capabilities in Intune. Corporate-owned status cannot be assigned to devices enrolled through Apple Business. |
| [Set up Apple User Enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/user-enrollment-methods-ios) | Create a user enrollment profile to deploy the Apple User Enrollment experience to devices using a managed Apple ID. |
| [Set up shared iPad devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/shared-ipad) | Configure devices so that they can be used by more than one person \(the type of setup you'd see in a library or educational environment\). |
| [Backup and restore devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/backup-restore-ios) | Back up and restore a device to prepare it for enrollment or migration in Intune, such as during Automated Device Enrollment setup. |
| [Change device ownership](https://learn.microsoft.com/en-us/intune/device-enrollment/add-corporate-identifiers#change-device-ownership) | After a device has been enrolled, you can change its ownership label in Intune to corporate-owned or personal-owned. This adjustment changes the way you can manage the device. |
| [Troubleshoot enrollment problems](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/troubleshoot-ios-enrollment-errors) | Troubleshoot and find resolutions to problems that occur during enrollment. |

## Run remote actions

After devices are set up, you can use remote actions in Intune to manage and troubleshoot devices from a distance. Availability varies by device platform. If an action is absent or disabled in the portal, then it isn't supported on the device.

| Task | Detail |
| --- | --- |
| [Take remote action on devices](https://learn.microsoft.com/en-us/intune/device-management/actions/) | Learn how to drill down and remotely manage and troubleshoot individual devices in Intune. This article lists all remote actions available in Intune and links to those procedures. |
| [Use TeamViewer to remotely administer Intune devices](https://learn.microsoft.com/en-us/intune/device-management/tools/teamviewer-legacy) | Configure TeamViewer within Intune, and learn how to remotely administer a device. |
| [Remediate vulnerabilities identified by Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/remediate-vulnerabilities) | Integrate Intune with Microsoft Defender for Endpoint to take advantage of Defender for Endpoint's threat and vulnerability management and use Intune to remediate endpoint weakness identified by Defender's vulnerability management capability. |

## Next steps

Check out these enrollment tutorials to learn how to do some of the top tasks in Intune. Tutorials are 100 – 200 level content for people new to Intune or a specific scenario.

- [Walk through Intune admin center](https://learn.microsoft.com/en-us/intune/fundamentals/tutorial-admin-center-walkthrough)
- [Use Apple corporate device enrollment features in Apple Business to enroll iOS/iPadOS devices in Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/tutorial-automated-ios)
- [Protect Exchange Online email on managed devices](https://learn.microsoft.com/en-us/intune/solutions/tutorials/protect-email-enrolled-devices)
- [Protect Exchange Online email on unmanaged devices](https://learn.microsoft.com/en-us/intune/solutions/tutorials/protect-email-unmanaged-devices)
- [Configure Slack to use Intune for EMM and app configuration](https://learn.microsoft.com/en-us/intune/app-management/configuration/tutorial-configure-slack)

For the Android version of this guide, see [Deployment guide: Manage Android devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-android).
