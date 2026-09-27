<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/quickstart-email-profile -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Step 11 - Create an email device profile for iOS/iPadOS in Microsoft Intune

In this article, you create an email profile for iOS/iPadOS devices. Email device profiles help standardize settings across your devices. By using these profiles, end users can access organization email on their personal devices without any confusing setup.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

To help safeguard your email, you can create a compliance policy that sets rules on devices that connect to email. Then, set up Conditional Access to allow only compliant devices access to your email profiles. To learn more about email profiles, see [configure email settings in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** Microsoft Intune role

## Create an iOS/iPadOS email profile

The profile includes the required settings that allow a device to connect to your organization's email.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** > **Manage devices** > **Configuration** > **Create** > **New policy**:

   [![Screenshot of Devices section in Intune admin center, Configuration selected, and Create button visible for new policy setup.](https://learn.microsoft.com/en-us/intune/device-configuration/templates/media/quickstart-email-profile/ios-create-profile.png)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/media/quickstart-email-profile/ios-create-profile.png#lightbox)
3. Enter the following properties:

   - **Platform**: Select **iOS/iPadOS**.
   - **Profile type**: Select **Templates** > **Email**.

4. Select **Create**.
5. In **Basics**, enter the following properties:

   - **Name**: Enter a descriptive name for the new profile. For this example, enter **iOS require work email**.
   - **Description**: Enter **Require iOS/iPadOS devices to use work email**.


   [![Screenshot of Microsoft Intune admin center, Basics step for iOS email profile with Name and Description entered.](https://learn.microsoft.com/en-us/intune/device-configuration/templates/media/quickstart-email-profile/ios-email-profile-name.png)](https://learn.microsoft.com/en-us/intune/device-configuration/templates/media/quickstart-email-profile/ios-email-profile-name.png#lightbox)

6. Select **Next**.
7. In **Configuration settings**, enter the following settings. For the other settings, use the default values.

   - **Email server**: For this evaluation step, enter `outlook.office365.com`. This setting specifies the Exchange location \(URL\) of the email server that the iOS/iPadOS mail app uses to connect to email.
   - **Account name**: Enter **Company Email**.
   - **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username for this profile using this name. For this evaluation step, use the **User Principal Name** as the username for the profile, like `user1@contoso.com`.
   - **Email address attribute from Microsoft Entra ID**: This setting is the email address from Microsoft Entra ID that signs in to Exchange. For this evaluation step, select **User Principal Name**.
   - **Authentication method**: For this evaluation step, select **Username and password**. If you set up [authentication certificates in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview), then you can choose **Certificate**.

8. Select **Next**.
9. In **Scope tags** \(optional\), select **Next**. In this example, don't use scope tags.
10. In **Assignments**, use the drop-down for **Assign to** and select **All users and all devices**. Then, select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned.

## Clean up resources

If you don't use this profile for other tutorials or testing, delete it:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **Manage devices** > **Configuration**.
2. Select the **iOS/iPadOS require work email** profile you created, and then select **Delete**.

## Next steps

In this article, you created an email profile for iOS/iPadOS devices. To learn more about all the profiles you can create in Intune, see [Create device profiles in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/overview).

This article is the last step in the evaluation guide. You set up a test environment and stepped through common tasks that help you better understand and use Intune.

When you're ready to deploy Intune in your organization, the following resources can help.

[Microsoft Intune planning guide](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide)

[Deploy or move to Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/get-started)

[Migration guide: Set up or move to Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/setup-migration)
