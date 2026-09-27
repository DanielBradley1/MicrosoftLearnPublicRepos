<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-company-portal-macos -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Add the macOS Company Portal App

To manage devices, install optional apps, and gain access to resources protected by Conditional Access on macOS devices with user affinity, users must install and sign in to the Company Portal app. You can provide instructions to your users to install Company Portal for macOS or install it on devices already enrolled directly from Intune.

You can use any of the following options to install the Company Portal for macOS app:

- [Instruct users to download and install Company Portal](#instruct-users-to-download-and-install-company-portal)
- [Install Company Portal for macOS as a macOS PKG app](#install-company-portal-for-macos-as-a-macos-pkg-app)
- [Install Company Portal for macOS by using a macOS Shell Script](#install-company-portal-for-macos-by-using-a-macos-shell-script)

To help keep the apps more secure and up to date once installed, the Company Portal app comes with Microsoft AutoUpdate \(MAU\).

Note

The Company Portal app can only be installed automatically on devices using Intune that are already enrolled using direct enrollment or Automated Device Enrollment. For personal device or manual enrollment, the Company Portal app must be downloaded and installed to initiate enrollment. See [Instruct users to download and install Company Portal](#instruct-users-to-download-and-install-company-portal).

## Instruct users to download and install Company Portal

You can instruct users to download, install, and sign in to Company Portal for macOS. For instructions on downloading, installing, and signing in to the Company Portal, see [Enroll your macOS device using the Company Portal app](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-company-portal-macos).

Note

The Intune Company Portal for macOS installs the universal version of the app that runs natively on Apple Silicon Macs. The same app installs the x64 version on Intel Mac machines.

## Install Company Portal for macOS as a macOS PKG app

Company Portal for macOS can be downloaded and installed as a PKG app. The version downloaded is the version that will always be installed and may need to be updated periodically to ensure users get the best experience during initial enrollment.

1. Download Company Portal for macOS from [https://go.microsoft.com/fwlink/?linkid=853070](https://go.microsoft.com/fwlink/?linkid=853070).
2. Follow the instructions in [Add an unmanaged macOS PKG app to Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-unmanaged-pkg-macos).

Note

Once installed, the Company Portal for macOS app will automatically update using Microsoft AutoUpdate \(MAU\).

## Install Company Portal for macOS by using a macOS Shell Script

Company Portal for macOS can be downloaded and installed using the [macOS Shell Scripts](https://learn.microsoft.com/en-us/intune/device-management/tools/run-shell-scripts-macos) feature. This option will always install the current version of Company Portal for macOS, but will not provide you with application install reporting you might be used to when deploying applications using [macOS LOB apps](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-lob-macos).

1. Download a sample script to install Company Portal for macOS from [Intune Shell Script Samples - Company Portal](https://github.com/microsoft/shell-intune-samples/tree/master/macOS/Apps/Company%20Portal).
2. Follow instructions to deploy the macOS Shell Script using [macOS Shell Scripts](https://learn.microsoft.com/en-us/intune/device-management/tools/run-shell-scripts-macos).

   - Set **Run script as signed-in user** to **No** \(to run in the system context\).
   - Set **Maximum number of retries if script fails** to **3**.

Note

The script will require internet access when it runs to download the current version of the Company Portal for macOS.

## Signing in to the Company Portal for macOS when using Setup Assistant with Modern Authentication

When creating an Automated Device Enrollment profile, you can choose the **Setup Assistant with modern authentication** authentication method. The user has to authenticate using Microsoft Entra credentials during the setup assistant screens. This will require an additional Microsoft Entra login post-enrollment in the Company Portal app to gain access to corporate resources protected by Conditional Access and for Intune to assess device compliance. The Company Portal can be installed in any of the three ways documented here for Setup Assistant with modern authentication.

Use one of the ways documented above to deploy the macOS Company Portal to the devices enrolling with Setup Assistant with modern authentication so that the end user can authenticate and complete Microsoft Entra registration.

Users must sign in to the Company Portal to complete Microsoft Entra authentication and gain access to resources protected by Conditional Access. User affinity is established when users complete the enrollment and reach the home screen of the macOS device. If the tenant has multifactor authentication turned on for these devices or users, the users will be asked to complete multifactor authentication during Setup Assistant. Multifactor authentication is not required, but it is available for this authentication method within Conditional Access if needed.

For more information about configuring Setup Assistant with modern authentication for macOS, see [Create an Apple enrollment policy](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos#create-an-enrollment-policy).

## Next steps

- To learn more about assigning apps, see [Assign apps to groups](https://learn.microsoft.com/en-us/intune/app-management/deployment/assign-groups).
- To learn more about configuring Automated Device Enrollment, see [Automated Device Enrollment for macOS](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-macos).
- To learn more about configuring Microsoft AutoUpdate settings on macOS, see [Deploy updates for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-updates).
