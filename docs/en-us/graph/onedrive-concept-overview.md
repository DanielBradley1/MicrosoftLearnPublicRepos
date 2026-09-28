<!-- Source: https://learn.microsoft.com/en-us/graph/onedrive-concept-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# OneDrive file storage API overview

OneDrive is the files hub in Microsoft 365. People work with files in a variety of contexts, like Microsoft Teams, groups, SharePoint, and more. With OneDrive, users can access these files no matter where they are stored, and with Microsoft Graph, you can use a single API to work with them.

Files in Microsoft 365 are stored in [drives](https://learn.microsoft.com/en-us/graph/api/resources/onedrive). Users can store files in a personal drive—their OneDrive—or in a shared drive powered by a [SharePoint](https://learn.microsoft.com/en-us/graph/sharepoint-concept-overview) document library. OneDrive's flexibility lets users collaborate however it works best for them. Users can share links to files, copy or move files to team drives, or even attach OneDrive files to mail messages in Outlook.

<iframe src="https://www.youtube-nocookie.com/embed/vG-hQxFHCAE" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Why integrate with OneDrive file storage in the cloud?

### Tap into an ecosystem with billions of files

OneDrive users can access their files from any device, online or offline, and share files with people inside or outside their organization. OneDrive enables real-time coauthoring in familiar apps like Word, Excel, and PowerPoint. Files light up with rich thumbnails for hundreds of formats, video streaming, analytics, and more, powered by Microsoft Graph. Data in OneDrive is protected with advanced encryption, compliance, and security features that customers trust.

With over 500 million devices running the OneDrive app and over 85% of the Fortune 500 using OneDrive for Business, by integrating your app with OneDrive, you can connect with millions of consumers, students, and business users and engage with customers where they already do their work every day.

### Store your app's files in a powerful cloud

When you store your files in OneDrive, your app can take advantage of the features of the Microsoft cloud and your users can access their files anywhere. Use the [file picker](https://dev.onedrive.com/sdk/js-v72/js-picker-overview.htm) SDK to quickly open, download, save, or share files stored in OneDrive from within your own app, using the same experience OneDrive users are familiar with. Get information about selected files directly from the picker SDK, or use Microsoft Graph APIs directly to interact more deeply with files. Use [special folders](https://learn.microsoft.com/en-us/graph/api/drive-get-specialfolder) to store files in well-known locations on OneDrive, like `Documents` and `Camera Roll`, or give your app its own personal folder.

### Bring your app straight to users within OneDrive

OneDrive customers can use or launch your app directly from within OneDrive to open, edit, or preview files. Use OneDrive's [file handler](https://learn.microsoft.com/en-us/onedrive/developer/file-handlers) extensions to provide icons and previews for your own custom file extensions, add your app to the **New** button or even add your own custom actions to the menu bar to launch your app.

### Work with content in formats your app understands

Your app can get file content in the format that is most convenient for you. Your app can display custom-sized [thumbnails](https://learn.microsoft.com/en-us/graph/api/driveitem-list-thumbnails) for hundreds of different file formats. You can download files in a variety of alternative [formats](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format), like PDF. You can even embed the OneDrive file previewers within your app by using the [preview](https://learn.microsoft.com/en-us/graph/api/driveitem-preview) API \(beta\).

### Work with file content and metadata without downloading the binary

With Microsoft Graph, you can access rich content through REST APIs without having to download the binary. Explore extracted metadata from [photo](https://learn.microsoft.com/en-us/graph/api/resources/photo), [audio](https://learn.microsoft.com/en-us/graph/api/resources/audio), and [video](https://learn.microsoft.com/en-us/graph/api/resources/video) files. Use the [Excel API](https://learn.microsoft.com/en-us/graph/api/resources/excel) to work directly with the raw data stored in an Excel workbook. Use the [Notes API](https://learn.microsoft.com/en-us/graph/integrate-with-onenote) to access the contents of OneNote notebooks.

### React to file changes

With [webhooks](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview), your app can get notified when files change so you can quickly react. Use the [delta API](https://learn.microsoft.com/en-us/graph/api/driveitem-delta) to see what changed since the last time your app synchronized with the cloud.

## API reference

Looking for the API reference for this service?

- [OneDrive file storage API in Microsoft Graph v1.0](https://learn.microsoft.com/en-us/graph/api/resources/onedrive)
- [OneDrive file storage API in Microsoft Graph beta](https://learn.microsoft.com/en-us/graph/api/resources/onedrive)
