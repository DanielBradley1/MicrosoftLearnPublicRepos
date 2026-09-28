<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-plan -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 2: Plan your device deployment with Intune for Education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-devices.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

## Plan your deployment

There are three main methods for joining Windows devices to Microsoft Entra ID and getting them enrolled and managed by Intune:

- **Automatic Intune enrollment via Microsoft Entra join** happens when a user first turns on a device that is in out-of-box experience, and selects the option to join Microsoft Entra ID. In this scenario, the user can customize certain Windows functionalities before reaching the desktop, and becomes a local administrator of the device. This option isn't an ideal enrollment method for education devices.
- **Automatic Intune enrollment with provisioning packages.** Provisioning packages are files that can be used to set up Windows devices, and can include information to connect to Wi-Fi networks and to join a Microsoft Entra tenant. Provisioning packages can be created using either Set Up School PCs or Windows Configuration Designer applications. These files can be used from the school device's desktop, or by saving it to a USB flash drive and distributing it to other devices during the out-of-box-experience.
- **Automatic Intune enrollment with Windows Autopilot.** Windows Autopilot is a collection of cloud services to configure the out-of-box experience, enabling light-touch or zero-touch deployment scenarios. You can optionally use Windows Autopilot for pre-provisioned deployment to enroll Windows Autopilot-registered devices with required apps and settings so that they're nearly ready for school use when students receive them. Students just have to connect to Wi-Fi and complete the remaining setup steps.

### Provisioning package overview

A provisioning package \(.ppkg\) is a file that contains configuration settings and is used to quickly and efficiently configure Windows client devices without installing a new image. This method ensures that school devices have a standard set of apps and settings when students start using them. For more information, see [Provisioning packages overview.](https://learn.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-packages)

You can use Windows Configuration Designer or the Set up School PCs app to create provisioning packages. Both tools guide you through how-to to create the package. For more information, see:

- [What is Set up School PCs?](https://learn.microsoft.com/en-us/education/windows/use-set-up-school-pcs-app)
- [Windows Configuration Designer](https://learn.microsoft.com/en-us/windows/configuration/provisioning-packages/provisioning-install-icd)
- [Bulk enrollment for Windows devices](https://learn.microsoft.com/en-us/mem/intune/enrollment/windows-bulk-enroll)

After you create the provisioning package, you can copy it to one or more USB drives, insert them into devices and power them on to start the provisioning process.

Devices continue to sync in the background after provisioning. Track provisioning progress on the Enrollment Status Page to ensure all required mobile device management policies and apps are delivered before student use.

### Windows Autopilot overview

Windows Autopilot is a collection of technologies you can use to simplify the setup and configuration of new school devices. With this method, there's no need for imaging. To set up your devices with Windows Autopilot:

- Register the device with Autopilot in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) or [Partner center.](https://partner.microsoft.com/dashboard/home)
- Create and assign an Autopilot deployment profile, Enrollment Status Page \(ESP\) profile, apps, and policies.

Learn more: [Choose the enrollment method](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/plan-enrollment?tabs=intune&pivots=windows#choose-the-enrollment-method)

### Grouping and targeting overview

By organizing devices, students, classrooms, or learning curricula into groups, you can provide students with the resources and configurations they need.

### Intune targeting methods

[Intune has four targeting methods:](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/plan-grouping?tabs=intune&pivots=windows#grouping-and-targeting-overview)

- Virtual Groups - Created by Intune and allow you to target All devices and All users.
- Assigned groups - Used when you want to manually add users or devices to a group.
- Dynamic groups - Groups based on rules that you create to assign students or devices to groups.
- Filters - Allows you to further narrow the assignment scope of a policy or app when targeting a group.

[Choose grouping methods:](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/plan-grouping?tabs=intune&pivots=windows#choose-grouping-methods)

- Autopilot user driven
- Autopilot self-deploying mode
- All enrollment types

## Prepare your tenant

### Set up Microsoft Entra ID

[Setting up Microsoft Entra ID](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id) is core to establishing your tenant.

While this Education Solution Guide does cover requirements baseline tenant setup, the [Industry Guide for Education](https://learn.microsoft.com/en-us/intune/intune-service/industry/education/introduction-intune-education) is another source of information.

Steps for setup include:

- [Create a Microsoft tenant](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#create-a-microsoft-365-tenant)
- [Add users, create groups, assign licenses](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#add-users-create-groups-and-assign-licenses)

  - School Data Sync \(SDS\)
  - Microsoft Entra ID connect
  - Manually create users
  - Create groups
  - Assign licenses

- [Configure school branding](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#configure-school-branding)
- [Configure device settings](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#configure-device-settings)

  - [Enable Microsoft Entra join](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#enable-microsoft-entra-join)
  - [Enable storage of local passwords \(optional\)](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#enable-storage-of-local-administrator-passwords-optional)
  - [Configure Enterprise state roaming](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#configure-enterprise-state-roaming-optional)

- [Restrict access to administrative actions \(optional\)](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#restrict-access-to-administrative-actions-optional)
- [Restrict access to groups \(optional\)](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-entra-id#restrict-access-to-groups-optional)

### Set up Microsoft Intune

The Microsoft Intune service can be managed in different ways. Learn more about [setting up Intune](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows).

The following links are **Windows**-specific unless explicitly pointing to **iOS**.

- [Prerequisites](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#prerequisites)
- [Configure Intune service for Education devices](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#configure-the-intune-service-for-education-devices)

  - [Configure enrollment restrictions](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#configure-enrollment-restrictions)
  - [Configure enrollment restrictions **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=ios#configure-enrollment-restrictions)

- [Optional configurations](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#optional-configuration)
- [Set up Apple MDM Certificate **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=ios#set-up-apple-mdm-certificate)
- [Configure Volume Purchase Program \(VPP\) **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=ios#configure-volume-purchase-program-vpp)
- [Configure Automated Device Enrollment \(ADE\) **iOS**](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=ios#configure-automated-device-enrollment-ade)
- [Configure Windows enrollment](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#configure-windows-enrollment)
- [Disable Windows Hello for Business](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#disable-windows-hello-for-business)
- [Configure Intune data collection policy](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#configure-intune-data-collection-policy)
- [Configure Windows data](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#configure-windows-data)
- [Configure Windows device diagnostics](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#configure-windows-device-diagnostics)
- [Optional- Configure the Enrollment Status Page](https://learn.microsoft.com/en-us/mem/intune/industry/education/tutorial-school-deployment/set-up-microsoft-intune?tabs=intune&pivots=windows#optional-configure-the-enrollment-status-page)

## Next steps

Now that you planned your device management, you're ready to configure settings and applications.

[Next: Configure settings and applications>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-settings)
