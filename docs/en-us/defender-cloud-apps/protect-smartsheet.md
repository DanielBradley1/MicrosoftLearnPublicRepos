<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-smartsheet -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# How Defender for Cloud Apps helps protect your Smartsheet environment

As a productivity and collaboration cloud solution, Smartsheet holds sensitive information to your organization. Any abuse of Smartsheet by a malicious actor or any human error may expose your most critical assets and services to potential attacks.

Connecting Smartsheet to Defender for Cloud Apps gives you improved insights into your Smartsheet activities and provides threat detection for anomalous behavior.

## Main threats to your Smartsheet environment

Connecting Smartsheet to Defender for Cloud Apps helps you address threats such as:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## How Defender for Cloud Apps helps to protect your environment

Use the following best practices to help protect your environment:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## Control Smartsheet with policies

The following policies can help you monitor and control Smartsheet:

| **Type** | **Name** |
| --- | --- |
| Built-in anomaly detection policy | [Unusual file share activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual file deletion activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual administrative activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user)  <br>[Unusual multiple file download activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |
| Activity policy | Build a customized policy by the Smartsheet [Audit Log](https://smartsheet.redoc.ly/tag/eventsObjects) activities |

Note

- Login/Logouts activities are not supported by Smartsheet.
- Smartsheet activities does not contain IP addresses.

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can automate the following Smartsheet governance actions in Defender for Cloud Apps to fix detected threats:

| **Type** | **Action** |
| --- | --- |
| User governance | Notify user on alert \(via Microsoft Entra ID\)  <br>Require user to sign in again \(via Microsoft Entra ID\)  <br>Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect Smartsheet in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect Smartsheet to Microsoft Defender for Cloud Apps

The following instructions describe how to connect Microsoft Defender for Cloud Apps to your existing Smartsheet via the App Connector APIs. The resulting connection gives you visibility into and control over your organization's use of Smartsheet.

### Prerequisites

Before you connect Smartsheet, make sure the following prerequisites are met:

- You must have a Smartsheet license that is part of an Enterprise plan with the Platinum package.
- The Smartsheet user used to log in to Smartsheet must be a System Admin.
- Event Reporting must be enabled by Smartsheet, either through standalone purchase or via an Enterprise plan with the Advance Platinum package.
- Smartsheet accounts must be in the **smartsheet.com** domain. These domains are not currently supported:

  - smartsheet.au
  - smartsheet.eu
  - smartsheetgov.com

### Configure Smartsheet

1. Register to add Developer Tools to your existing Smartsheet account:

   1. Go to the [Developer Sandbox Account Registration](https://developers.smartsheet.com/register/) page.
   2. Enter your Smartsheet email address in the text box:

      ![Screenshot of the Developer Sandbox Account Registration page with the email address text box for registering developer tools.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/smartsheet-register-to-developer-tools.png)

   3. An activation mail will appear in your mailbox. Activate Developer Tools by using the activation mail.
   4. In Smartsheet, select **Create Developer Profile**. Enter your name and email address. Select **Save** and then **Close**:

      ![Screenshot of the Create Developer Profile form with fields for entering your name and email address.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/smartsheet-create-developer-tools.png)

2. In Smartsheet, select **Developer Tools**:

   ![Screenshot of the Smartsheet menu with the Developer Tools option selected.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/smartsheet-entering-developer-tools.png)

3. In the **Developer Tools** dialog, select **Create New App**:

   ![Screenshot of the Developer Tools page with the Create New App option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/smartsheet-developer-tools.png)

4. In the **Create New App** dialog, provide the following values:

   - **App name**: For example, **Microsoft Defender for Cloud Apps**.
   - **App description**: For example, **Microsoft Defender for Cloud Apps connects to Smartsheet via its API and detects threats within users' activity.**
   - **App URL**: `https://portal.cloudappsecurity.com`
   - **App contact/support**: `https://learn.microsoft.com/cloud-app-security/support-and-ts`
   - **App redirect URL**: `https://portal.cloudappsecurity.com/api/oauth/saga`
   - **Publish App?**: Select.
   - **Logo**: Leave blank.

     ![Screenshot of the Create New App dialog for entering OAuth app details such as app name, description, and redirect URL.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/smartsheet-oauth-app-creation.png)

5. Select **Save**. Copy the **App client id** and the **App secret** that are generated. You'll need these values when you configure Defender for Cloud Apps.

### Configure Defender for Cloud Apps

Note

The Smartsheet user configuring the integration must always remain a Smartsheet admin, even after the connector is installed.

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. On the **App connectors** tab, select **+Connect an app**, and then select **Smartsheet**.
3. In the next window, give the connector a descriptive name, and then select **Next**.

   ![Screenshot of the app connector dialog with the Connect Smartsheet option selected.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-smartsheet.png)

4. On the **Enter details** screen, enter these values and select **Next**:

   - **Client ID**: The app client ID that you saved earlier.
   - **Client Secret**: The app secret that you saved earlier.

5. On the **External Link** page, select **Connect Smartsheet**.
6. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.
7. The first connection can take up to four hours to get all users and their activities in the seven days before the connection.
8. After the connector's **Status** is marked as **Connected**, the connector is live and works.

## Rate limits and limitations

The default rate limit is 300 requests per minute. For more information, see the [Smartsheet documentation](https://smartsheet.redoc.ly/#section/Work-at-Scale/Rate-Limiting).

Limitations include:

- Log in and log out activities aren't supported by Smartsheet.
- Smartsheet activities don't contain IP addresses.
- System activities are shown with the Smartsheet account name.

## Next steps

[Control cloud apps by using policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
