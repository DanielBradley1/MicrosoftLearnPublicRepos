<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-automation-file-uploads -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Manage automation file uploads in Microsoft Defender for Endpoint

Enable the content analysis capability so that certain files and email attachments can automatically be uploaded to the cloud for additional inspection in Automated investigation.

Microsoft uses cloud-based file inspection mechanisms to inspect and analyze files.

Identify the files and email attachments by specifying the file extension names and email attachment extension names.

For example, if you add *exe* and *bat* as file or attachment extension names, then all files or attachments with those extensions will automatically be sent to the cloud for additional inspection during Automated investigation.

Note

Microsoft securely stores the files submitted for a six-month period. Files are promptly deleted after six months.

## Add file extension names and attachment extension names

Use the following steps to add file extension names and attachment extension names for automated investigation.

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. Sign in to the [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) using an account with the Security administrator or Global administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **Rules** > **Automation uploads**.
3. Toggle **Content analysis** between **On** and **Off**.
4. Configure the following extension names and separate extension names with a comma:

   - **File extension names** - Suspicious files except email attachments will be submitted for additional inspection

Note

By default, several extension names are automatically filled. One of them is ***double quotes \("\)***, which includes files that don't have any file extensions at all.

## Related content

- [Manage automation folder exclusions](https://learn.microsoft.com/en-us/defender-endpoint/automation-folder-exclusions-configure)
