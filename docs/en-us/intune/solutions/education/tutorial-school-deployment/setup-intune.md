<!-- Source: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/setup-intune -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Set up Microsoft Intune

Without the proper tools and resources, managing hundreds or thousands of devices in a school environment can be a complex and time-consuming task. Microsoft Intune is a collection of services that simplifies the management of devices at scale.

The Microsoft Intune service can be managed in different ways.

- **Intune admin center** is the primary Intune interface that supports the entire device lifecycle, from the enrollment phase through retirement. IT administrators can manage all settings across all Intune supported platforms.
- **Intune for Education** is a curated view of Intune that supports the entire device lifecycle, from the enrollment phase through retirement. IT administrators can start managing classroom devices with bulk enrollment options and a streamlined deployment. At the end of the school year, IT admins can reset devices, ensuring they're ready for the next year.

  [![Intune for Education dashboard](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-education-portal.png)](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-education-portal.png#lightbox)

  For more information, see [Intune for Education documentation](https://learn.microsoft.com/en-us/intune-education/what-is-intune-for-education).

Tip

**Intune** and **Intune for Education** both configure the **Intune** service. Changes made in one admin center are reflected in the other. However, **Intune for Education** only supports a subset of policies and apps curated to suit simple K-12 scenarios on Windows and iPadOS.

---

In this section you will:

- Review Intune's licensing prerequisites
- Configure the Intune service for education devices

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Check out the requirements for device management

Before configuring settings with Intune, consider the following prerequisites:

- **Intune subscription.** Microsoft Intune is licensed in three ways:

  - As a standalone service
  - As part of [Enterprise Mobility + Security](https://www.microsoft.com/microsoft-365/microsoft-365-enterprise)
  - As part of a [Microsoft 365 Education subscription](https://www.microsoft.com/licensing/product-licensing/microsoft-365-education)

- **Intune for Education device platforms.** Intune for Education can manage devices running a supported version of Windows, Windows 11 SE, and iPadOS
- **Intune device platforms.** Intune can manage devices running a supported version of Windows, Windows 11 SE, iOS, iPadOS, macOS, Android, and Linux
- **Network requirements.** Confirm all the required network endpoints can access without SSL inspection or any type of filtering. See [Network endpoints for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/endpoints) for a list of endpoints.

For more information, see [Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing) and [this comparison sheet](https://aka.ms/EDU-Plan-Comparison), which includes a table detailing the *Microsoft Modern Work Plan for Education*.

## Configure the Intune service for Education devices

The Intune service can be configured in different ways, depending on the needs of your school. In this section, you configure the Intune service using settings commonly implemented by K-12 school districts.

### Configure enrollment restrictions

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Restrict which devices can be managed

With enrollment restrictions, you control which devices can enroll and be managed by Intune. For example, you can prevent the enrollment of personal devices.

To block personally owned devices from enrolling:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Enroll devices** > **Device platform restrictions**.
3. Select the tab for the platform you want to restrict.
4. Select **Create restriction**.
5. On the **Basics** page, provide a name for the restriction and, optionally, a description > **Next**.
6. On the **Platform settings** page, in the **Personally owned devices** field, select **Block** > **Next**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/enrollment-restrictions.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/enrollment-restrictions.png" alt="This screenshot is of the device enrollment restriction page in Microsoft Intune admin center." data-linktype="relative-path">
   </a>
   </span>

7. Optionally, on the **Scope tags** page, add scope tags > **Next**.
8. On the **Assignments** page, select **Add groups**, and then use the search box to find and choose groups to which you want to apply the restriction > **Next**.
9. On the **Review + create** page, select **Create** to save the restriction.

For more information, see [Create a device platform restriction](https://learn.microsoft.com/en-us/intune/device-enrollment/restrictions).

### Optional configuration

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure optional tenant configuration

- Customize branding according to organization policies. For more information, see [How to configure the Intune Company Portal apps, Company Portal website, and Intune app](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-company-portal).
- Create Terms and conditions according to organization policies. For more information, see [Terms and conditions for user access](https://learn.microsoft.com/en-us/intune/device-enrollment/create-terms-and-conditions).

### Configure Windows enrollment

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure which users can enroll Windows devices

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **Enroll devices** > **Automatic Enrollment**.
3. Set the **MDM user scope** to **All** or **Some** and select a group if you want to restrict enrollment to certain users.

   Important

   The MDM user scope must be set to *All* if provisioning packages are used to enroll devices.
4. Set **MAM user scope** to **None**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-windows-enrollment.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-windows-enrollment.png" alt="A screenshot showing the MDM user scope and MAM user scope." data-linktype="relative-path">
   </a>
   </span>

5. Select **Save**.

For more information, see [Enable Windows automatic enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm#enable-windows-automatic-enrollment).

### Disable Windows Hello for Business

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Disable functionality typically inaccessible to students

Windows Hello for Business is a biometric authentication feature that allows users to sign in to their devices using a PIN, password, or fingerprint. Windows Hello for Business is enabled by default on Windows devices, and to set it up, users must perform for multifactor authentication \(MFA\). As a result, this feature might not be ideal for students, who don't have MFA enabled.

Tip

**Passwordless for Students**

If you're interested in using Windows Hello for Business with students, then review our guidance on how you can use Temporary Access Pass. For more information, see [Passwordless for Students](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/protect-passwordless-students).

It's common for Windows Hello for Business to be disabled at the tenant level. Then, a policy can be targeted at users or devices that need it. For example, staff and teachers.

To disable Windows Hello for Business at the tenant level:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **By platform** > **Windows** > **Device onboarding** > **Enrollment**.
3. Select **Windows Hello for Business**.
4. Ensure that **Configure Windows Hello for Business** is set to **disabled**.
5. Select **Save**.

[![Disablement of Windows Hello for Business from Microsoft Intune admin center.](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/whfb-disable.png)](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/whfb-disable.png#lightbox)

For more information how to enable Windows Hello for Business on specific devices, see [Create a Windows Hello for Business policy](https://learn.microsoft.com/en-us/intune/device-security/identity-protection/configure-tenant-wide-policy).

### Configure Intune data collection policy

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure Endpoint analytics

Intune needs permission to collect data for Endpoint analytics on Windows devices.

To enable data collection:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Reports** > **Endpoint analytics** > **Settings**.
3. Under **Intune data collection policy**, select **Intune data collection policy**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-data-collection-policy.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-data-collection-policy.png" alt="Selecting the Intune data collection policy." data-linktype="relative-path">
   </a>
   </span>

4. Select **Properties**.
5. Under **Configuration settings** select **Edit**.
6. Set **Health Monitoring** to **Enable**.
7. Select **Scope** and tick **Endpoint analytics**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-data-collection-policy-settings.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-data-collection-policy-settings.png" alt="A screenshot showing the configuration of the Intune data collection policy." data-linktype="relative-path">
   </a>
   </span>

8. Select **Review + Save**.
9. Select **Save**.

For more information on data collection, see [Endpoint analytics data collection](https://learn.microsoft.com/en-us/intune/endpoint-analytics/ref-data-collection).

### Configure Windows data

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Configure tenant Windows data settings

Intune needs permission to collect certain data for Windows update reports on Windows devices.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** > **Connectors and tokens** > **Windows data**
3. Under **Windows data** select **On**.
4. Review the **Windows license verification** section and configure as per your licensing.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-windows-data.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/media/setup-intune/intune-windows-data.png" alt="A screenshot showing the configuration of the Intune Windows data settings." data-linktype="relative-path">
   </a>
   </span>

5. Select **Save**.

For more information, see [Enable use of Windows diagnostic data by Intune](https://learn.microsoft.com/en-us/intune/privacy/enable-windows-diagnostic-data).

### Configure Windows device diagnostics

![](https://learn.microsoft.com/en-us/intune/media/icons/16/check.svg) Allow remote retrieval of diagnostic information

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** > **Device diagnostics**.
3. Configure settings as per your requirements.

This table provides the settings most commonly set by customers, but can be customized to suit your schools needs.

| Setting | Common configuration |
| --- | --- |
| Device diagnostics are available for corporate-managed devices running Windows. Diagnostics can include user identifiable information such as user or device name. | Enabled |
| Automatically capture diagnostics when devices experience a failure during the Windows Autopilot process on Windows. Diagnostics can include user identifiable information such as user or device name. | Enabled |

For more information, see [Collect diagnostics from a Windows device](https://learn.microsoft.com/en-us/intune/device-management/actions/collect-diagnostics).

### \(Optional\) Configure the Enrollment Status Page

Consider enabling the Enrollment Status Page if planning to use Windows Autopilot to enroll Windows devices in Intune.

The enrollment status page \(ESP\) displays the provisioning status to people enrolling Windows devices and signing in for the first time. You can configure the ESP to block device use until all required policies and applications are installed. Device users can look at the ESP to track how far along their device is in the setup process.

Additional information:

- [Windows Autopilot Enrollment Status Page](https://learn.microsoft.com/en-us/autopilot/enrollment-status)
- [Set up the Enrollment Status Page](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/setup-status-page)

This table provides the settings most commonly set by customers, but can be customized to suit your schools needs.

| **Blade** | **Configuration group** | **Setting** | **Value** |
| --- | --- | --- | --- |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\\Enrollment Status Page | Default\\Show app and profile configuration progress | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\\Enrollment Status Page | Default\\Show an error when installation takes longer than specified number of minutes | 120 |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\\Enrollment Status Page | Default\\Show custom message when time limit or error occurs | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\\Enrollment Status Page | Default\\Turn on log collection and diagnostics page for end users | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\\Enrollment Status Page | Default\\Only show page to devices provisioned by out-of-box experience \(OOBE\) | Yes |
| [Windows enrollment](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesEnrollmentMenu/%7E/windowsEnrollment) | General\\Enrollment Status Page | Enrollment Status Page\\Default\\Block device use until required apps are installed if they're assigned to the user/device | *All* or *Selected* with the minimum apps required.  <br>  <br>For example, Microsoft 365 apps or web content filtering software |

### Set up Apple MDM Certificate

- [Intune](#tabpanel_1_intune)
- [Intune for Education](#tabpanel_1_intune-for-education)

To set up an Apple MDM certificate, see [Get an Apple MDM push certificate](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/create-mdm-push-certificate#steps-to-get-your-certificate).

To set up an Apple MDM certificate in Intune for Education, see [Add an MDM push certificate](https://learn.microsoft.com/en-us/intune-education/setup-ios-device-management)

Important

The Apple MDM certificate needs to be renewed yearly. Make a note in your calendar to renew the certificate in just under a year from when you add the certificate. You can view the expiry date in the admin center at any time.

### Configure Volume Purchase Program \(VPP\)

- [Intune](#tabpanel_2_intune)
- [Intune for Education](#tabpanel_2_intune-for-education)

To set up an Apple VPP, see [How to manage iOS and macOS apps purchased through Apple Business with Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-vpp-apple).

To set up an Apple VPP in Intune for Education, see [Configure VPP tokens](https://learn.microsoft.com/en-us/intune-education/setup-ios-device-management#configure-vpp-tokens).

Important

The Apple VPP token needs to be renewed yearly. Make a note in your calendar to renew the token in just under a year from when you add the token. You can view the expiry date in the admin center at any time.

### Configure Automated Device Enrollment \(ADE\)

If you plan to integrate Apple School Manager and use Automated Device Enrollment, follow these steps.

- [Intune](#tabpanel_3_intune)
- [Intune for Education](#tabpanel_3_intune-for-education)

To set up an Apple MDM certificate, see [Set up automated device enrollment in Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-automated-ios).

To set up an Apple ADE in Intune for Education, see [Configure enrollment program token](https://learn.microsoft.com/en-us/intune-education/setup-ios-device-management#configure-enrollment-program-token).

Important

The Apple ADE token needs to be renewed yearly. Make a note in your calendar to renew the token in just under a year from when you add the token. You can view the expiry date in the admin center at any time.

---

## Next steps

When the Intune service configured, you can configure policies and applications in preparation for the deployment of students' and teachers' devices.

[Next: Configure devices >](https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/configure-overview)
