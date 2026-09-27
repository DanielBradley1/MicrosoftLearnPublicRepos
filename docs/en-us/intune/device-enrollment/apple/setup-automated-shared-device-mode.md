<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-shared-device-mode -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Set up enrollment for devices in shared device mode

*Applies to iOS/iPadOS*

Set up automated device enrollment for devices in [shared device mode](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-ios-shared-devices). *Shared device mode* is a feature of Microsoft Entra ID that enables frontline workers to securely share a single device throughout the day, signing in and out as needed. This experience utilizes the [Microsoft Enterprise SSO plug-in](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-enterprise-sso-plugin-ios) to limit the number of times employees have to sign in during a session.

Corporate-owned devices purchased through Apple Business or Apple School Manager can be enrolled in Intune via automated device enrollment. Microsoft Intune supports zero-touch provisioning for devices in shared device mode, which means that the device can be set up and enrolled in Intune with minimal interaction from the frontline worker.

In this article, you will:

- Create an Apple enrollment policy
- Create a dynamic Microsoft Entra group for automatic grouping
- Create an assignment filter for fast provisioning
- Create a device configuration policy for single-sign on \(SSO\) app extension
- Assign Microsoft Authenticator app \(VPP version\)

## Prerequisites

- Complete all [prerequisites for Apple Automated Device Enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-ios#prerequisites).
- Read [Before you begin](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/overview-automated-enrollment-apple#before-you-begin) for best practices and recommendations for automated device enrollment.

## Step 1: Create an Apple enrollment policy

Create an Apple automated device enrollment policy in Microsoft Intune for devices enrolling in shared device mode. Include these configurations:

- **User affinity**: Enroll with Microsoft Entra ID shared mode
- **Locked enrollment**: Yes
- **Apply device name template**: Yes \(optional\)
- **Device Name Template** \(optional\): {{DEVICETYPE}}-{{SERIAL}}
- **Toggle All** \(optional\): Hide

Although optional, we recommend applying a device name template with the recommended formatting. You can also hide all or some Setup Assistant screens to speed up provisioning and user onboarding. When you're done configuring the rest of the enrollment policy, assign it to devices.

Note

You cannot change the user affinity setting in an existing enrollment policy. If you need to modify this setting, you must create a new Apple enrollment policy.

For more information about how-to create an enrollment policy, see [Create an Apple enrollment policy](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-ios#create-an-apple-enrollment-policy).

## Step 2: Create a dynamic Microsoft Entra group

Create a dynamic Microsoft Entra group using the `enrollmentProfileName` property to automatically group devices that enroll with a specific enrollment policy. In this case, we want to group devices that are in shared device mode and enrolling with the policy you created in Step 1. Include these configurations when creating your dynamic group:

- **Group type**: Security
- **Membership type**: Dynamic Device
- Add a dynamic query with the following rule:

  - **Property**: enrollmentProfileName
  - **Operator**: Equals
  - **Value**: Enter the name of the enrollment policy you created for devices in shared device mode.

For more information about how to create a dynamic group for shared devices in Microsoft Entra ID, see [Create a group membership rule](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-create-rule#to-create-a-group-membership-rule).

## Step 3: Create an assignment filter

Create an assignment filter to quickly target devices assigned to your enrollment policy. Add a rule with the following parameters:

- **Property**: enrollmentProfileName
- **Operator**: Equals
- **Value**: Enter the name of the enrollment policy you created for devices in shared device mode.

For more information about how to create an assignment filter rule, see [Create a filter](https://learn.microsoft.com/en-us/intune/fundamentals/filters/overview#prerequisites).

## Step 4: Create a device configuration policy

Configure a single-sign on \(SSO\) app extension policy for shared device mode. Create a device configuration policy and include these configurations:

- **Profile type**: Templates
- **Template name**: Device features
- Expand **Single sign-on app extension**, and then configure:

  - **SSO app extension type**: Microsoft Entra ID
  - **Enable shared device mode**: Yes
  - **Key**: device\_registration
  - **Type**: String
  - **Value**: {{DEVICEREGISTRATION}}

You can configure the rest of the policy to meet your organization's needs. When you're done configuring the policy, assign it to **All devices** and then add the assignment filter you created in [Step 3](#step-3-create-an-assignment-filter).

For more information about creating an SSO app extension policy, see:

- [Create a device configuration policy](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-features-apple#create-the-profile)
- [Single-sign on \(SSO\) app extension settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-device-features-apple#single-sign-on-sso)

## Step 5: Assign the Microsoft Authenticator app

Assign the Microsoft Authenticator app to targeted devices. Assign the app as *required* to **All devices**. Then add the assignment filter you created in [Step 3](#step-3-create-an-assignment-filter). You must have purchased the Microsoft Authenticator app through an Apple volume-purchase program.

For more information about assigning a volume-purchased app, see [Assign a volume purchased app](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-vpp-apple#assign-a-volume-purchased-app).

## Step 6: Distribute devices

Shared devices, which are enrolled without user affinity, require minimal user interaction from the frontline worker. Upon receiving the device, the frontline worker will need to open the Microsoft Authenticator app to make sure the device is in shared device mode.

Users typically don't like enrolling themselves, and may not be familiar with the Company Portal app. Be sure to provide guidance, including what information to enter. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide#step-5---create-a-rollout-plan).
