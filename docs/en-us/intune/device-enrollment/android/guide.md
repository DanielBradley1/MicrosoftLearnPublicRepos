<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/android/guide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Enrollment guide: Enroll Android devices in Microsoft Intune

Personal and organization-owned devices can be enrolled in Intune. Once enrolled, they receive the policies and profiles you create. You have the following options when enrolling Android devices:

- [BYOD: Android Enterprise personally owned devices with a work profile](#byod-android-enterprise-personally-owned-devices-with-a-work-profile)
- [Android Enterprise corporate owned dedicated devices](#android-enterprise-dedicated-devices) \(COSU\)
- [Android Enterprise corporate owned fully managed](#android-enterprise-fully-managed) \(COBO\)
- [Android Enterprise corporate owned work profile](#android-enterprise-corporate-owned-work-profile) \(COPE\)
- [Android Open Source Project \(AOSP\)](#android-open-source-project-aosp)
- [Android device administrator](#android-device-administrator) \(DA\)

This article provides enrollment recommendations and includes an overview of the administrator and user tasks for each option.

There's also a visual guide of the different enrollment options for each platform:

[![A visual representation of Intune enrollment options by platform](https://learn.microsoft.com/en-us/intune/device-enrollment/media/guide/msft-intune-enrollment-options-thumb-landscape.png)](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf)  
[Download PDF version](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.pdf) \| [Download Visio version](https://download.microsoft.com/download/e/6/2/e6233fdd-a956-4f77-93a5-1aa254ee2917/msft-intune-enrollment-options.vsdx)

## Before you begin

For a list of all the Intune-specific prerequisites and configurations needed to prepare your tenant for enrollment, go to [Enrollment guide: Microsoft Intune enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/guide).

Note

After you create an enrollment profile and assign it to users or groups, don't rename the enrollment profile. It can prevent future enrollments. If you need to change the name of the enrollment profile, then:

1. Create a new enrollment profile with the new name.
2. Assign the new profile to users & devices.
3. Delete the old profile.

## BYOD: Android Enterprise personally owned devices with a work profile

These devices are personal or BYOD \(bring your own device\) Android devices that access organization email, apps, and other data.

---

| Feature | Use this enrollment option when |
| --- | --- |
| Use Google Mobile Services \(GMS\). | ✅ |
| Devices are personal or BYOD. | ✅  <br>  <br>You can mark these devices as corporate or personal. |
| You have new or existing devices. | ✅ |
| Need to enroll a few devices, or a large number of devices \(bulk enrollment\). | ✅ |
| Devices are associated with a single user. | ✅ |
| You use the optional device enrollment manager \(DEM\) account. | ✅ |
| Devices are managed by another MDM provider. | ❌  <br>  <br>When a device enrolls, MDM providers install certificates and other files. These files must be removed. The quickest way might be to unenroll, or factory reset the devices. If you don't want to factory reset, then contact the other MDM provider for guidance. |
| Devices are owned by the organization or school. | ❌  <br>  <br>Not recommended for organization-owned devices. Organization-owned devices should be enrolled using [Android Enterprise fully managed](#android-enterprise-fully-managed) \(in this article\), or using [Android Enterprise corporate owned work profile](#android-enterprise-corporate-owned-work-profile) \(in this article\). |
| Devices are user-less, such as kiosk, dedicated, or shared. | ❌  <br>  <br>User-less or shared devices should be organization-owned. These devices should be enrolled using Android Enterprise dedicated devices. |

---

### Admin tasks \(personally owned devices with a work profile\)

This task list provides an overview. For more specific information, go to [Set up enrollment of Android Enterprise personally owned work profile devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-personal-work-profile).

- Be sure your devices are [supported based on platform](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms). For AOSP devices, go to [Android Open Source Project Supported Devices](https://learn.microsoft.com/en-us/intune/fundamentals/aosp-supported-devices).
- Connect your Intune organization account to your Managed Google Play account in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). When you connect, Intune automatically adds the Company Portal app and other common Android Enterprise apps to the devices. For the specific steps, go to [Connect your Intune account to your Managed Google Play account](https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play).

### End user tasks \(personally owned devices with a work profile\)

Your users must do the following steps. For the specific user experience, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-work-profile-android).

Depending on your organization's configuration, users enroll using web-based enrollment or the Company Portal app.

**Web-based enrollment:**

1. The user navigates to the enrollment URL provided by their organization, or is redirected from the Intune Company Portal app or a productivity app such as Outlook or Teams.
2. The user selects **Get started**.
3. The user selects **Accept & continue**.
4. A Google Chrome browser opens prompting the user to continue.
5. The user signs in with their work credentials and follows the prompts to install essential apps, register their device, and create a work profile.

**App-based enrollment:**

1. User goes to the Google Play store and installs the [Company Portal app](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).
2. User opens the Company Portal app and signs in with their organization credentials \(`user@contoso.com`\). After signing in, your enrollment profile applies to the device.

   For more specific steps, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-work-profile-android).

Tip

Intune is transitioning personally owned work profile management to web-based enrollment. For information on what's changing and how to prepare, see [Android Management API for personally owned work profiles](https://learn.microsoft.com/en-us/intune/device-enrollment/android/android-management-api-overview).

Users typically don't like enrolling themselves, and may not be familiar with the Company Portal app. Be sure to provide guidance, including what information to enter. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide#step-5---create-a-rollout-plan).

Tip

There is a short, step-by-step video to help your users in enroll their devices in Intune:

[Enroll your Android device](https://www.youtube.com/watch?v=9Dl8HsGk4tI&t=3s)

## Android Enterprise dedicated devices

Previously referred to as COSU. These devices are organization-owned, and are supported by Google's Zero Touch. The only purpose is to be a kiosk-style device. They aren't associated with a single or specific user. These devices are commonly used to scan items, print tickets, get digital signatures, manage inventory, and more.

---

| Feature | Use this enrollment option when |
| --- | --- |
| Use Google Mobile Services \(GMS\). | ✅ |
| Devices are owned by the organization or school. | ✅ |
| You have new or existing devices. | ✅ |
| Need to enroll a few devices, or a large number of devices \(bulk enrollment\). | ✅ |
| Devices are user-less, such as kiosk, dedicated, or shared. | ✅ |
| Devices are personal or BYOD. | ❌  <br>  <br>BYOD or personal devices should be enrolled using [Android Enterprise personally owned devices with a work profile](#byod-android-enterprise-personally-owned-devices-with-a-work-profile) \(in this article\). |
| Devices are associated with a single user. | ❌  <br>  <br>Not recommended. These devices should be enrolled using Android Enterprise fully managed. |
| You use the optional device enrollment manager \(DEM\) account. | ❌  <br>  <br>The DEM account isn't supported. |
| Devices are managed by another MDM provider. | ❌  <br>  <br>To be fully managed by Intune, users need to unenroll from the current MDM provider, and then enroll in Intune. |

---

### Admin tasks \(Dedicated devices\)

This task list provides an overview. For more specific information, go to [Set up Intune enrollment of Android Enterprise dedicated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-dedicated).

- Be sure your devices are [supported](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).
- Factory reset the devices. This step is required.
- Connect your Intune organization account to your Managed Google Play account in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). When you connect, Intune automatically adds the Intune app and other common Android Enterprise apps to the devices. For the specific steps, go to [Connect your Intune account to your Managed Google Play account](https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play).
- Create an enrollment profile in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), and have your dedicated device group ready to receive the profile. For the specific steps, go to [Set up Intune enrollment of Android Enterprise dedicated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-dedicated).
- Enroll the devices in Intune. For the specific steps, go to [Enroll your Android Enterprise devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/ref-corporate-methods).

  On Samsung's Knox devices, you can automatically enroll a large number of Android Enterprise devices using Samsung Knox Mobile Enrollment \(KME\). For more information, go to [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-samsung-knox-mobile).
- Communicate to your users how they should enroll: Near Field Communication \(NFC\), Token, QR Code, Google Zero Touch, or Samsung Knox Mobile Enrollment \(KME\).

### End user tasks \(Dedicated devices\)

Admins can complete the enrollment themselves, and then give the devices to the users. Or, users can enroll the devices using the following steps:

1. Users turn on the device, and are prompted for information, including the enrollment method: NFC, Token, QR Code, or Google Zero Touch.
2. After they enter the required information, your enrollment profile applies to the device. When the enrollment wizard completes, the device is ready to use.

Users typically don't like enrolling themselves, and may not be familiar with the Company Portal app. Be sure to provide guidance, including what information to enter. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide#step-5---create-a-rollout-plan).

## Android Enterprise fully managed

Previously referred to as COBO. These devices are organization-owned, and have one user. They're used exclusively for organization work; not personal use.

---

| Feature | Use this enrollment option when |
| --- | --- |
| Use Google Mobile Services \(GMS\). | ✅ |
| Devices are owned by the organization or school. | ✅ |
| You have new or existing devices. | ✅ |
| Need to enroll a few devices, or a large number of devices \(bulk enrollment\). | ✅ |
| Devices are associated with a single user. | ✅ |
| Devices are user-less, such as kiosk, dedicated, or shared. | ❌  <br>  <br>User-less devices should be enrolled using [Android Enterprise dedicated devices](#android-enterprise-dedicated-devices) \(in this article\). |
| Devices are personal or BYOD. | ❌  <br>  <br>BYOD or personal devices should be enrolled using [Android Enterprise personally owned devices with a work profile](#byod-android-enterprise-personally-owned-devices-with-a-work-profile) \(in this article\). |
| Devices are managed by another MDM provider. | ❌  <br>  <br>To be fully managed by Intune, users need to unenroll from the current MDM provider, and then enroll in Intune. |
| You use the optional device enrollment manager \(DEM\) account | ❌  <br>  <br>The DEM account isn't supported. |

---

### Admin tasks \(Fully managed\)

This task list provides an overview. For more specific information, go to [Set up Intune enrollment of Android Enterprise fully managed devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-fully-managed).

- Be sure your devices are [supported](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).
- Factory reset the devices. This step is required.
- Connect your Intune organization account to your Managed Google Play account in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). When you connect, Intune automatically adds the Company Portal app and other common Android Enterprise apps to the devices. For the specific steps, go to [Connect your Intune account to your Managed Google Play account](https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play).
- Enable fully managed user devices in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). For the specific steps, go to [Set up Intune enrollment of Android Enterprise fully managed devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-fully-managed).
- Enroll the devices in Intune. For the specific steps, go to [Enroll your Android Enterprise devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/ref-corporate-methods).
- Communicate to your users how they should enroll: Near Field Communication \(NFC\), Token, QR Code, Google Zero Touch, or Samsung Knox Mobile Enrollment \(KME\).

  Using Samsung Knox Mobile Enrollment \(KME\), you can automatically enroll a large number of Android Enterprise Samsung Knox devices. For more information, go to [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-samsung-knox-mobile).

### End user tasks \(Fully managed\)

The specific steps depend on how you configured the enrollment profile. For the specific user experience, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intune-app-android).

1. Users turn on the device, and are prompted for information, including the enrollment method: NFC, Token, QR Code, or Google Zero Touch. They can be asked to sign in with their organization credentials \(`user@contoso.com`\).
2. After they enter the required information, your enrollment profile applies to the device.

   Users might have to enter more information. For more specific steps, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intune-app-android).

Users typically don't like enrolling themselves, and may not be familiar with the Company Portal app. Be sure to provide guidance, including what information to enter. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide#step-5---create-a-rollout-plan).

## Android Enterprise corporate owned work profile

Previously referred to as COPE. These devices are organization-owned, and have one user. They're used for organization work, and allow personal use.

---

| Feature | Use this enrollment option when |
| --- | --- |
| Use Google Mobile Services \(GMS\). | ✅ |
| Devices are owned by the organization or school. | ✅ |
| You have new or existing devices. | ✅ |
| Need to enroll a few devices, or a large number of devices \(bulk enrollment\). | ✅ |
| Devices are associated with a single user. | ✅ |
| Devices are user-less, such as kiosk, dedicated, or shared. | ❌  <br>  <br>User-less devices should be enrolled using Android Enterprise dedicated devices. Also, an organization administrator can enroll. When the device is enrolled, create a [dedicated device](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise) \(Device experience\) profile, and assign this profile to this device. |
| Devices are personal or BYOD. | ❌  <br>  <br>BYOD or personal devices should be enrolled using [Android Enterprise personally owned devices with a work profile](#byod-android-enterprise-personally-owned-devices-with-a-work-profile) \(in this article\). |
| Devices are managed by another MDM provider. | ❌  <br>  <br>To be fully managed by Intune, users need to unenroll from the current MDM provider, and then enroll in Intune. |
| You use the optional device enrollment manager \(DEM\) account. | ❌  <br>  <br>The DEM account isn't supported. |

---

### Admin tasks \(Corporate owned with a work profile\)

This task list provides an overview. For more specific information, go to [Set up Intune enrollment of Android Enterprise corporate owned work profile](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-corporate-work-profile).

- Be sure your devices are [supported](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).
- Factory reset the devices. This step is required.
- Connect your Intune organization account to your Managed Google Play account in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). When you connect, Intune automatically adds the Company Portal app and other common Android Enterprise apps to the devices. For the specific steps, go to [Connect your Intune account to your Managed Google Play account](https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play).
- Enable corporate-owned personal profile devices in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). For the specific steps, go to [Set up Intune enrollment of Android Enterprise corporate-owned devices with work profile](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-corporate-work-profile).
- Enroll the devices in Intune. For the specific steps, go to [Enroll your Android Enterprise devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/ref-corporate-methods).
- Communicate to your users how they should enroll: Near Field Communication \(NFC\), Token, QR Code, Google Zero Touch, or Samsung Knox Mobile Enrollment \(KME\).

  Using Samsung Knox Mobile Enrollment \(KME\), you can automatically enroll a large number of Android Enterprise Samsung's Knox devices. For more information, go to [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-samsung-knox-mobile).

### End user tasks \(Corporate owned with a work profile\)

The specific steps depend on how you configured the enrollment profile. For the specific user experience, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intune-app-android).

1. Users turn on the device, and are prompted for information, including the enrollment method: NFC, Token, QR Code, or Google Zero Touch. They can be asked to sign in with their organization credentials \(`user@contoso.com`\).
2. After they enter the required information, your enrollment profile applies to the device.

   Users might have to enter more information. For more specific steps, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intune-app-android).

Users typically don't like enrolling themselves, and may not be familiar with the Company Portal app. Be sure to provide guidance, including what information to enter. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide#step-5---create-a-rollout-plan).

## Android Open Source Project \(AOSP\)

Note

Currently, there's limited OEM support for this enrollment method.

Also referred to as AOSP. These devices are organization-owned, and don't use Google Mobile Services \(GMS\). They can be kiosk-style devices that aren't associated with a single or specific user, or can have one user. They're used exclusively for organization work; not personal use.

When you create the Intune enrollment profile, you decide if the devices are userless, or are associated with a single user. For more information on these options, including supported OEMs, go to:

- [Set up Intune enrollment for Android \(AOSP\) corporate-owned userless devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-userless)
- [Set up Intune enrollment for Android \(AOSP\) corporate-owned user-associated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-user-associated)

---

| Feature | Use this enrollment option when |
| --- | --- |
| Use Google Mobile Services \(GMS\). | ❌  <br>  <br>These devices don't support [GMS](https://www.android.com/gms/) \(opens Android's web site\). Some countries/regions don't support GMS.  <br>  <br>If your devices will use GMS, then use [dedicated devices](#android-enterprise-dedicated-devices) \(in this article\) or [fully managed](#android-enterprise-fully-managed) \(in this article\) enrollment. |
| Devices are owned by the organization or school. | ✅ |
| You have new or existing devices. | ✅ |
| Need to enroll a few devices, or a large number of devices \(bulk enrollment\). | ❌  <br>  <br>Can only enroll one device at a time. |
| Devices are associated with a single user. | ✅ |
| Devices are user-less, such as kiosk, dedicated, or shared. | ✅ |
| Devices are personal or BYOD. | ❌  <br>  <br>[Android Enterprise personally owned devices with a work profile](#byod-android-enterprise-personally-owned-devices-with-a-work-profile) \(in this article\) support [GMS](https://www.android.com/gms/) \(opens Android's web site\). |
| Devices are managed by another MDM provider. | ❌  <br>  <br>To be fully managed by Intune, users need to unenroll from the current MDM provider, and then enroll in Intune. |
| You use the optional device enrollment manager \(DEM\) account | ❌  <br>  <br>The DEM account isn't supported. |

---

### Admin tasks \(AOSP\)

This task list provides an overview. For more specific information, go to enrollment for [AOSP corporate-owned userless devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-userless) and [AOSP corporate-owned user-associated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-user-associated).

- Be sure your devices are [supported](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).
- Factory reset the devices. This step is required. New devices might not require a factory reset.
- Create an enrollment profile in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), and have your device groups ready. For the specific steps, go to:

  - [AOSP corporate-owned userless devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-userless)
  - [AOSP corporate-owned user-associated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-user-associated)

- Enroll the devices in Intune. For the specific steps, go to:

  - [AOSP corporate-owned userless devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-userless)
  - [AOSP corporate-owned user-associated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-aosp-corporate-user-associated)


  During enrollment, the Microsoft Intune app and Microsoft Authenticator app automatically install and open on the device, which allows the device to enroll. The device is locked in the enrollment process until enrollment completes.

### End user tasks \(AOSP\)

The specific steps depend on how you configured the enrollment profile.

Admins can complete the enrollment themselves, and then give the devices to the users. Or, users can enroll the devices using the following steps:

1. Users turn on the device, and are prompted for information, including the enrollment method: QR Code. If you created a user-associated devices enrollment profile, then they might be asked to sign in with their organization credentials \(`user@contoso.com`\).
2. If you created a userless devices enrollment profile, then wait for the enrollment wizard to complete. When it does, the device is ready to use.

   If you created a user-associated devices enrollment profile, then users enter the required information. Then, wait for the enrollment wizard to complete. For more specific steps, go to [enroll the device](https://learn.microsoft.com/en-us/intune/user-help/enrollment/enroll-intune-app-android).

Users typically don't like enrolling themselves, and may not be familiar with the Company Portal app. Be sure to provide guidance, including what information to enter. For some guidance on communicating with your users, see [Planning guide: Step 5 - Create a rollout plan](https://learn.microsoft.com/en-us/intune/fundamentals/planning-guide#step-5---create-a-rollout-plan).

## Android device administrator

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

These Android devices are corporate, or personal/BYOD \(bring your own device\) devices that can access organization email, apps, and other data.

[Google deprecated Android device administrator management](https://blog.google/products/android-enterprise/da-migration/) in 2020. Intune is ending support for device administrator devices with access to Google Mobile Services in August 2024.

Microsoft recommends:

- Don't enroll new devices using Android device administrator.
- Enroll new devices using one of the other methods described in this article and/or using [App protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/overview).
- Move existing Android device administrator devices to one of the other methods described in this article. If you're moving them to [Android Enterprise personally owned devices with a work profile](#byod-android-enterprise-personally-owned-devices-with-a-work-profile) \(in this article\), consider using the streamlined flow to move [Android devices from device administrator to personally owned work profile management](https://learn.microsoft.com/en-us/intune/device-enrollment/android/migrate-device-admin-to-work-profile).
- Create a device enrollment restriction to block device administrator enrollment. Android devices can try to enroll using device administrator before trying other enrollment methods. So, create the restriction to prevent this behavior. For more information, go to [Set enrollment restrictions](https://learn.microsoft.com/en-us/intune/device-enrollment/restrictions).

## Related articles

- [MAM](https://learn.microsoft.com/en-us/intune/app-management/protection/mam-without-enrollment)
- [iOS/iPadOS enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/guide-ios-ipados)
- [Linux enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/guide-linux)
- [macOS enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/apple/guide-macos)
- [Windows enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/guide)
