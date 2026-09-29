<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/use-case-admin-quarantine -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Tutorial: Protect files with admin quarantine

Important

File policies retire on January 6, 2027. To maintain file-based data protection, [migrate to Microsoft Purview DLP or auto-labeling policies](https://learn.microsoft.com/en-us/defender-cloud-apps/migrate-file-policies-to-purview).

[File policies](https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies) are a great tool for finding threats to your information protection policies. For instance, create file policies that find places where users stored sensitive information, credit card numbers, and third-party ICAP files in your cloud.

In this tutorial, you'll learn how to use Microsoft Defender for Cloud Apps to detect unwanted files stored in your cloud that leave you vulnerable, and take immediate action to stop them in their tracks and lock down the files that pose a threat by using **Admin quarantine** to protect your files in the cloud, remediate problems, and prevent future leaks from occurring.

- [Understand how quarantine works](#understand-how-quarantine-works)
- [Set up admin quarantine](#set-up-admin-quarantine)

## Understand how quarantine works

Note

- For a list of apps that support admin quarantine, see the list of [governance actions](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-actions).
- Files labeled by Defender for Cloud Apps can't be quarantined.
- Defender for Cloud Apps admin quarantine actions is limited to 100 actions per day.
- Sharepoint sites that are renamed either directly or as part of domain rename can't be used as a folder location for admin quarantine.

1. When a file matches a policy, the **Admin quarantine** option is available for the file.
2. Set an automated quarantine action in the policy.

   [![quarantine automatically.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-automated.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-automated.png#lightbox)
3. When **Admin quarantine** is applied, the following things occur behind the scenes:

   1. The original file is moved to the admin quarantine folder you set.
   2. The original file is deleted.
   3. A tombstone file is uploaded to the original file location.

      ![quarantine tombstone.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-tombstone.png)
   4. The user can only access the tombstone file. In the file, they can read the custom guidelines provided by IT and the correlation ID to give IT to release the file.

4. When you receive the alert that a file has been quarantined, go to **Policies** -> **Policy Management**. Then select the **Information Protection** tab. In the row with your file policy, choose the three dots at the end of the line, and select **View all matches**. This brings you the report of matches, where you can see the matching and quarantined files:

   [![Quarantined files.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-alerts.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-alerts.png#lightbox)
5. After a file is quarantined, use the following process to remediate the threat situation:

   1. Inspect the file in the quarantined folder on SharePoint online.
   2. You can also look at the audit logs to deep dive into the file properties.
   3. If you find the file is against corporate policy, run the organization's Incident Response \(IR\) process.
   4. If you find that the file is harmless, you can restore the file from quarantine. At that point the original file is released, and copied back to the original location. The tombstone is deleted, and the user can access the file.

      ![quarantine restore.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-restore.png)

6. Validate that the policy runs smoothly. Then, you can use the automatic governance actions in the policy to prevent further leaks and automatically apply an Admin quarantine when the policy is matched.

Note

When you restore a file:

- Original shares aren't restored, default folder inheritance applied.
- The restored file contains only the most recent version.
- The quarantine folder site access management is the customer's responsibility.

## Set up admin quarantine

1. Set file policies that detect breaches. Examples of these types of policies include:

   - A metadata only policy such as a sensitivity label in SharePoint Online
   - A native data loss prevention \(DLP\) policy such as a policy that searches for credit card numbers
   - An ICAP third-party policy such as a policy that looks for Vontu

2. Set a quarantine location:

   1. For Microsoft 365 SharePoint or OneDrive for Business, you can't put files in admin quarantine as part of a policy until you set it up:

      ![quarantine warning.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-warning.png)

      To set admin quarantine settings, in the Microsoft Defender Portal, select **Settings**. Then choose **Cloud Apps**. Under **Information Protection**, choose **Admin quarantine**. Provide a site for the quarantine folder location and a user notification that your user will receive when their file is quarantined.

      [![quarantine settings.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-settings.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/quarantine-settings.png#lightbox)

      Note

      Defender for Cloud Apps creates a quarantine folder on the selected site.
   2. For Box, the quarantine folder location and user message can't be customized. The folder location is the drive of the admin who connected Box to Defender for Cloud Apps and the user message is: This file was quarantined to your administrator's drive because it might violate your company's security and compliance policies. Contact your IT administrator for help.

## Next steps

[Best practices for protecting your organization](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
