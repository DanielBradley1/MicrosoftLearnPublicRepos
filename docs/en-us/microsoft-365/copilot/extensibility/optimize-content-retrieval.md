<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/optimize-content-retrieval -->
<!-- Sitemap-Last-Modified: 2025-09-12 -->

# Optimize content retrieval

Declarative agents extend Microsoft 365 Copilot to customize the experience for users. When you build declarative agents, you can add SharePoint content and upload files as knowledge sources. This article describes the best practices to apply to optimize how your agent returns data from SharePoint and embedded content knowledge sources.

Note

Agents grounded in SharePoint data and embedded files are only available to users in tenants that have Copilot Studio metering enabled or users who have Microsoft 365 Copilot licenses. For details, see [Microsoft 365 Copilot developer licenses](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/prerequisites#microsoft-365-copilot-developer-licenses).

## Reference only relevant SharePoint files

You can reference specific SharePoint files via the `OneDriveAndSharePoint` object in the [agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.5#onedrive-and-sharepoint-object), either by URL or by ID.

When you specify up to 20 files, Copilot searches the full contents of all files. Copilot has full access to all the file content and returns the appropriate content to the user based on their query.

To optimize the content that Copilot returns, choose the most relevant SharePoint files to specify in your manifest. For example, if a folder contains eight files and only five are relevant to the user's task, specify the five files individually instead of referencing the folder. To ensure that Copilot searches the full file contents, the best practice is to limit the total page count of the relevant files that you specify to no more than 300 pages.

## Limit SharePoint file size

When you reference SharePoint sites or folders by URL in your [agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.4#onedrive-and-sharepoint-object) and the files included in the site or folder are large, Copilot might have trouble identifying the right content to return to the user. To reduce the risk that Copilot won't find the right content in the sites or folders you reference, keep your SharePoint files to a maximum of 36,000 characters \(approximately 15-20 pages\). If your files are larger than 36,000 characters, consider breaking them up into separate shorter files to help Copilot scan the full contents.

Alternatively, you can reference specific SharePoint files by ID. Copilot will search the full contents of all files if you specify 20 or fewer files. If you specify more than 20 files, it will search the full contents of the 20 most relevant files.

## Remove special formatting

Copilot is currently unable to parse tables and other special formatting in SharePoint content. To ensure that Copilot can consume your SharePoint content, remove tables or other special formatting from the content before you reference it in your agent manifest.

## Optimize embedded file content retrieval

For agents that include [embedded file content](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge#embedded-file-content), Copilot indexes the first 750-1,000 pages \(1.8 million characters\) of each embedded file.

To optimize embedded file content for Copilot retrieval, upload files that are no larger than 750-1,000 pages. For more information, see [Length of documents that you provide to Copilot](https://support.microsoft.com/topic/keep-it-short-and-sweet-a-guide-on-the-length-of-documents-that-you-provide-to-copilot-66de2ffd-deb2-4f0c-8984-098316104389).

To optimize Excel content for Copilot retrieval, store all the data in one sheet within a workbook.

## Related content

- [Declarative agents overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-declarative-agent)
- [Known issues](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/known-issues)
