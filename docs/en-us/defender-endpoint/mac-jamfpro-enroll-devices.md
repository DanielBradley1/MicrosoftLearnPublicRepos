<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-enroll-devices -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Enroll macOS devices in Jamf Pro for Microsoft Defender for Endpoint

Enroll macOS devices in Jamf Pro so Jamf Pro can deliver the configuration profiles and deployment policies required by Microsoft Defender for Endpoint. You can use invitation-based Device Enrollment or Automated Device Enrollment with a computer PreStage.

Jamf Pro is a separate product that isn't part of Defender for Endpoint and isn't included with Defender for Endpoint subscriptions. To use these procedures, your organization needs a separate Jamf Pro subscription. For product and subscription information, see [Jamf Pro](https://www.jamf.com/products/jamf-pro/). If your organization doesn't use Jamf Pro, you can [deploy Defender for Endpoint with Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune) or [use another MDM solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm).

Important

Microsoft provides information about Jamf Pro to support integration scenarios but doesn't provide troubleshooting support for this third-party product. For issues specific to Jamf Pro, contact Jamf support.

## Prerequisites

Before you enroll macOS devices, make sure you meet the following requirements:

- Review the [Defender for Endpoint on macOS prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites).
- [Set up computer groups in Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-device-groups).
- [Deploy and configure Defender for Endpoint on macOS with Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies).
- Verify that your Jamf Pro account has permission to configure enrollment and assign computers to the appropriate groups or PreStage enrollment.

## Choose an enrollment method

Jamf Pro supports several enrollment methods. The Defender for Endpoint deployment series covers these two methods:

- [Enrollment invitations](#enrollment-method-1-enrollment-invitations) for user-initiated Device Enrollment.
- [Automated Device Enrollment](#enrollment-method-2-prestage-enrollments) that uses a computer PreStage.

Choose the enrollment method that meets your organization's device ownership and deployment requirements.

## Enroll devices by using enrollment invitations

Jamf Pro Device Enrollment is intended for institutionally owned Mac computers that aren't eligible for Automated Device Enrollment. An enrollment invitation gives users email access to the enrollment portal and lets you control options such as expiration, sign-in requirements, and the number of times an invitation can be used.

Use the current Jamf Pro documentation to configure and complete invitation-based enrollment:

- Review [Device Enrollment for Computers](https://learn.jamf.com/r/jamf-pro-documentation-current/Device_Enrollment_for_Computers).
- Configure the [User-Initiated Enrollment settings](https://learn.jamf.com/r/jamf-pro-documentation-current/Configuring_the_User-Initiated_Enrollment_Settings).
- Follow [Sending a Computer Enrollment Invitation via Email](https://learn.jamf.com/r/jamf-pro-documentation-current/Sending_a_Computer_Enrollment_Invitation).
- Provide users with the [Device Enrollment Experience for Computers](https://learn.jamf.com/r/jamf-pro-documentation-current/User-Initiated_Enrollment_Experience_for_Computers).

## Enroll devices by using Automated Device Enrollment

Automated Device Enrollment is commonly used for organization-owned Mac computers and enrolls them during initial setup. Jamf Pro uses a computer PreStage enrollment to define the enrollment experience and the devices in scope.

Use the current Jamf Pro documentation to configure Automated Device Enrollment:

- Review [Automated Device Enrollment for Computers](https://learn.jamf.com/r/jamf-pro-documentation-current/Automated_Device_Enrollment_for_Computers), including the required integration with Apple Business Manager or Apple School Manager.
- Review how [Computer PreStage Enrollments](https://learn.jamf.com/r/jamf-pro-documentation-current/Computer_PreStage_Enrollments) define settings and scope.
- Follow [Creating or Editing a Computer PreStage Enrollment](https://learn.jamf.com/r/jamf-pro-documentation-current/Configuring_a_Computer_PreStage_Enrollment).

## Confirm device enrollment

Enrollment screens and required user actions vary by the macOS version and your Jamf Pro enrollment settings. Follow the current Jamf documentation for the selected enrollment method instead of relying on a fixed sequence of screens.

After enrollment is complete, verify in Jamf Pro that each Mac is enrolled, is assigned to the intended computer group or PreStage enrollment, and receives the Defender for Endpoint configuration profiles and deployment policy.
