<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/scenarios/from-app -->
<!-- Sitemap-Last-Modified: 2023-03-20 -->

# Open files from your app in Microsoft 365 for mobile

In order to invoke Microsoft 365 for mobile when opening an Office file from your app, you must use the URL schemes that Word, Excel, and PowerPoint for iOS or Android register when they are installed.

## URL schemes for invoking Microsoft 365 for mobile

The following is the list of scheme names used to invoke Microsoft 365 for mobile:

- `ms-word:`
- `ms-powerpoint:`
- `ms-excel:`

You must include the following information along with the URL scheme:

- The mode in which to open the file. Valid values are:

  - `ofv` for opening as read-only.
  - `ofe` for opening for editing.

- The [WOPISrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) to the file, denoted by the `|u|` parameter.
- The service identifier, denoted by the `|d|` parameter.
- The user identifier, denoted by the `|e|` parameter.
- The file name, with extension, denoted by the `|n|` parameter.
- The source of the open action with `|a|`. The value of this parameter can be either:

  - `Web` – to be used in the case where a website is invoking the protocol handler.
  - `App` – to be used in the case where a native app is invoking the protocol handler.

Example:

`ms-word:ofe|u|https://contoso/wopi/file/12312|d|Contoso|e|a3243d|n|document1.docx|a|App`

The URL used should be URL encoded.

Note that the file is opened directly against your service. Your app essentially passes the URL to the file to Microsoft 365 for mobile without passing the actual file. The Microsoft 365 for mobile app then opens the file directly using the WOPI protocol.

## Identifying supported Office for iOS versions

Before using the URL schemes specified above to invoke Microsoft 365 for iOS, you must do the following:

1. Verify the particular Microsoft 365 for iOS application \(Word, Excel, or PowerPoint\) is installed.

   Use the iOS `canOpenURL` method to determine whether your application can open the resource. This method takes the URL for the resource as a parameter, and returns No if the application that accepts the URL is not available. If `canOpenURL` returns No, you’ll need to prompt the user to install Office for iOS. Use the following links to direct the user to the appropriate Microsoft 365 application:

   - For iOS, use [https://aka.ms/m365ios3p](https://aka.ms/m365ios3p)
   - For Android, use [https://aka.ms/m365aos3p](https://aka.ms/m365aos3p)

2. Check the version of Microsoft 365 for iOS installed is a supported version. You can check this by verifying whether the following URL schemes are registered:

   - `ms-word-wopi-support-1605`
   - `ms-powerpoint-wopi-support-1605`
   - `ms-excel-wopi-support-1605`


   Important


   These URL schemes are only used to check if the currently installed Microsoft 365 for iOS supports opening files from a WOPI host, and not for invoking the Microsoft 365 for iOS apps.

## \(Optional\) Passback protocol for Office for iOS

If you want Microsoft 365 for iOS to return users to your iOS application when they choose the in-app back arrow \(distinct from the iOS back control\), you will need to include the passback parameter when invoking Microsoft 365 for iOS. This is denoted by `|p|` followed by your app’s registered URL scheme \(without a colon\).

You must ensure that your application can properly handle the response from Microsoft 365 for iOS.

Tip

You’ll provide your app’s registered URL scheme during the initial integration phase.

For security reasons, Microsoft 365 for iOS only returns users to the referring application if the file opened successfully. When the user chooses the back arrow, Microsoft 365 for iOS responds to the invoking application with the passback protocol, open mode, URL, upload-pending status, and `document context`. The upload-pending status uses the descriptor `|z|`, and is either yes or no.

`document context` is a string you provide via the `|c|` parameter when invoking Microsoft 365 for iOS. Microsoft 365 for iOS doesn’t use this parameter; it's purely for your use, as needed by your app. Microsoft 365 for iOS doesn't limit the length of the string beyond any limits the operating system imposes.

Schema format invoking your app when user chooses back:

`<app protocol>:ofe|u|<URL>|z|<yes or no>|c|<doc context>`

Example:

`contosodrive:ofe|u|https://contoso/Q4/budget.docx|z|no|c|folderviewQ4`
