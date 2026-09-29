<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/tutorial-proxy -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Tutorial: Protect any apps in use in your organization in real time

The apps you sanction employees to use, often store some of your most sensitive corporate data and secrets. In the modern workplace, users access these apps in many risky situations. These users could be partners in your organization over who you have little visibility, or employees using unmanaged devices or coming from public IP addresses. Due to the wide range of risks in this landscape, a zero-trust strategy must be employed. Often, it's not enough to know about breaches and data loss in these apps after the fact; therefore, many information protection and cyberthreat scenarios must be addressed or prevented in real time.

In this tutorial, you'll learn how to use access and session controls to monitor and control access to apps and their data. Adaptively managing access to your data and mitigating against threats allows Defender for Cloud Apps to protect your most sensitive assets. Specifically, we'll cover the following scenarios:

- [Monitor user activities for anomalies](#phase-1-monitor-user-activities-for-anomalies)
- [Protect your data when it's exfiltrated](#phase-2-protect-your-data-when-its-exfiltrated)
- [Prevent unprotected data from being uploaded to your apps](#phase-3-prevent-unprotected-data-from-being-uploaded-to-your-apps)

## How to protect your organization from any app in real time

Use this process to roll out real-time controls in your organization.

### Phase 1: Monitor user activities for anomalies

Microsoft Entra ID apps are automatically deployed for Conditional Access app control, and are monitored in real time for immediate insights into their activities and related information. Use this information to identify anomalous behavior.

Use the Defender for Cloud Apps' [Activity Log](https://learn.microsoft.com/en-us/defender-cloud-apps/activity-filters) to monitor and characterize app use in your environment, and understand their risks. Narrow the scope of activities listed by using [search, filters, and queries](https://learn.microsoft.com/en-us/defender-cloud-apps/activity-filters-queries) to quickly identify risky activities.

### Phase 2: Protect your data when it's exfiltrated

A primary concern for many organizations is how to prevent data exfiltration before it happens. Two of the biggest risks are unmanaged devices \(that may not be protected with a pin or may contain malicious apps\) and guest users where your IT department has little visibility and control.

Now that your apps are deployed, you can easily configure policies to mitigate both of these risks by leveraging our native integrations with Microsoft Intune for device management, Microsoft Entra ID for user groups, and Microsoft Purview Information Protection for data protection.

- **Mitigate unmanaged devices**: Create a [session policy to label](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad#create-a-defender-for-cloud-apps-session-policy) and protect highly confidential files meant for users in your organization only.
- **Mitigate guest users**: Create a [session policy to apply custom permissions](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad#protect-download) to any file that is downloaded by guest users. For example, you can set permissions so that guest users can only access a protected file.

### Phase 3: Prevent unprotected data from being uploaded to your apps

In addition to preventing data exfiltration, organizations often want to make sure that data that is infiltrated to cloud apps is also secure. A common use case is when a user attempts to upload files that are not labeled correctly.

For any of the apps you've configured above, you can configure a session policy to prevent the upload of files that are not labeled correctly, as follows:

1. Create a session policy to [block uploads of incorrectly labeled files](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad#protect-upload).
2. Configure a policy to display a [block message with instructions on how to correct the label and try again](https://learn.microsoft.com/en-us/defender-cloud-apps/session-policy-aad#educate-users-to-protect-sensitive-files).

Protecting file uploads in this way ensures that data saved to the cloud has the correct access permissions applied. In the event that a file is shared or lost, it can only be accessed by authorized users.

## Learn more

- Try our interactive guide: [Protect and control information with Microsoft Defender for Cloud Apps](https://mslearn.cloudguides.com/guides/Protect%20and%20control%20information%20with%20Microsoft%20Cloud%20App%20Security)
