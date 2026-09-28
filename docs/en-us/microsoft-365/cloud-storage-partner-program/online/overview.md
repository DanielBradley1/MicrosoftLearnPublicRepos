<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/overview -->
<!-- Sitemap-Last-Modified: 2026-07-10 -->

# Integrate with Microsoft 365 for the web

As members of the Cloud Storage Partner Program \(CSPP\), cloud storage providers can seamlessly integrate Microsoft Word, Excel, and PowerPoint for the web directly into their cloud storage solutions. This integration allows users to open, view, edit, and save files in Microsoft 365 files directly the browser within the end user's browser, delivering a consistent experience that aligns with CSPP requirements and enhances productivity without leaving the partner's storage solution.

Important

The Microsoft 365 - Cloud Storage Partner Program is for independent software vendors whose business is cloud storage. It's not open to Microsoft 365 customers directly.

Overview of a Cloud Storage Provider:

- Is an independent software vendor \(ISV\) that develops, owns, and operates a product or service including cloud file storage.
- Makes their solution available as a Software as a Service \(SaaS\).
- Operates a solution that stores all end users’ files at rest in a cloud location entirely owned or leased by the partner \(including under a subscription or similar arrangement with a third‑party cloud infrastructure provider\) and not in any location owned, leased, or subscribed to by the partner’s customers.
- Owns the WOPI host domain URLs as explained in [Microsoft configured settings](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings).
- Manages identity controls for access to the solution.
- Serves more than one external customer.

To meet CSPP program requirements, all partner solutions must demonstrate full WOPI integration in compliance with the [Microsoft Cloud Storage Partner Program Integration Terms](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/legal/cspp-terms) and this documentation. This ensures that solutions align with the established technical and operational guidelines while providing end-users a consistent experience across platforms.

These requirements represent a baseline for participation in the CSPP program. Every application is individually reviewed for suitability by the CSPP team. The program is governed by the [Microsoft Cloud Storage Partner Program Integration Terms](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/legal/cspp-terms).

Important

Participants in the Microsoft 365 - Cloud Storage Partner Program must support upload, download, viewing, and editing in Microsoft Word, Excel and PowerPoint for the web even if the published partner solution will only show a subset of these applications and/or functions to the end-user.

## View Microsoft 365 files

You can make viewing available in two ways:

- By using the high-fidelity previews in Microsoft 365 for the web as an integrated part of your experience. For example, you can use these previews in a light box view of a Word document.
- By offering to show Microsoft 365 files in a full-page interactive preview. Depending on your solution, this might be useful for file browsing or showing read-only files or in cases where users don’t have a license to edit files in Microsoft 365 for the web.

## Edit Microsoft 365 files

Editing is a core part of Microsoft 365 for the web integration. When you integrate with Microsoft 365 for the web, your users can edit Excel, PowerPoint, and Word files directly in the browser. Also, they can [edit documents collaboratively with other users using Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/coauth). To edit documents, users require an Microsoft 365 license. For more information, see [Managing Microsoft 365 User Licenses](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business).

## Integration process

Integrating with Microsoft 365 for the web includes some HTML and JavaScript work and setting up a few simple REST endpoints. If you're familiar with existing Microsoft 365 protocols, note that you don’t have to implement the \[MS-FSSHTTP\]: File Synchronization via SOAP over HTTP Protocol \(Cobalt\). At a high level, to integrate with Microsoft 365 for the web, you:

- Read XML from Microsoft 365 for the web that describes the capabilities of Microsoft 365 for the web. This is called [WOPI discovery](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#wopi-discovery).
- Implement [REST endpoints](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/endpoints) that Microsoft 365 for the web uses to learn about, fetch, and update files. To do this, you implement the server side of the WOPI protocol.
- Provide an HTML page \(or pages\) that wrap Microsoft 365 for the web. This page is called the [host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage).

The following figure shows the WOPI protocol workflow.

![Figure 2 WOPI protocol workflow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/wopi-flow.png)

***Figure 2 -** WOPI protocol workflow*

Your solution must meet the following basic requirements.

### Authentication

Authentication is handled by passing Microsoft 365 for the web an access token that you generate. Assign this token a reasonable expiration date. Also, we recommend that tokens are only valid for a single user against a single file, to help mitigate the risk of token leaks. For more information, see [Access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).

### Conflict resolution

Microsoft 365 for the web supports multiuser authoring scenarios if all users are using Microsoft 365 for the web. However, you're responsible for managing conflicts that might come from applications other than Microsoft 365 for the web. You'd want to set up some form of file locking or use another type of conflict resolution.

### File IDs

Ensure that files are represented by a persistent ID. This ID must be URL-safe because it might be passed as part of the URL at different times. Also, the ID can't change when the file is renamed, moved, or edited. This ensures an uninterrupted editing experience for your users. For more information, see [File ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id).

### File versions

You should have a mechanism for users to clearly identify file versions through the REST APIs. Because files are cached to improve viewing performance, file versions are extremely helpful. Without them, users can’t easily determine whether they have the latest version of the file.

## Consider security

Microsoft 365 for the web is designed to work for enterprises that have strict security requirements. To make your integration as secure as possible, be sure that:

- All traffic is SSL encrypted.
- Initial requests to Microsoft 365 for the web are made by using POST, where the access token is in the body of the POST request.

Set up Microsoft 365 for the web identity by using a public [proof key](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys) to decrypt part of the WOPI requests. Also, the file cache indexes store file contents by using a SHA256 hash as the cache key. You can pass the hash value to Microsoft 365 for the web by using the [SHA256](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#sha256) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response. If not provided, Microsoft 365 for the web generates a cache key from the file ID and version. To ensure that users don't force a cache collision and view the wrong file, none of the user-provided information should generate the cache key.

## Microsoft 365 subscriptions

Any user who will edit files using a Microsoft 365 app must have a valid Microsoft 365 license. CSPP partners are responsible for ensuring all of their users have the appropriate license and that business users in particular are programatically checked for such a listence. For details, see [Managing Microsoft 365 user licenses](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business).

## Interested?

If you’re interested in integrating your solution with Microsoft 365 for the web, take a moment to register at [Microsoft 365 Cloud Storage Partner Program](https://developer.microsoft.com/office/cloud-storage-partner-program).
