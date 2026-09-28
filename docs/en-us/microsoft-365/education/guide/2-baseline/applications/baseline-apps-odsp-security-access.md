<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-security-access -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 3: Configure security and access control in OneDrive and SharePoint for education

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Microsoft OneDrive and SharePoint \(ODSP\) are key components of the education offering for the Microsoft ecosystem. This article provides guidance on how to configure security and access control in Microsoft OneDrive and SharePoint for education.

## Roles and responsibilities

- IT Admin
- Identity Admin
- OneDrive Admin
- SharePoint Admin
- EXO Admin

## Authentication

SharePoint in Microsoft 365 serves a wide range of customers with various usability and security needs. Some customers don't mind asking users to reauthenticate if it means their data is more secure. Other customers want to minimize the number of sign-in screens that users see, especially in situations where it seems as though SharePoint should already know who the user is. Luckily, customers don't have to choose usability or security because they work together in many great ways.

Learn more about [authentication in SharePoint in Microsoft 365](https://learn.microsoft.com/en-us/sharepoint/authentication).

[![Picture describing authentication in SharePoint.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sharepoint-authentication.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sharepoint-authentication.png#lightbox)

## Safeguarding your data

You control your data. When you put your data in SharePoint and OneDrive for Microsoft 365, you remain the owner of the data. For more info about the ownership of your data, see [Microsoft 365 Privacy by Design.](https://www.microsoft.com/trustcenter/privacy/privacy-overview)

Learn more about [how Microsoft 365 safeguards your data in SharePoint and OneDrive](https://learn.microsoft.com/en-us/sharepoint/safeguarding-your-data).

## Control access from unmanaged devices

As at least a SharePoint Administrator in Microsoft 365, you can block or limit access to SharePoint and OneDrive content from unmanaged devices \(those not hybrid AD joined or compliant in Intune\). You can block or limit access for:

- All users in the organization or only some users or security groups
- All sites in the organization or only some sites

Learn more about how to [control access from unmanaged devices](https://learn.microsoft.com/en-us/sharepoint/control-access-from-unmanaged-devices).

## Control access based on network location

As an IT admin, you can control access to SharePoint and OneDrive resources in Microsoft 365 based on defined network locations that you trust. This is also known as location-based policy.

To create a location-based policy, you define a trusted network boundary by specifying one or more authorized IP address ranges. Any user who attempts to access SharePoint and OneDrive from outside this network boundary \(using web browser, desktop app, or mobile app on any device\) is blocked.

Learn more about how to [control access based on network location](https://learn.microsoft.com/en-us/sharepoint/control-access-based-on-network-location).

## Enable conditional access \(OneDrive\)

Conditional access control capabilities in Microsoft Entra ID offer simple ways for you to secure resources in the cloud. The new OneDrive sync app works with the conditional access control policies to ensure syncing is only done with compliant devices. For example, you might require sync to be available only on domain-joined devices or devices that meet compliance as defined by the Mobile Device Management system \(like Intune\).

Learn more about how to [enable conditional access](https://learn.microsoft.com/en-us/sharepoint/enable-conditional-access).

For information about how conditional access works, see:

- [Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/)
- [Require managed devices for cloud app access with conditional access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/require-managed-devices)
- [Configure Microsoft Entra hybrid join for managed domains](https://learn.microsoft.com/en-us/azure/active-directory/devices/hybrid-azuread-join-managed-domains)
- [Control access from unmanaged devices](https://learn.microsoft.com/en-us/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive)

## Sign out inactive users

SharePoint Administrators or higher in Microsoft 365 who want to control user access to SharePoint and OneDrive data on unmanaged devices. Idle session sign-out lets you specify a time at which users are warned and are later signed out of Microsoft 365 after a period of browser inactivity in SharePoint and OneDrive.

Learn more about how to [sign out inactive users](https://learn.microsoft.com/en-us/SharePoint/sign-out-inactive-users).

Note

For education scenarios:

## Next steps

Now that you completed the OneDrive/SharePoint security and access section, you're ready for the OneDrive/SharePoint compliance section.

[Next: OneDrive/SharePoint Compliance>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-compliance)
