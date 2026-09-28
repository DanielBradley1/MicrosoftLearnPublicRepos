<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/known-issues -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Known Issues

The following are known issues for Microsoft 365 for the web integration.

## Known Issues integrating with Microsoft 365 for the web

#### [#139](https://github.com/microsoft/Office-Online-Test-Tools-and-Documentation/issues/139): Business user flow: Microsoft 365 for the web does not load properly after user sign-in when third-party cookies are disabled

As part of the [business user flow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business), users are asked to sign in using their Microsoft 365 credentials. After sign-in, they're re-directed to the HostEditUrl. But if third-party cookies are disabled, the Microsoft 365 for the web application fails to load because the authentication cookie needed to verify the user has signed in successfully with Microsoft 365 and it isn't sent along with the Microsoft 365 for the web iframe request.

Users must either allow third-party cookies or add `*.officeapps.live.com` to their browsers cookie allow list.

In some browsers, like Safari, third-party cookies are disabled by default.

Also, browsers like Internet Explorer have a concept of *zones*, which can change how cookies are handled \(among other things\). Ensure all the sites in question are in the internet zone.

#### [#143](https://github.com/microsoft/Office-Online-Test-Tools-and-Documentation/issues/143): PowerPoint for the web: Download a Copy triggers browser pop-up blocker

In PowerPoint for the web only, the **Download a Copy** action can trigger the browser's pop-up blocker. We're working on a fix for this issue.

#### [#158](https://github.com/microsoft/Office-Online-Test-Tools-and-Documentation/issues/158): Microsoft 365 for the web fails to load files with characters in the name that are invalid in Windows

If a user's file name contains the following characters, the file won't open properly in Microsoft 365 for the web:

`\` `/` `:` `*` `?` `"` `<` `>` `|`

We're evaluating fixes for this problem. In the meantime, hosts should strip these characters from file names in order to open them in Microsoft 365 for the web.

#### [#183](https://github.com/microsoft/Office-Online-Test-Tools-and-Documentation/issues/183): Creating new documents in Word for the web results in two PutFile calls

When [creating new files](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/createnew) in Word for the web, the WOPI host receives two PutFile requests from Microsoft 365 for the web instead of one.

## Known issues integrating with Microsoft 365 for mobile

#### Microsoft 365 for mobile fails to load files with invalid characters in the file name, folder names, or user ID

Microsoft 365 for mobile fails to load files if there are invalid characters in certain [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) or [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo) properties. The following characters are not supported:

`\` `/` `:` `*` `?` `"` `<` `>` `|` `#` `{` `}` `^` `[` `]` `%`

These properties are affected:

###### CheckFileInfo

- [BaseFileName](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#basefilename)
- [UserId](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#userid)
- [OwnerId](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#ownerid)

###### CheckContainerInfo

- Name

To work around this issue, hosts should replace these characters with `-`.
