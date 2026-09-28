<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/createnew -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# Create new files using Microsoft 365 for the web

Hosts can create new Microsoft 365 files using blank document templates from Microsoft 365 for the web. In order to support this, hosts use the `editnew` WOPI action as follows:

1. Create a zero-byte file with the appropriate file extension. Use `docx` for Word documents, `pptx` for PowerPoint presentations, and `xlsx` for Excel workbooks.
2. Run the `editnew` action on the newly created file. Microsoft 365 for the web detects that the file is zero bytes based on the [Size](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#size) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response.

Once the `editnew` action runs, Microsoft 365 for the web runs a [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) operation on the file, overwriting it with template content appropriate to the file type.

This [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) operation is done on an unlocked file. Hosts must ensure that [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) operations on the unlocked, zero bytes files succeed. For more information, see the [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) documentation.

Important

Because creating new files is done in two steps, it's possible for the [**PutFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile) operation to fail, leaving the zero-byte file. Since such a file isn't valid, hosts should expect and handle this case. The ultimate solution is left to the host. Options for handling this situation include:

- Hide zero-byte files from the user.
- Prevent users from opening zero-byte files in Microsoft 365 for the web.
- If a file is zero bytes, when opening Microsoft 365 for the web against the file, always use the `editnew` action. \(This is only an option if the user has edit permissions to the document.\)

This isn't an exhaustive list of options; ultimately, the host must decide the best approach to this issue.
