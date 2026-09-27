<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/user-enroll-devices-on-premises-mdm -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How users enroll devices with on-premises MDM in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

With Configuration Manager on-premises mobile device management \(MDM\), users can enroll their devices. There are two prerequisites:

- With client settings, you grant the user permission to enroll.
- You install the required trusted root certificate on the device.

For more information on how to set up enrollment, see [Set up device enrollment for on-premises MDM](https://learn.microsoft.com/en-us/intune/configmgr/mdm/get-started/set-up-device-enrollment-on-premises-mdm).

## Enroll Windows 10

1. On a Windows 10 computer, go to **Settings**.
2. Select **Accounts**, and then select **Access work or school**.
3. Select **Connect**, enter your user principal name \(UPN\), and select **Continue**. The UPN may be the same as your email address, for example, jdoe@contoso.com.
4. Enter the fully qualified domain name \(FQDN\) of the enrollment proxy point, and select **Continue**.
5. Enter your password, and select **Sign in**.
6. Windows doesn't need to remember the sign-in info for this action, so select **Skip**.

After a short time, the device enrolls with Configuration Manager.

## Enroll Windows 10 Mobile

1. On a Windows 10 Mobile device, go to **Settings**.
2. Select **Accounts**, and then select **Work access**.
3. Select **Connect**.
4. Enter your UPN and the FQDN of the enrollment proxy point. Then select **Connect**.
5. On the next screen, enter your UPN and password, and then select **Sign-in**.

After a short time, the device enrolls with Configuration Manager. Select **Done**.

## Verify enrollment

Use the Configuration Manager console to verify that devices are enrolled successfully. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select **Devices**. Browse or search for the enrolled device in the list of devices.
