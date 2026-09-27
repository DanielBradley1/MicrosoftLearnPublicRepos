<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-1 -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Get an Apple token for school devices

Before you can enroll corporate-owned devices with Apple School Manager, you need a token \(.p7m\) file from Apple. This token lets Intune sync information about Apple School Manager-participating devices. It also permits Intune to perform enrollment policy uploads to Apple and to assign devices to those policies. While you are in the Apple portal, you can also assign device serial numbers to manage.

## Get Apple token

In the first set of steps, you download the Intune public key certificate required to create an Apple token.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices**.
2. Expand **Device onboarding**, and then select **Enrollment**.
3. Select the **Apple mobile** tab.
4. Choose **Enrollment program tokens**.
5. Select **Create**.
6. Select **I agree** to give permission to Microsoft to send user and device information to Apple.
7. Select **Download your public key**. This step downloads and saves the encryption key \(.pem\) file locally. The .pem file is used to request a trust-relationship certificate from the Apple School Manager portal.

   In the next set of steps, you download a token and assign devices. Keep the browser and tab with the admin center open while you're completing steps in Apple School Manager.

   Tip

   The following steps describe what you need to do in Apple School Manager. For the specific steps, see the [Apple School Manager User Guide](https://support.apple.com/guide/apple-school-manager/device-workflow-axm6a88f692e/1/web/1) \(opens Apple Support\).
8. Choose **Create a token via Apple School Manager**, and sign in to [Apple School Manager](https://school.apple.com) with your company Apple ID. You can use this Apple ID to renew your Apple School Manager token.
9. In Apple School Manager, go to your MDM Server assignments to add an MDM server.
10. Enter the mobile device management \(MDM\) server name. The server name is for your reference to identify the MDM server. It isn't the name or URL of the Microsoft Intune server.
11. Upload the public key certificate file \(.pem file\).
12. Save your MDM server.
13. Select the download button to download the server token \(.p7m\) file to your computer.
14. Go to **Devices** and select the devices you want to assign to this token. You can sort by various device properties, like serial number. You can also select multiple devices simultaneously.
15. Select **Edit MDM Server**. Select the MDM server you just added, and then save your changes. This step assigns devices to the token.
16. Return to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and enter the Apple ID you used to create the token.

    ![Example screenshot showing the Apple ID used to create the enrollment program token and browsing to the enrollment program token.](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/media/school-manager/image03.png)

17. For **Apple token**, browse to the certificate \(.pem\) file. Select **Open**, and then choose **Create**. With the push certificate, Intune can enroll and manage devices by pushing policies to enrolled devices. Intune automatically syncs your Apple School Manager devices from Apple.

## Next steps

This series of articles describes how to set up Microsoft Intune for devices purchased through Apple School Manager.

1. [Prerequisites](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager)
2. 🡺 Get an Apple token for school devices \(*You are here*\)
3. [Create an Apple enrollment policy](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-2)
4. [Sync and distribute devices](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-3)
