<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-mngt-structure -->
<!-- Sitemap-Last-Modified: 2025-10-16 -->

# Step 1: Device management structure with Intune for Education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-devices.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Device management starts with a consistent and secure device management solution. Intune provides a mechanism to manage and deploy devices in your tenant.

## Prerequisites

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/license/a1.png) Microsoft 365 A1 for devices

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/products/entraid.png) Microsoft Entra ID \(Education\)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/products/intune.png) Microsoft Intune

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/products/intune.png) Microsoft Intune for Education

## Roles and responsibilities

- IT Admin
- Device Admin
- Identity Admin
- Teachers
- School Leaders
- Microsoft partners

## What is Intune for Education? Intune versus Intune for Education

**Microsoft Intune** is a comprehensive mobile device management \(MDM\) and mobile application management \(MAM\) platform designed to help organizations manage and secure their devices and applications. It offers a wide range of configuration options, integrates with Microsoft Entra ID for access control, and provides robust data protection through Azure Information Protection.

On the other hand, **Intune for Education** is a streamlined version of Intune, designed for educational institutions. It simplifies the setup and management of classroom devices and apps, making it easier for IT professionals in schools to deploy settings, apps, and tools that support learning. Intune for Education focuses on creating a safe learning environment, managing users, and securing data while ensuring privacy and compliance across all devices.

From the Web, **Intune for Education** is tailored to meet the specific needs of educational institutions, offering a simplified management and deployment process that saves significant time for IT professionals. It doesn't include some of the advanced features available in the full Intune console, which are geared towards enterprises. Despite this, **Intune for Education** isn't limiting, as schools, colleges, and universities often don't require these advanced features.

In summary, while both Intune and Intune for Education serve the purpose of managing and securing devices, Intune offers a more comprehensive set of features suitable for enterprises, whereas Intune for Education is streamlined to meet the specific needs of educational institutions, making it easier to manage classroom devices and apps.

Note

- Intune for Education is available for A1 for devices educational license.
- Intune is available with A3 or A5 license.

## Managed versus unmanaged devices

**Managed devices** are typically organization-owned devices that are set up and configured by your company's IT or security team. These devices are enrolled in Intune or Intune for Education, allowing for comprehensive management and security policies to be applied. This includes installing business-critical apps, applying policies, enabling features like BitLocker, and monitoring device health through the Microsoft Defender portal.

**Unmanaged devices**, also known as bring-your-own devices \(BYOD\), are personally owned devices that employees set up and use. These devices can also be onboarded and protected just like managed devices. Users can take steps to protect their BYOD devices themselves, such as using the Microsoft Authenticator app for multifactor authentication \(MFA\) and joining their devices to the organization's network.

Managed devices offer a higher level of control and security through Intune or Intune for Education, while unmanaged devices provide flexibility for employees to use their personal devices, with some security measures still being enforceable through Intune's app protection policies.

Note

For education scenarios:

- BYOD devices can be an alternative to organizations that don't have the budget for managed devices.
- Unmanaged devices can be used in educational organization for consultants and external users.

## Device lifecycle management

School IT administrators and educators need an easy-to-use, flexible, and secure way to manage the lifecycle of the devices in their schools. Microsoft has developed integrated suites of products for streamlined, cost-effective device lifecycle management.

Microsoft 365 Education provides tools and services that enable simplified management of all devices through Microsoft Intune services. With Microsoft's solutions, IT administrators have the flexibility to support diverse scenarios, including school-owned devices and bring-your-own devices.

Microsoft Intune services include:

- Microsoft Intune
- Microsoft Intune for Education
- Windows Autopilot
- Microsoft Surface Management Portal

These services are part of the Microsoft 365 stack to help secure access, protect data, and manage risk.

## Why Intune

Devices can be managed with Intune, enabling simplified management of multiple devices from a single point.

- Enroll: to enable remote device management, devices must be enrolled in Intune with an account in your Microsoft Entra tenant. Some enrollment methods require an IT administrator to initiate enrollment, while others require students to complete the initial device setup process. This document discusses the facets of various device enrollment methodologies
- Configure: once the devices are enrolled in Intune, applications and settings are applied.
- Protect and manage: in addition to its configuration capabilities, Intune helps protect devices from unauthorized access or malicious attacks. For example, managing Defender Antivirus and BitLocker can make devices more secure. Policies are available that let you control settings for Windows Firewall, Endpoint Protection, and software updates
- Retire: when it's time to repurpose a device, Intune offers several options, including resetting the device, removing it from management, or wiping school data. In this section, we cover different device return and exchange scenarios.

Note

For education scenarios:

- Enrollment of all teacher and faculty can help maintain and keep your internal network and devices secure and up-to-date.
- Configuring managed devices help control what organizations allow to be available on controlled devices.
- Some protection and management capabilities requires A3 or A5 licenses.
- Easy to reset devices after each school year and update those devices with new approved content.

## Four pillars of modern device management

- **Identity management:** setting up and configuring the identity system, with Microsoft 365 Education and Microsoft Entra ID, as the foundation for user identity and authentication
- **Initial setup:** setting up the Intune environment for managing devices, including configuring settings, deploying applications, and defining updates cadence
- **Device enrollment:** setting up devices for deployment and enrolling them in Intune
- **Device reset:** resetting managed devices with Intune

Note

For education scenarios:

- Intune and Intune for Education can be used to easily manage devices during the summer transition.

## Next steps

Now that you reviewed devices management structure, you're ready for planning device management.

[Next: Plan device management>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/devices/baseline-devices-plan)
