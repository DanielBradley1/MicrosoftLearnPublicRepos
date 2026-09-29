<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/troubleshooting-content-inspection -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Troubleshooting content inspection errors

Important

File policies retire on January 6, 2027. To maintain file-based data protection, [migrate to Microsoft Purview DLP or auto-labeling policies](https://learn.microsoft.com/en-us/defender-cloud-apps/migrate-file-policies-to-purview).

This article provides a list of content inspection statuses and their meanings.

## Content inspection status

The table lists each content inspection status and its description.

| Content inspection status | Description |
| --- | --- |
| Completed | The content inspection completed successfully. |
| Not applicable | Content inspection wasn't applicable for this file. This status might appear because no policy requires content inspection of this file or because the file type isn't supported. |
| Pending | The file is currently in the content inspection queue. |
| Failed: Download error | Microsoft Defender for Cloud Apps couldn't download the file for inspection. |
| Failed: File is encrypted | The file couldn't be decrypted. If the [Inspect protected files](https://learn.microsoft.com/en-us/defender-cloud-apps/content-inspection#content-inspection-for-protected-files) setting is active and the file policy has the **Inspect protected files** checkbox selected, this status is expected and can be safely disregarded. |
| Failed: File is corrupted | The file is corrupted in some way and couldn't be inspected. |
| Failed: Internal error | Something undetermined went wrong when trying to inspect the file. |
| Failed: File size exceeded | The file exceeded the maximum file size of 30 MB. |
| Failed: File is too long and was partially scanned | The file exceeded the maximum of 1 million characters. For the part of the content that was scanned, relevant policy matches were applied. |
| Failed: File access denied | The file is external to your cloud and couldn't be accessed by Defender for Cloud Apps. |
| Failed: File was deleted | The file no longer exists in your cloud and couldn't be inspected. |
| Failed: Unsupported file type | Defender for Cloud Apps can't perform content inspection on this file type. This status may appear because the file type isn't supported or because the file isn't actually in the format of the expected file type. |

Note

If you see a dash in the scan status, this means that the file is not queued to be scanned. See [File policies](https://learn.microsoft.com/en-us/defender-cloud-apps/data-protection-policies) for information on setting content inspection policies.

## Next steps

[Best practices for protecting your organization](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
