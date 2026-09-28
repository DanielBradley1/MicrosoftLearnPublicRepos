<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/protected-view -->
<!-- Sitemap-Last-Modified: 2023-03-20 -->

# Protected view for documents on CSPP Plus hosts

Protected view \([Protected View](https://support.microsoft.com/topic/what-is-protected-view-d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653)\) and Application Guard \([Application Guard for Office](https://support.microsoft.com/topic/application-guard-for-office-9e0fb9c2-ffad-43bf-8ba3-78f785fdba46)\) are mechanisms embedded into Microsoft Office products to help protect users' computers from attacks in files sourced from the Internet. A user's license controls the availability of these tools. When enabled, Office opens files from potentially unsafe locations in Protected View or Application Guard.

As part of the CSPP Plus program, desktop Office clients can open, edit, and save files stored on selected third-party hosts. Like other files originating from the Internet, these files are considered potentially unsafe and, by default, open in a restricted form:

![File opened in Protected View](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/protected-view-1.png)

***Figure 1*** - *File opened in Protected View*

![File opened in Application Guard](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/protected-view-2.png)

***Figure 2*** - *File opened in Application Guard*

It's possible to remove the protection provided by Protected View and Application Guard to enable unrestricted access to files, converting the documents to Trusted Documents.

Note

Organizations can implement policies that prevent removing Protected View and Application Guard protection from a file.

## Individual \(per file\) authorization

Users can trust individual documents to prevent opening them in Protected View and Application Guard:

Warning

Users are advised to only do this if they are confident that the file, and its source, is trustworthy.

For Protected View:

- On the Message Bar, click **Enable Editing**.

For Application Guard:

- Go to **File** > **Info** and select **Remove protection**.

## Manual authorization \(per machine\)

Users can trust specific Internet locations to prevent Protected View and Application Guard to act on those files based on location.

Warning

Only do this if you're confident that the location is trustworthy.

Add the host internet address as a trusted site:

1. Open the **Control Panel**.
2. Open the **Internet Options** object.
3. In the Internet Properties window, click the **Security** tab.
4. Select the **Trusted sites** entry and click the **Sites** button.  
   ![Internet properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/protected-view-3.png)
5. In the **Add this website to the zone** field, enter the address for the trusted location starting with *https:*.
6. Click **Add**.  
   ![Trusted sites](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/protected-view-4.png)
7. Close the windows.

Note

Organizations can implement policies that prevent users from modifying these settings.

## Global authorization \(GPO\)

IT admins can enforce assignments of Internet Sites to Security Zones across organizations using Group Policy Objects \(GPO\). This includes the classification of a particular hosts as a trusted location.

To enforce mapping hosts to certain zones, IT admins can enable and configure this GPO: **Site to Zone Assignment List**.

You can find this GPO in the Group Policy Editor under:  
**Computer Configuration / Administrative Templates / Windows Components / Internet Explorer / Internet Control Panel / Security Page / Site to Zone Assignment List**.

![Site to Zone Assignment List](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/images/protected-view-5.png)

Note

`api.contoso.com` in the previous screenshot should be replaced by the appropriate domain\(s\) provided by the CSPP Plus host.

After enabling the GPO, IT Admins can assign websites to each of the security zones according to this map:

1. Intranet zone
2. Trusted Sites zone
3. Internet zone
4. Restricted Sites zone

To prevent Protected View and Application Guard to act on files based on location, the host address, starting with https:, should be assigned to Trusted Sites zone \(2\).

Note

Enabling the Site to Zone Assignment List GPO overwrites all previously configured assignments. It prevents users from modifying the assignments. And sets it to only consider the mappings included in the GPO across all the zones.

## Related articles

- [Using Group Policy Preferences to add a web site to local intranet, trusted site, and still allow them to add their own](http://jjstellato.blogspot.com/2011/08/using-group-policy-preferences-to-add.html).
