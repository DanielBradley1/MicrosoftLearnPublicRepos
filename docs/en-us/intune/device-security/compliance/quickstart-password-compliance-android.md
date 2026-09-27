<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/compliance/quickstart-password-compliance-android -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Step 6 - Create a password compliance policy for Android Enterprise devices

In this article, you use Microsoft Intune to create a password compliance policy for Android Enterprise devices. This policy requires your Android users to enter a password of a specific length to be compliant with your organization's security requirements. You can create a password compliance policy for any device platform that Intune supports. This example uses Android Enterprise.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

An Intune device compliance policy specifies the rules and settings that devices must meet to be considered compliant. You can enforce these compliance policies by using Microsoft Entra Conditional Access, which you can use to allow or block access to company resources. You can also get device reports and take actions for non-compliance.

Important

In addition to password settings, consider other system security settings to protect your workforce. For more information, see [System security settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-enterprise-settings).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Policy and Profile manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** Microsoft Intune role

## Create a device compliance policy

Create a device compliance policy that requires your Android users to enter a password of a specific length.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices** > **Compliance**.
2. On the **Policies** tab, select **Create policy**.
3. For **Platform**, select **Android Enterprise**.
4. For **Profile type**, select either **Fully managed, dedicated, and corporate-owned work profile** or **Personally-owned work profile**, and then select **Create**.
5. On **Basics**, enter **Android compliance** as the *Name*. Adding a *Description* is optional. Select **Next**.
6. On **Compliance settings**, expand **System Security** and configure the following settings:

   - For **Require a password to unlock mobile devices**, select **Require**.
   - For **Required password type**, select **At least numeric**.
   - For **Minimum password length**, enter **6**.


   [![Screenshot of Microsoft Intune admin center showing Compliance settings for Android with password requirements highlighted.](https://learn.microsoft.com/en-us/intune/device-security/compliance/media/quickstart-password-compliance-android/quickstart-set-password-length-android-01.png)](https://learn.microsoft.com/en-us/intune/device-security/compliance/media/quickstart-password-compliance-android/quickstart-set-password-length-android-01.png#lightbox)

7. On the **Assignments**, you can optionally assign the policy to the user or group you created in [Step 2 - Create a user and assign a license](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user) and [Step 3 - Create a group](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group) evaluation steps.
8. When done, select **Next** until you reach the **Review + create** step. Then, select **Create** to create the policy.

When you successfully create the policy, it appears in your list of device compliance policies.

## Conditional Access policy assignment

With the free trial, you can create a Conditional Access policy that enforces this password requirement. This tutorial doesn't include these steps but you can do it.

For more information, see:

- [Learn about Conditional Access and Intune](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/overview)
- [Common ways to use Conditional Access with Intune](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/scenarios)

## Clean up resources

When you no longer need the policy, delete it. To delete the policy, select the compliance policy and select **Delete**.

## Next steps

In this article, you used Intune to create a compliance policy for your Android Enterprise devices that requires a password with at least six characters. For more information about creating compliance policies, see [Get started with device compliance policies in Intune](https://learn.microsoft.com/en-us/intune/device-security/compliance/overview).

To continue evaluating Microsoft Intune, go to the next step:

[Step 7 - Send notifications to noncompliant devices](https://learn.microsoft.com/en-us/intune/device-security/compliance/quickstart-noncompliance-notification)
