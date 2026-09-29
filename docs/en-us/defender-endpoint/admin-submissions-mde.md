<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/admin-submissions-mde -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Submit files in Microsoft Defender for Endpoint

In Microsoft Defender for Endpoint, admins can use the unified submissions feature to submit files and file hashes \(SHAs\) to Microsoft for review. The unified submissions experience is a one-stop shop for submitting emails, URLs, email attachments, and files in one, easy-to-use submission experience. Admins can use the Microsoft Defender portal or the Microsoft Defender for Endpoint Alert page to submit suspicious files.

## What do you need to know before you begin?

The new unified submissions experience is available in subscriptions that include Microsoft Defender XDR or Microsoft Defender for Endpoint Plan 2. You need to assign permissions before you can perform the procedures in this article. Use one of the following options:

**Microsoft Defender for Endpoint** permissions:

- Submit files / file hashes: *"Alerts investigation" or "Manage security settings in Security Center"*
- View submissions: "*View Data - Security operations"*

**Microsoft Defender unified RBAC** permissions:

- Submit files / file hashes: *"Alerts \(Manage\)" or "Core security settings \(manage\)"*
- View submissions: *"Security data basics \(read\)"*

For more information about how you can submit spam, phish, URLs, and email attachments to Microsoft, see [Use the Submissions page to submit suspected spam, phish, URLs, legitimate email getting blocked, and email attachments to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin).

## Submit a file or file hash to Microsoft from the Defender portal

Use the following steps to submit a file or file hash to Microsoft from the Submissions page in the Defender portal.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Investigation & response** > **Actions & submissions** > **Submissions**. Or, to go directly to the **Submissions** page, use [https://security.microsoft.com/reportsubmission](https://security.microsoft.com/reportsubmission).
2. On the **Submissions** page, select the **Files** tab.
3. On the **Files** tab, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-create.png) **Add new submission**.
4. ![Screenshot showing how to add a new submission.](https://learn.microsoft.com/en-us/defender/media/unified-admin-submission-new.png)
5. In the **Submit items to Microsoft for review** flyout that opens, select **Files** or **File hash** from the **Select the submission type** dropdown list.

   - If you selected **Files**, configure the following options:

     - Select **Browse files**. In the dialog that opens, find and select the file, and then select **Open**. Repeat this step as many times as necessary. To remove an entry from the flyout, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-close.png) next to the entry.

       - The maximum total size of all files is 500 MB.
       - Use the password 'infected' to encrypt archive files.

     - **The file should have been categorized as**: Select one of the following values:

       - **Malware** \(false negative\)
       - **Unwanted software**
       - **Clean** \(false positive\)

     - **Choose the priority**: Select one of the following values:

       - **Low - bulk file or file hash submission**
       - **Medium - standard submission**
       - **High - needs immediate attention** \(max three per day\)

     - **Notes for Microsoft \(optional\)**: Enter an optional note.
     - **Share feedback and relevant content with Microsoft**: Read the privacy statement and then select this option.


     ![Screenshot showing how to submit files.](https://learn.microsoft.com/en-us/defender/media/unified-admin-submission-file.png)

   - If you selected **File hash**, configure the following options:

     - In the empty box, enter the file hash value \(for example, `2725eb73741e23a254404cc6b5a54d9511b9923be2045056075542ca1bfbf3fe`\) and then press the ENTER key. Repeat this step as many times as necessary. To remove an entry from the flyout, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-close.png) next to the entry.
     - **The file should have been categorized as**: Select one of the following values:

       - **Malware** \(false negative\)
       - **Unwanted software**
       - **Clean** \(false positive\)

     - **Notes for Microsoft \(optional\)**: Enter an optional note.
     - **Share feedback and relevant content with Microsoft**: Read the privacy statement and then select this option.


     ![Screenshot showing how to submit files hashes.](https://learn.microsoft.com/en-us/defender/media/unified-admin-submission-file-hash.png)


   When you're finished in the **Submit items to Microsoft for review** flyout, select **Submit**.

Back on the **Files** tab of the **Submissions** page, the submission is shown.

To view the details of the submission, select the submission by clicking anywhere in the row other than the check box next to the **Submission name**. The details of the submission are in the details flyout that opens.

## Report items to Microsoft from the Alerts page in the Defender portal

Use the following steps to report items to Microsoft from the Alerts page in the Defender portal.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Investigation & response** > **Incidents & alerts** > **Alerts**. Or, to go directly to the **Alerts** page, use [https://security.microsoft.com/alerts](https://security.microsoft.com/alerts).
2. On the **Alerts** page, find the alert that contains the file you want to report. For example, you can select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-filter.png) **Filter**, and then select **Service/detection sources** > **Microsoft Defender for Endpoint**.
3. Select the alert from the list by clicking anywhere in the row other than the check box next to the **Alert name** value.
4. In the details flyout that opens, select ![](https://learn.microsoft.com/en-us/defender-endpoint/media/defender-portal-icon-more-actions.png) > **Submit items to Microsoft for review**.

   a.  ![Screenshot showing how to submit items from an alerts queue.](https://learn.microsoft.com/en-us/defender/media/unified-admin-submission-alerts-queue.png)
5. The options that are available in the **Submit items to Microsoft for review** flyout that opens are the same as described in [Submit a file or file hash to Microsoft from the Defender portal](#submit-a-file-or-file-hash-to-microsoft-from-the-defender-portal).

   The only difference is an **Include alert story** option that you can select to attach a JSON file that helps Microsoft investigate the submission.

   ![Screenshot showing how to specify a submission type and fill in required fields.](https://learn.microsoft.com/en-us/defender/media/unified-admin-submission-alert-queue-flyout.png)

   When you're finished in the **Submit items to Microsoft for review** flyout, select **Submit**.

The submission is available on the **Files** tab of the **Submissions** page at [https://security.microsoft.com/reportsubmission?viewid=file](https://security.microsoft.com/reportsubmission?viewid=file).

## Related content

- [Exclusions for Microsoft Defender for Endpoint and Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-overview)
- [Microsoft Defender for Endpoint in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-security-center-mde)
- [Address false positives/negatives](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-false-positives-negatives)
- [View and organize alerts queue in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue)
