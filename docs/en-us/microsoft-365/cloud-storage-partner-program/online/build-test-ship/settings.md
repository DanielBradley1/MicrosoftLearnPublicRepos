<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Microsoft-configured settings

Most Microsoft 365 for the web behavior is configurable based on properties provided in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo). However, there are some Microsoft 365 for the web settings that must be changed by Microsoft.

Important

Changes to these settings require time to propagate.

Any changes to Microsoft-configured settings **will take 4-5 weeks to fully roll out**. This includes changes to the [WOPI domain allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#wopi-domain-allow-list), and applies to both the production and test environments.

## WOPI domain allow list

Important

Any domains added to the allow list **must be owned by the partner**. Microsoft doesn't permit domains associated with a partner that aren't owned and controlled by that partner.

Note

Only subdomains are allowed in the domain allow list. For example: 'test.contoso.com' is acceptable. '\*.contoso.com' is not acceptable and will be rejected.

Microsoft 365 for the web only makes WOPI requests to trusted partner domains. This domain list is called the *WOPI domain allow list.* It contains entries of the form:

- `wopi.contoso.com`
- `qa-wopi.contoso.com`

Entries in the WOPI domain allow list are implicitly wild-carded. In other words, the entry `wopi.contoso.com` is equivalent to `*.wopi.contoso.com`. This entry allows WOPI requests to be made to any subdomain under `wopi.contoso.com`.

Tip

If you ever generate [**WopiSrc**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) values that point to a subdomain, it needs to be on the allow list. The [**WopiSrc**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) represents the domain that a WOPI client uses to run WOPI operations against.

If you don't ever generate [**WopiSrc**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) values that point to a subdomain, that subdomain doesn't need to be on the WOPI domain allow list \(but it might need to be on the [**Redirect domain allow list**](#redirect-domain-allow-list)\).

#### Test Environment

Microsoft 365 for the web has different allow lists for the production and test environments. When you're first given access to the test environment, Microsoft adds the domains you provide to the test-only WOPI domain allow list.

In the Microsoft 365 for the web test environment, hosts must use a WOPI-dedicated subdomain for handling WOPI traffic. This subdomain is typically something like `wopi-test.hostdomain.com`, though that's just a name convention and hosts can use other names if needed. This approach ensures that Microsoft 365 for the web can't make WOPI requests to arbitrary domains.

Note

The [domain\(s\) configured](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping) for your Test environment can't match the ones you will be using in Production

For testing and development using the Microsoft 365 for the web test environment, a WOPI-dedicated subdomain isn't required.

#### Production Environment

Important

You must first pass verification testing described in [Launch your Microsoft 365 for the web integration](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/shipping) before we will provision production domains.

In the Microsoft 365 for the web production environment, hosts must use a WOPI-dedicated subdomain for handling WOPI traffic. This subdomain is typically something like `wopi.hostdomain.com`, though that's just a name convention and hosts can use other names if needed. This approach ensures that Microsoft 365 for the web can't make WOPI requests to arbitrary domains.

Warning

A production WOPI subdomain shouldn’t ever surface user-provided content. In other words, a user shouldn’t be able to upload something to the host and trick Microsoft 365 for the web into making WOPI requests to the user-controlled content. That would represent a potential security hole.

For example, consider a service that uses the URL `https://www.contosodrive.com` for their main website. Users can upload and control content that's served out of the `www.contosodrive.com` domain. If the Microsoft 365 for the web allow list contains `contosodrive.com`, then a nefarious user could upload content and then create a [WOPISrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) pointing to it, like this: `?WOPISrc=https://www.contosodrive.com/my-content/wopi/files/attack.json`. They could then provide an arbitrary CheckFile and possibly GetFile response by using the [FileUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileurl) property. This means that an attacker can abuse the trust between the Microsoft 365 for the web service and the host. In one possible example, the attacker could change links in the Microsoft 365 for the web UI like the button controlled by the [FileSharingUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#filesharingurl) property to lead to malicious sites.

This threat is mitigated by requiring a dedicated subdomain for WOPI traffic that's separate from the domain used when serving user content.

Tip

All domains on the production allow list are automatically allowed in the test environment. The inverse isn't true.

You can request changes to your domain allow list by submitting an [Environment Change Request form](https://aka.ms/cspp-update). Any changes to Microsoft-configured settings **will take 4-5 weeks to fully roll out**. This applies to both the production and test environments.

## ‘Saved to…’ name

Microsoft 365 for the web displays a message in the bottom status bar when saving files.

![Figure 1 The ‘Saved to…’ UI for OneDrive](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/saved-to.png)

***Figure 1 -** The ‘Saved to…’ UI for OneDrive*

By default, the name listed in this UI will match the Microsoft 365 for the web partner ID for your host. In most cases, this is the appropriate value. However, there may be cases where you wish to use a different name here than your partner ID. For example, you may have a specific product brand that you want to display here such as ‘ContosoDrive’ instead of ‘Contoso.’ In that case, you can provide your preferred name to Microsoft.

Important

This value is not localized.

You can request changes to your 'Saved to...' name by submitting an [Environment Change Request form](https://aka.ms/cspp-update). Any changes to Microsoft-configured settings **will take 4-5 weeks to fully roll out**. This applies to both the production and test environments

## Redirect domain allow list

Note

This setting is only relevant for hosts using the [**business user flow**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business).

When validating that a business user has an Microsoft 365 subscription, Microsoft 365 for the web navigates the user off of the host site so they can sign in to their Microsoft 365 account. Once the user has signed in, Microsoft 365 for the web will navigate back to the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) provided by the host initially.

In order for that redirection to happen, the domain of the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) must be on the redirect domain allow list. Like the WOPI domain allow list, entries on this list are implicitly wild-carded. The entries on this list might be different than those on the WOPI domain allow list.

Microsoft 365 for the web also uses the [DownloadUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#downloadurl) as part of the [business user flow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business), and the domain for this URL must also be included on the redirect domain allow list.

You can request changes to your Redirect domain allow list by submitting an [Environment Change Request form](https://aka.ms/cspp-update). Any changes to Microsoft-configured settings **will take 4-5 weeks to fully roll out**. This applies to both the production and test environments

## Homepage URL

Note

This setting is only relevant for hosts using the [**business user flow**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business).

As part of the [Business User Flow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business), Microsoft 365 for the web may determine that a user does not have the Microsoft 365 subscription necessary for editing documents using Microsoft 365 for the web. In this case Microsoft 365 for the web offers to redirect the user back to the host. However, navigating the user to the [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl) does not make sense in this case since the user does not have the appropriate subscription to edit, so Microsoft 365 for the web will not load properly.

Thus, in this case Microsoft 365 for the web navigates the user to a URL determined by the host, called the Homepage URL. This is a single setting per WOPI host and must be changed by Microsoft.

In this scenario, Microsoft 365 for the web navigates the user to a URL determined by the host, called the Homepage URL. This is a single setting per WOPI host and must be changed by Microsoft.
