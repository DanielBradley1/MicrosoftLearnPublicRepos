<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/cloud-discovery-anonymizer -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Cloud discovery data anonymization

Cloud discovery data anonymization enables you to protect user privacy. Once the data log is uploaded to Microsoft Defender for Cloud Apps, the log is sanitized and all username information is replaced with encrypted usernames. By replacing usernames with encrypted values, all cloud activities are kept anonymous. When necessary, for a specific security investigation \(for example, a security breach or suspicious user activity\), admins can resolve the real username. If an admin has a reason to suspect a specific user, they can also look up the encrypted username of a known username, and then start investigating using the encrypted username. Each username conversion is audited in the portal's **Governance log**.

Key points:

- No private information is stored or displayed. Only encrypted information.
- Private data is encrypted using AES-128 with a dedicated key per tenant.
- Resolving usernames is done ad-hoc, per-username by deciphering a given encrypted username.
- Anonymization capabilities aren't supported when using the "Defender for Cloud Apps Proxy" stream.
- As Microsoft Defender moves toward a fully unified identity platform, some Defender for Cloud Apps data pipelines remain separate. Cloud discovery data anonymization uses a separate data pipeline that isn't yet integrated with the [Identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory). Correlations defined in the Identity inventory don't affect anonymization. For a full list of affected features, see [Enable Identity inventory integration](https://learn.microsoft.com/en-us/defender-cloud-apps/general-setup#enable-identity-inventory-integration).

## Prerequisites

To resolve \(deanonymize\) usernames in Cloud Discovery data:

- You must have the [Cloud Discovery global admin](https://learn.microsoft.com/en-us/defender-cloud-apps/manage-admins#built-in-admin-roles-in-defender-for-cloud-apps) role with anonymization permissions enabled during role assignment.

Note

Microsoft recommends that you use roles with the fewest permissions. Using roles with the fewest permissions helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## How data anonymization works

1. There are three ways to apply data anonymization:

   - You can set the data from a specific log file to be anonymized, by selecting **Anonymize private information** when you [create a snapshot cloud discovery report](https://learn.microsoft.com/en-us/defender-cloud-apps/create-snapshot-cloud-discovery-reports). Select **Anonymize private information**.  
     ![Screenshot of the option to anonymize private information when creating a snapshot report.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-log.png)
   - You can anonymize data from a new data source by selecting **Anonymize private information** when you [set up an automated log upload](https://learn.microsoft.com/en-us/defender-cloud-apps/discovery-docker).  
     ![Screenshot of the option to anonymize private information for an automated data source upload.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-autolog.png)
   - You can set the default in Defender for Cloud Apps to anonymize all data from both snapshot reports from uploaded log files and continuous reports from log collectors as follows:

     1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**.
     2. Under **Cloud Discovery**, select **Anonymization**. To anonymize usernames by default, select **Anonymize private information by default in new reports and data sources**. You can also select **Anonymize device information by default in 'Defender-managed endpoints' report**.

2. When anonymization is selected, Defender for Cloud Apps parses the traffic log and extracts specific data attributes.
3. Defender for Cloud Apps replaces the username with an encrypted username.
4. Defender for Cloud Apps then analyzes cloud usage data and generates cloud discovery reports based on the anonymized data.

   ![Screenshot of the cloud discovery dashboard displaying anonymized usage data.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-dashboard.png)

5. For a specific investigation, such as an investigation of an anomalous usage alert, you can resolve the specific username in the portal and provide a business justification.

   Note

   The following steps also work for device names on the **Devices** tab.

   **To resolve a single username**:

   1. Select the three dots at the end of the row of the user you want to resolve and select **Deanonymize user**.

      ![Screenshot of the user table with the Deanonymize user option selected.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-user-table.png)

   2. In the pop-up, enter the justification for resolving the username and then select **Resolve**. In the relevant row, the resolved username is displayed.

      Note

      Resolving a username is audited.

      ![Screenshot of the Resolve dialog where a business justification is entered before selecting Resolve.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-resolve-dialog.png)


   You can also use the Anonymization settings page to resolve a single username or look up the encrypted username of a known username.


   1. In the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**.
   2. Under **Cloud Discovery**, select **Anonymization**. Then, under **Anonymize and resolve usernames** enter a justification for why you're doing the resolution.
   3. Under **Enter username to resolve**, select **From anonymized** and enter the anonymized username, or select **To anonymized** and enter the original username to resolve. Select **Resolve**.

      ![Screenshot of the Resolve anonymization dialog for entering a username and confirming a deanonymization request.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymizer.png)


   **To resolve multiple usernames**:


   1. Either select the checkboxes that appear when you hover over the user icons by the users you want to resolve or, in the top-left, corner select the **Bulk selection** checkbox.

      ![Screenshot of the bulk selection checkboxes for resolving multiple anonymized users.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-bulk-resolve.png)

   2. Select **Deanonymize user**.
   3. In the pop-up, enter the justification for resolving the username and then select **Resolve**. In the relevant rows, the resolved usernames are displayed.

      Note

      Bulk username resolution is audited.

      ![Screenshot of the resolve dialog prompting for justification before deanonymizing multiple users.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/anonymize-resolve-dialog.png)

6. Each username resolution action is audited in the portal's **Audit log**.

Note

Starting October, 2025 - **Resolve Anonymization** actions are no longer part of **Governance logs**. Instead, they will be audited in the **Activity log** only.

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
