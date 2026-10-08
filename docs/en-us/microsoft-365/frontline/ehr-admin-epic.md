<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-admin-epic?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Virtual Appointments with Teams - Integration into Epic EHR

The Microsoft Teams Electronic Health Record \(EHR\) connector makes it easy for clinicians to launch a virtual patient appointment or consultation with another provider in Microsoft Teams directly from the Epic EHR system. Built on the Microsoft 365 cloud, Teams enables simple, secure collaboration and communication with chat, video, voice, and healthcare tools in a single hub that supports compliance with HIPAA, HITECH certification, and more.

The communication and collaboration platform of Teams makes it easy for clinicians to cut through the clutter of fragmented systems so they can focus on providing the best possible care. With the Teams EHR connector, you can:

- Launch Teams Virtual Appointments from your Epic EHR system with an integrated clinical workflow.
- Enable patients to join Teams Virtual Appointments from within the patient portal
- Support other scenarios including multi-participant, group visits, and interpreter services.
- Write metadata back to the EHR system about Teams Virtual Appointments to record when attendees connect, disconnect, and enable automatic auditing and record keeping.
- View consumption data reports and customizable Call Quality information for EHR-connected appointments.

This article describes how to set up and configure the Teams EHR connector to integrate with the Epic platform in your healthcare organization. It also gives you an overview of the Teams Virtual Appointments experience from the Epic EHR system.

<iframe src="https://learn-video.azurefd.net/vod/player?id=51442f11-3e9f-4699-896a-edad4f54fc3f" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>


Important

New customer onboarding is currently paused. Please reach out to TeamsForHealthcare@service.microsoft.com for further questions.

## Before you begin

Before you get started, there's a few things to do to prepare for the integration.

### Get familiar with the integration process

Review the following information to get an understanding of the overall integration process.

![Image summarizing the steps in the overall integration process.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-flow.png?view=o365-worldwide)

|  | Request app access | App enablement | Connector configuration | Epic configuration | Testing |
| --- | --- | --- | --- | --- | --- |
| **Duration** | Approximately 7 business days | Approximately 7 business days | Approximately 7 business days | Approximately 7 business days |  |
| **Action** | You [request access to the Teams application](#request-access-to-the-teams-app). | We create a public and private key certificate and upload them to Epic. | You complete configuration steps in the EHR connector configuration portal. | You work with your Epic technical specialist to configure FDI records in Epic. | You complete testing in your test environment. |
| **Outcome** | We authorize your organization for testing. | Epic syncs the public key certificate. | You receive FDI records for Epic configuration. | Configuration completed. Ready to test. | Full validation of flows and decision to move to production. |

### Request access to the Teams app

Important

New customer onboarding is currently paused. Please reach out to TeamsForHealthcare@service.microsoft.com for further questions.

You'll need to request access to the Teams application.

1. Request to download the Teams application in the [Epic Connection Hub](https://appmarket.epic.com/). Doing this triggers a request from Epic to the Microsoft EHR connector team.
2. Sign in to [EHR connector portal](https://ehrconnector.teams.microsoft.com/) and add your FHIR URL.
3. After you make your request and added FHIR URL, send an email to [TeamsForHealthcare@service.microsoft.com](mailto:teamsforhealthcare@service.microsoft.com) with your organization name, tenant ID, and the email address of your Epic technical contact.
4. The Microsoft EHR connector team will respond to your email with confirmation of enablement.

### Review the Epic-Microsoft Teams Telehealth Integration guide

Review the [Epic-Microsoft Teams Telehealth Integration Guide](https://galaxy.epic.com/Search/GetFile?Url=1!68!100!100100357) with your Epic technical specialist. Make sure that all prerequisites are met.

## Prerequisites

- An active subscription to Microsoft Cloud for Healthcare or a subscription to Microsoft Teams EHR connector standalone offer \(only enforced when testing in a production EHR environment\).
- Epic version November 2018 or later.
- Users have an appropriate Microsoft 365 or Office 365 license that includes Teams meetings.
- Teams is adopted and used in your healthcare organization.
- Identified a person in your organization who is a Microsoft 365 Global Administrator with access to the [Teams admin center](https://admin.teams.microsoft.com).
- Your systems meet all [software and browser requirements](https://learn.microsoft.com/en-us/microsoftteams/hardware-requirements-for-the-teams-app) for Teams.

Important

Make sure you complete the pre-integration steps and all prerequisites are met before you move forward with the integration.

The integration steps are performed by the following people in your organization:

- **Microsoft 365 Global Administrator**: The main person who is responsible for the integration. The admin configures the connector, enables SMS \(if needed\), and adds the Epic customer analyst who will be approving the configuration.
- **Epic customer analyst**: A person in your organization who has login credentials to Epic. They approve the configuration settings entered by the admin and provide the configuration records to Epic.

The Microsoft 365 admin and Epic customer analyst can be the same person.

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## Set up the Teams EHR connector

The connector setup requires that you:

- [Launch the EHR connector configuration portal](#launch-the-ehr-connector-configuration-portal)
- [Enter configuration information](#enter-configuration-information)
- [Approve or view the configuration](#approve-or-view-the-configuration)
- [Review and finish the configuration](#review-and-finish-the-configuration)

### Launch the EHR connector configuration portal

To get started, your Microsoft 365 admin launches the [EHR connector configuration portal](https://ehrconnector.teams.microsoft.com) and signs in using their Microsoft 365 credentials.

Your Microsoft 365 admin can configure a single organization or multiple organizations to test the integration. Configure the test and production URL in the configuration portal. Make sure to test the integration from the Epic test environment before moving to production.

Note

Your Microsoft 365 admin and Epic customer analyst must complete the integration steps in the configuration portal. For Epic configuration steps, contact the Epic technical specialist assigned to your organization.

### Enter configuration information

Next, to set up the integration, your Microsoft 365 admin completes following steps:

1. Adds a Fast Health Interoperability Resources \(FHIR\) base URL from your Epic technical specialist and specifies the environment. Configure as many FHIR base URLs as needed, depending on your organization's needs and the environments you want to test.

   - The FHIR base URL is a static address that corresponds to your server FHIR API endpoint. An example URL is `https://lamnahealthcare.com/fhir/auth/connect-ocurprd-oauth/api/FHDST`.
   - You can set up the integration for test and production environments. For initial setup, we encourage you to configure the connector from a test environment before moving to production.

2. Adds the username of the Epic customer analyst who will be approving the configuration in a later step.

   [![Screenshot of the Configuration page, showing the approver being added.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-configure.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-configure.png?view=o365-worldwide#lightbox)

### Approve or view the configuration

The Epic customer analyst in your organization who was added as approver launches the [EHR connector configuration portal](https://ehrconnector.teams.microsoft.com) and signs in using their Microsoft 365 credentials. After successful validation, the approver is asked to sign in using their Epic credentials to validate the Epic organization.

Note

If the Microsoft 365 admin and Epic customer analyst are the same person, you'll still need to sign in to Epic to validate your access. The Epic sign-in is used only to validate your FHIR base URL. Microsoft won't store credentials or access EHR data with this sign-in.

[![Screenshot of the Approve or View Configuration page, showing the Login and approve option.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-login-approve.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-login-approve.png?view=o365-worldwide#lightbox)

After successful sign-in to Epic, the Epic customer analyst **must** approve the configuration. If the configuration isn't correct, your Microsoft 365 admin can sign in to the configuration portal and change the settings.

[![Screenshot of the Approve or View Configuration page, showing the Approve option.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-approve.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-approve.png?view=o365-worldwide#lightbox)

### Review and finish the configuration

When the configuration information is approved by the Epic administrator, you'll be presented with integration records for patient and provider launch. The integration records include:

- Patient and provider records
- Direct SMS record
- SMS configuration record
- Device test configuration record

The context token for device test can be found in the patient integration record. The Epic customer analyst must provide these records to Epic to complete the virtual appointments configuration in Epic. For more information, see the [Epic-Microsoft Teams Telehealth Integration Guide](https://galaxy.epic.com/Search/GetFile?Url=1!68!100!100100357).

Note

At any time the Microsoft 365 or Epic customer analyst can sign in to the configuration portal to view integration records and change organization configuration, as needed.

[![Screenshot of the Review and Finish page, showing integration information.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-finish.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-connector-epic-finish.png?view=o365-worldwide#lightbox)

Note

The Epic customer analyst must complete the approval process for each FHIR base URL that's configured by the Microsoft 365 admin.

## Launch Teams Virtual Appointments

After completing the EHR connector steps and Epic configuration, your organization is ready to support video appointments with Teams.

### Virtual Appointments prerequisites

- Your systems must meet all [software and browser requirements](https://learn.microsoft.com/en-us/microsoftteams/hardware-requirements-for-the-teams-app) for Teams.
- You completed the integration setup between the Epic organization and your Microsoft 365 organization.

### Provider experience

Healthcare providers from your organization can join appointments using Teams from their Epic provider apps \(Hyperspace, Haiku, Canto\). The **Begin virtual visit** button is embedded in the provider flow.

![Provider experience of a virtual appointment with patient.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehc-provider-experience-6.png?view=o365-worldwide)

Key features of the provider experience:

- Providers can join appointments using supported browsers or the Teams application.
- Providers must do a one-time sign-in with their Microsoft 365 account when joining an appointment for the first time.
- After the one-time sign-in, the provider is taken directly to the virtual appointment in Teams. \(The provider must be signed in to Teams\).
- Providers can see real-time updates of participants connecting and disconnecting for a given appointment. Providers can see when the patient is connected to an appointment.

Note

Any information entered in the meeting chat that's necessary for medical records continuity or retention purposes should be downloaded, copied, and notated by the healthcare provider. The chat doesn't constitute a legal medical record or a designated record set. Messages from the chat are stored based on settings created by the Microsoft Teams admin.

### Patient experience

The connector supports patients joining appointments through a link in the SMS text message, MyChart web, and mobile. At the time of the appointment, patients can start the appointment from MyChart using the **Begin virtual visit** button or by tapping the link in the SMS text message.

![Patient experience of a virtual appointment.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehc-virtual-visit-5.png?view=o365-worldwide)

Key features of the patient experience:

- Patients can join appointments from [modern web browsers on desktop and mobile without having to install the Teams application](https://learn.microsoft.com/en-us/microsoft-365/frontline/browser-join?view=o365-worldwide).
- Patients can test their device hardware and connection before joining an appointment.

  [![Images of a mobile device, showing device test capabilities.](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-admin-epic-device-test.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/frontline/media/ehr-admin-epic-device-test.png?view=o365-worldwide#lightbox)

  Device test capabilities:

  - Patients can test their speaker, microphone, camera, and connection.
  - Patients can complete a test call to fully validate their configuration.
  - Results of the device test can be sent back to the EHR system.

- Patients can join appointments with a single click and no other account or sign-in is required.
- Patients aren't required to create a Microsoft account or sign in to launch an appointment.
- Patients are placed in a lobby until the provider joins and admits them.
- Patients can test their video and microphone in the lobby before they join the appointment.

Note

Epic, MyChart, Haiku, and Canto are trademarks of Epic Systems Corporation.

## Troubleshoot Teams EHR connector setup and integration

If you're experiencing issues when setting up the integration, see [Troubleshoot Teams EHR connector setup and configuration](https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-connector-troubleshoot-setup-configuration?view=o365-worldwide) for guidance on how to resolve common setup and configuration issues.

## Get insight into Virtual Appointments usage

The [EHR connector Virtual Appointments report](https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-connector-report?view=o365-worldwide) in the Teams admin center gives you an overview of EHR-integrated virtual appointment activity in your organization. You can view a breakdown of data for each appointment that took place for a given date range. The data includes the staff member who conducted the appointment, duration, the number of attendees, department, and whether the appointment was within the allocation limit.

### Privacy and location of data

Teams integration into EHR systems optimizes the amount of data used and stored during integration and virtual appointment flows. The solution follows the overall Teams privacy and data management principles and guidelines outlined in Teams Privacy.

The Teams EHR connector doesn't store or transfer any identifiable personal data or any health records of patients or healthcare providers from the EHR system. The only data stored by the EHR connector is the EHR user's unique ID, which is used during Teams meeting setup.

The EHR user's unique ID is stored in one of the three geographic regions described in [Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-services-data-location). All chat, recordings, and other data shared in Teams by meeting participants are stored according to existing storage policies. To learn more about the location of data in Teams, see [Location of data in Teams](https://learn.microsoft.com/en-us/microsoftteams/location-of-data-in-teams).

## Related articles

- [Teams Virtual Appointments usage report](https://learn.microsoft.com/en-us/microsoft-365/frontline/virtual-appointments-usage-report?view=o365-worldwide)
- [Teams EHR connector Virtual Appointments report](https://learn.microsoft.com/en-us/microsoft-365/frontline/ehr-connector-report?view=o365-worldwide)
- [Get started with Teams for healthcare organizations](https://learn.microsoft.com/en-us/microsoft-365/frontline/teams-in-hc?view=o365-worldwide)
