<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/protect-servicenow -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# How Defender for Cloud Apps helps protect your ServiceNow environment

ServiceNow is a major CRM cloud provider. It stores sensitive data about customers, internal processes, incidents, and reports. As a business-critical app, people both inside and outside your organization use it, including partners and contractors. Many of these users might not follow security best practices. They could share sensitive data without meaning to. Malicious actors might also try to access your most sensitive customer assets.

Connecting ServiceNow to Defender for Cloud Apps improves insights into your users' activities. It also helps detect threats using machine-learning anomaly detection and information protection, such as identifying when sensitive customer data is uploaded to ServiceNow.

Use this app connector to access SaaS Security Posture Management \(SSPM\) features, via security controls reflected in Microsoft Secure Score. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score).

## Main threats

Connecting ServiceNow to Defender for Cloud Apps helps you address the following threats:

- Compromised accounts and insider threats
- Data leakage
- Insufficient security awareness
- Unmanaged bring your own device \(BYOD\)

## Protect your environment with Defender for Cloud Apps

You can protect your ServiceNow environment in these ways:

- [Detect cloud threats, compromised accounts, and malicious insiders](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#detect-cloud-threats-compromised-accounts-malicious-insiders-and-ransomware)
- [Discover, classify, label, and protect regulated and sensitive data stored in the cloud](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)
- [Enforce DLP and compliance policies for data stored in the cloud](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#enforce-dlp-and-compliance-policies-for-data-stored-in-the-cloud)
- [Limit exposure of shared data and enforce collaboration policies](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#limit-exposure-of-shared-data-and-enforce-collaboration-policies)
- [Use the audit trail of activities for forensic investigations](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#use-the-audit-trail-of-activities-for-forensic-investigations)

## SaaS security posture management for ServiceNow

Connect ServiceNow to Microsoft Defender for Cloud Apps to get security tips for ServiceNow in Microsoft Secure Score.

In Secure Score, select **Recommended actions**. Filter by **Product** = **ServiceNow**. Examples include:

- *Enable MFA*
- *Activate the explicit role plugin*
- *Enable high security plugin*
- *Enable script request authorization*

For more information, see:

- [Security posture management for SaaS apps](https://learn.microsoft.com/en-us/defender-cloud-apps/security-saas)
- [Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)

## Control ServiceNow with built-in policies and policy templates

You can use the following built-in policy templates to detect and notify you about potential threats:

Important

File policies retire on January 6, 2027. To maintain file-based data protection for this app, [migrate to Microsoft Purview DLP or auto-labeling policies](https://learn.microsoft.com/en-us/defender-cloud-apps/migrate-file-policies-to-purview).

| Type | Name |
| --- | --- |
| Built-in anomaly detection policy | [Activity from anonymous IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-anonymous-ip-addresses)  <br>[Activity from infrequent country](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-infrequent-country)  <br> |
| [Activity from suspicious IP addresses](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-from-suspicious-ip-addresses)  <br>[Impossible travel](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#impossible-travel)  <br>[Activity performed by terminated user](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#activity-performed-by-terminated-user) \(requires Microsoft Entra ID as IdP\)  <br>[Multiple failed login attempts](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#multiple-failed-login-attempts)  <br>[Ransomware detection](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#ransomware-activity)  <br>[Unusual multiple file download activities](https://learn.microsoft.com/en-us/defender-cloud-apps/anomaly-detection-policy#unusual-activities-by-user) |  |
| Activity policy template | Logon from a risky IP address  <br>Mass download by a single user |
| File policy template | Detect a file shared with an unauthorized domain  <br>Detect a file shared with personal email addresses  <br>Detect files with PII/PCI/PHI |

For more information about creating policies, see [Create a policy](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies#create-a-policy).

## Automate governance controls

You can also automate ServiceNow governance actions to fix detected threats. These actions run through Microsoft Entra ID:

| Type | Action |
| --- | --- |
| User governance | - Notify user on alert \(via Microsoft Entra ID\)  <br>- Require user to sign in again \(via Microsoft Entra ID\)  <br>- Suspend user \(via Microsoft Entra ID\) |

For more information about remediating threats from apps, see [Governing connected apps](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).

## Protect ServiceNow in real time

Review our best practices for [securing and collaborating with external users](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#secure-collaboration-with-external-users-by-enforcing-real-time-session-controls) and [blocking and protecting the download of sensitive data to unmanaged or risky devices](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices#block-and-protect-download-of-sensitive-data-to-unmanaged-or-risky-devices).

## Connect ServiceNow to Microsoft Defender for Cloud Apps

Use the app connector API to connect Microsoft Defender for Cloud Apps to your existing ServiceNow account. The ServiceNow app connector gives you visibility into and control over ServiceNow use. For threat detection, governance controls, and real-time protection guidance, see [Protect ServiceNow](https://learn.microsoft.com/en-us/defender-cloud-apps/protect-servicenow).

Use this app connector to access SaaS Security Posture Management \(SSPM\) features, via security controls reflected in Microsoft Secure Score. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score).

### Prerequisites

- In order to connect ServiceNow with Defender for Cloud Apps,
- Your ServiceNow instance must support API access.
- You must have an admin role.
- The admin account used to make the connection must have permissions to use the API.

Defender for Cloud Apps supports the following ServiceNow versions:

- Eureka
- Fiji
- Geneva
- Helsinki
- Istanbul
- Jakarta
- Kingston
- London
- Madrid
- New York
- Orlando
- Paris
- Quebec
- Rome
- San Diego
- Tokyo
- Utah
- Vancouver
- Washington
- Xanadu
- Yokohama
- Zurich
- Australia

For more information, see [ServiceNow OAuth applications documentation](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/security/concept/c_OAuthApplications.html#c_OAuthApplications).

Tip

We recommend deploying ServiceNow using OAuth app tokens, available for Fuji and later releases. For more information, see [Configure OAuth applications in ServiceNow](https://docs.servicenow.com/bundle/paris-platform-administration/page/administer/security/concept/c_OAuthApplications.html#c_OAuthApplications).

For earlier releases, a [legacy connection mode](#legacy-servicenow-connection) is used that uses usernames and passwords The username and password provided are only used for API token generation and aren't saved after the initial connection process.

### How to connect ServiceNow to Defender for Cloud Apps using OAuth

Perform the following steps to create an OAuth profile in ServiceNow and connect it to Defender for Cloud Apps:

1. Sign in with an Admin account to your ServiceNow account.

   Note

   For earlier releases, a [legacy connection mode](#legacy-servicenow-connection) is available based on user/password. The username/password provided are only used for API token generation and aren't saved after the initial connection process.
2. Create a new OAuth profile and then select **Create an OAuth API endpoint for external clients**.
3. Fill in the following **Application Registries New record** fields:

   1. Enter a name for your OAuth profile, for example, CloudAppSecurity.
   2. Copy the **Client ID**. You'll need it later.
   3. In the **Client Secret** field, enter a string. If left empty, a random secret is generated automatically. Copy and save it for later.
   4. Increase the **Access Token Lifespan** to at least 3,600.
   5. Change the **Scope Restriction** value to **Broadly Scoped**.

4. Select the name of the OAuth that was defined, and change the **Refresh Token Lifespan** to **7,776,000 seconds** \(90 days\).
5. Establish an internal procedure to ensure that the connection remains active.

   1. Make sure to revoke the old refresh token before the expected expiration of the refresh token.
   2. In the Microsoft Defender Portal, edit the existing connector, using the same client ID and client secret. This will generate a new refresh token.


   Note


   Token rotation is a recurring process every 90 days. Without refreshing the token before expiration, the ServiceNow connection will stop working.

### Connect ServiceNow to Microsoft Defender for Cloud Apps

To complete the connection in the Microsoft Defender Portal, follow these steps:

1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**.
2. In the **App connectors** page, select **+Connect an app**, and then **ServiceNow**.

   ![Screenshot that shows where to find the ServiceNow connector in the Defender portal.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/connect-servicenow.png)
3. In the next window, give the connection a name and select **Next**.
4. In the **Enter details** page, select **Connect using OAuth token \(recommended\)**. Select **Next**.

   ![Screenshot of the ServiceNow App Connector Details Dialog.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/servicenow-app-connector-details-screenshot.png)
5. To find your ServiceNow user name, in the ServiceNow portal, go to **Users** and then locate your name in the table. \(Optional\) To use a non-admin user for this step, create a non-admin user by following the steps in the below section.
6. In the **OAuth Details** page, enter your **Client ID** and **Client Secret**. Select **Next**.
7. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Connected apps**, select **App Connectors**. Make sure the status of the connected App Connector is **Connected**.

After connecting ServiceNow, you'll receive events for 1 hour prior to connection.

### Optional: Create a non-admin user in ServiceNow

#### Step 1: Create custom access control lists \(ACLs\) in ServiceNow

1. Sign in to ServiceNow with an administrator account.
2. Open the **Elevate Roles** menu and enable both **admin** and **security\_admin**. These elevated roles are required to create ACLs for certain tables.
3. Navigate to **Access Control \(ACL\)** configuration.
4. Create a **Read** ACL for each of the following tables:

   - sys\_user
   - sys\_user\_group
   - sys\_user\_grmember
   - sys\_user\_has\_role
   - sys\_properties
   - v\_plugin
   - sysevent\_script\_action
   - sys\_attachment
   - sys\_attachment\_doc
   - sysevent
   - syslog\_transaction
   - incident
   - sys\_user\_role\_contains

5. For each ACL, set **Type** = **record**, **Operation** = **read**, **Name** = the table name, and **Required Role** = a custom role such as **custom\_table\_access**.
6. Use the same custom role across all ACLs to simplify management.

#### Step 2: Create a non-admin user

1. In ServiceNow, go to **User Administration** > **Users**.
2. Create a new user account.
3. Record the username and password for later use in the integration setup.
4. Open the newly created user profile.
5. Scroll to the **Roles** section.
6. Assign the custom role created in Step 1 \(for example, **custom\_table\_access**\) to the user.

### Legacy ServiceNow connection

To connect ServiceNow with Defender for Cloud Apps, you must have admin-level permissions and make sure the ServiceNow instance supports API access.

1. Sign in with an Admin account to your ServiceNow account.
2. Create a new service account for Defender for Cloud Apps and attach the Admin role to the newly created account.
3. Make sure the REST API plug-in is turned on.

## Next steps

- If you have any problems connecting the app, see [Troubleshooting App Connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-api-connectors-using-error-messages).
- [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)
