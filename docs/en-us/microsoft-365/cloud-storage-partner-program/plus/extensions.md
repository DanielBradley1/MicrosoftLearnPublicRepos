<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/extensions -->
<!-- Sitemap-Last-Modified: 2023-06-17 -->

# Supported File Types and Extensions for Coauthoring

|  | Word | Excel | PowerPoint |
| --- | --- | --- | --- |
| **Coauthoring-Enabled**  <br>• The list of WOPI+ Open and Save a Copy is filtered to this list  <br>  <br>  <br>  <br>  <br> | `.docx`  <br>  <br>  <br> | `.xlsx`  <br>`.xlsm`  <br>`.xlsb`  <br>  <br>  <br>  <br> | `.pptx`  <br>`.ppsx`  <br>  <br>  <br>  <br> |
| **Local-only**  <br>• All other extensions \(including but not limited to\)  <br>• Open and edit via sync-client on the local machine, not via WOPI+  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br> | `.doc`  <br>`.docm`  <br>`.dot`  <br>`.dotx`  <br>`.dotm`  <br>`.odt`  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br>  <br> | `.xls`  <br>`.xla`  <br>`.ods`  <br>`.csv`  <br>`.xml`  <br>`.xmlx`  <br>`.mht`, `.mhtml`  <br>`.htm`, `.html`  <br>`.txt`  <br>`.dif`  <br>`.slk`  <br>`.pdf`  <br>`.xps` | `.ppt`  <br>`.pot`  <br>`.potm`  <br>`.potx`  <br>`.pps`  <br>`.ppsm`  <br>`.pptm`  <br>`.odp`  <br>  <br>  <br>  <br>  <br>  <br> |

## Coauthoring-Enabled

You can open and save these files to the host via WOPI+.

The Add-a-Place file browsing experience and the Save-a-Copy experience are intentionally filtered to only these file extensions.

## Local-only file types

These are non-collaboration file types that are editable by the Microsoft Office Desktop apps, but are not supported for coauthoring.

As noted above, these file types are filtered out from the in-app file browsing experience via Add-a-Place.

In the case of an open from the local disk \(including from a sync-backed folder\) files with these extensions will always open in Local Only mode. Similarly, if the user wants to save to a file of this type, they can use the Browse functionality to open the native Common File Dialog.

![the Browse functionality allows the user to open the native Common File Dialog](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/common-file-dialog.png)

This will provide a file type drop-down \(as shown in Excel\) that's typical for the local file experience:

![File type drop-down \(Excel shown\) that is typical for the local file experience](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/common-file-dialog-dropdown.png)

## Strict Open XML Document format

Coauthoring is not supported for files originally saved in the Strict Open XML Document format. Attempting to open a file stored in this format will result in the error, *"Someone has this workbook locked"*.

Unfortunately, it's not always easy to determine if a file was saved in the Strict Open XML Document format as these files have the same extensions as the default file types. This means that Word, Excel, and PowerPoint files saved in the Strict Open XML Document format will still have the `.docx`, `.xlsx`, and `.pptx` extensions.

If your users are seeing error this when attempting to coauthor, use the following steps to try and resolve the issue:

1. Have all but one user close the file
2. The remaining user should save the file in any format other than Strict XML
3. All users can now open the document and coauthor

## More information about coauthoring and Office file types

- For general information about coauthoring that is not WOPI specific, see the [Document collaboration and co-authoring](https://support.microsoft.com/en-us/office/document-collaboration-and-co-authoring-ee1509b4-1f6e-401e-b04a-782d26f564a4) documentation.
- You can find answers to common co-authoring issues on the [Troubleshoot co-authoring in Office](https://support.microsoft.com/en-us/office/troubleshoot-co-authoring-in-office-bd481512-3f3a-4b6d-b7eb-ebf9d3626ae7) page.
- See the [File format reference for Word, Excel, and PowerPoint](https://learn.microsoft.com/en-us/deployoffice/compat/office-file-format-reference) to get detailed information about Office file formats.
