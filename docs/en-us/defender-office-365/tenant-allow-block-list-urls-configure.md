<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-urls-configure -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# Allow or block URLs using the Tenant Allow/Block List

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In all organizations with cloud mailboxes, admins can create and manage entries for URLs in the Tenant Allow/Block List. For more information about the Tenant Allow/Block List, see [Manage allows and blocks in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about).

Note

To allow phishing URLs from non-Microsoft phishing simulations, use the [advanced delivery policy configuration](https://learn.microsoft.com/en-us/defender-office-365/advanced-delivery-policy-configure) to specify the URLs. Don't use the Tenant Allow/Block List.

This article describes how admins can manage entries for URLs in the Microsoft Defender portal and in Exchange Online PowerShell.

## What do you need to know before you begin?

- You open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com). To go directly to the **Tenant Allow/Block List** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList). To go directly to the **Submissions** page, use [https://security.microsoft.com/reportsubmission](https://security.microsoft.com/reportsubmission).
- To connect to Exchange Online PowerShell, see [Connect to Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell).
- For URL entry syntax, see [URL syntax for the Tenant Allow/Block List](#url-syntax-for-the-tenant-allowblock-list).
- 

  - Entry limits for URLs:
  - **Microsoft 365 organizations without Defender for Office 365**: A maximum of 1000 total URL entries:

    - Allow entries: 500 maximum.
    - Block entries: 500 maximum.

  - **Microsoft 365 organizations with Defender for Office 365 Plan 1 \(included or in an add-on subscription\)**: A maximum of 2000 total URL entries:

    - Allow entries: 1000 maximum.
    - Block entries: 1000 maximum.

  - **Microsoft 365 organizations with Defender for Office 365 Plan 2 \(included or in an add-on subscription\)**: A maximum of 15000 total URL entries:

    - Allow entries: 5000 maximum.
    - Block entries: 10000 maximum.

- You can enter a maximum of 250 characters in a URL entry.
- An entry should be active within 5 minutes.
- You need to be assigned permissions before you can do the procedures in this article. You have the following options:

  - [Microsoft Defender XDR Unified role based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) \(If **Email & collaboration** > **Defender for Office 365** permissions is ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) **Active**. Affects the Defender portal only, not PowerShell\):

    - *Add and remove entries from the Tenant Allow/Block List*: Membership assigned with the following permissions:

      - **Authorization and settings/Security settings/Detection tuning \(manage\)**

    - *Read-only access to the Tenant Allow/Block List*:

      - **Authorization and settings/Security settings/Read-only**.
      - **Authorization and settings/Security settings/Core Security settings \(read\)**.

  - [Exchange Online permissions](https://learn.microsoft.com/en-us/exchange/permissions-exo/permissions-exo):

    - *Add and remove entries from the Tenant Allow/Block List*: Membership in one of the following role groups:

      - **Organization Management** or **Security Administrator** \(Security admin role\).
      - **Security Operator** \(Tenant AllowBlockList Manager role\): This permission works only when assigned directly in the **Exchange admin center** at [https://admin.exchange.microsoft.com](https://admin.exchange.microsoft.com) > **Roles** > **Admin Roles**.

    - *Read-only access to the Tenant Allow/Block List*: Membership in one of the following role groups:

      - **Global Reader**
      - **Security Reader**
      - **View-Only Configuration**
      - **View-Only Organization Management**

  - [Microsoft Entra built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal): Membership in the **Global Administrator**<sup>\*</sup>, **Security Administrator**, **Global Reader**, or **Security Reader** roles gives users the required permissions *and* permissions for other features in Microsoft 365.

    Important

    \<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Create allow entries for URLs

Unnecessary allow entries expose your organization to malicious email that the system would otherwise filter, so there are limitations for creating allow entries directly in the Tenant Allow/Block List.

To create allow entries for URLs, use either of the following methods:

- From the **URLs** tab on the **Submissions** page at [https://security.microsoft.com/reportsubmission?viewid=url](https://security.microsoft.com/reportsubmission?viewid=url). When you submit a blocked URL as **I've confirmed it's clean**, you can select **Allow this URL** to add and allow entry for the URL on the **URLs** tab on the **Tenant Allow/Block Lists** page. For instructions, see [Report good URLs to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-good-urls-to-microsoft).

  This method is required to override malware and high confidence phishing verdicts.
- From the **URLs** tab on the **Tenant Allow/Block Lists** page or in PowerShell, as described in the following procedures.

  This method is available to override the following verdicts only:

  - Bulk
  - Spam
  - High confidence spam
  - Phishing \(not high confidence phishing\)

Tip

Allow entries from submissions are added during mail flow based on the filters that determined the message was malicious. For example, if the sender email address and a URL in the message are determined to be malicious, an allow entry is created for the sender \(email address or domain\) and the URL.

During mail flow or time of click, if messages containing the entities in the allow entries pass other checks in the filtering stack, the messages are delivered \(all filters associated with the allowed entities are skipped\). For example, if a message passes [email authentication checks](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-about), URL filtering, and file filtering, a message from an allowed sender email address is delivered if it's also from an allowed sender.

By default, allow entries for [domains and email addresses](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-good-email-to-microsoft), [files](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-good-email-attachments-to-microsoft), and [URLs](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-good-urls-to-microsoft) are kept for 45 days after the filtering system determines that the entity is clean, and then the allow entry is removed. Or you can set allow entries to expire up to 30 days after you create them. Allow entries for [spoofed senders](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure#create-allow-entries-for-spoofed-senders) never expire.

> During time of click, the URL allow entry overrides all filters associated with the URL entity, which allows users to access the URL.
> 
> A URL allow entry doesn't prevent the URL from being wrapped by Safe Links protection in Defender for Office 365. For more information, see [Do not rewrite list in SafeLinks](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).

### Use the Microsoft Defender portal to create allow entries for URLs in the Tenant Allow/Block List

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Rules** section > **Tenant Allow/Block Lists**. Or, to go directly to the **Tenant Allow/Block List** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. On the **Tenant Allow/Block List** page, select the **URLs** tab.
3. On the **URLs** tab, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Add**, and then select **Allow**.
4. In the **Allow URLs** flyout that opens, configure the following settings:

   - **Add URLs with wildcards**: Enter one URL per line, up to a maximum of 20. For details about the syntax for URL entries, see [URL syntax for the Tenant Allow/Block List](#url-syntax-for-the-tenant-allowblock-list).
   - **Remove allow entry after**: Select from the following values:

     - **45 days after last used date** \(default\)
     - **1 day**
     - **7 days**
     - **Specific date**: The maximum value is 30 days from today.

   - **Optional note**: Enter descriptive text for why you're allowing the URLs.


   When you're finished in the **Allow URLs** flyout, select **Add**.

Back on the **URLs** tab, the entry is listed.

#### Use PowerShell to create allow entries for URLs in the Tenant Allow/Block List

In [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), use the following syntax to create allow entries for URLs in the Tenant Allow/Block List:

```powershell
New-TenantAllowBlockListItems -ListType Url -Allow -Entries "Value1","Value2",..."ValueN" [-RemoveAfter 45]  [-Notes <String>]
```

This example adds an allow entry for the URL abc.contoso.com and all email addresses \(for example, xyz@abc.contoso.com\). Because we didn't use the ExpirationDate or RemoverAfter parameters, the entry expires after 45 days from last used date.

```powershell
New-TenantAllowBlockListItems -ListType Url -Allow -Entries abc.contoso.com
```

For detailed syntax and parameter information, see [New-TenantAllowBlockListItems](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/new-tenantallowblocklistitems).

## Create block entries for URLs

Email messages that contain URLs from block entries in the Tenant Allow/Block List are blocked as *high confidence phishing*. Messages that contain the blocked URLs are quarantined.

To create block entries for URLs, use either of the following methods:

- From the **URLs** tab on the **Submissions** page at [https://security.microsoft.com/reportsubmission?viewid=url](https://security.microsoft.com/reportsubmission?viewid=url). When you submit a message as **I've confirmed it's a threat**, you can select **Block this URL** to add a block entry to the **URLs** tab on the **Tenant Allow/Block Lists** page. For instructions, see [Report questionable URLs to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#report-questionable-urls-to-microsoft).
- From the **URLs** tab on the **Tenant Allow/Block Lists** page or in PowerShell, as described in the following procedures.

### Use the Microsoft Defender portal to create block entries for URLs in the Tenant Allow/Block List

Perform the following steps to create block entries for URLs in the Microsoft Defender portal.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Rules** section > **Tenant Allow/Block Lists**. Or, to go directly to the **Tenant Allow/Block List** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. On the **Tenant Allow/Block List** page, select the **URLs** tab.
3. On the **URLs** tab, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Add**, and then select **Block**.
4. In the **Block URLs** flyout that opens, configure the following settings:

   - **Add URLs with wildcards**: Enter one URL per line, up to a maximum of 20. For details about the syntax for URL entries, see [URL syntax for the Tenant Allow/Block List](#url-syntax-for-the-tenant-allowblock-list).
   - **Remove block entry after**: Select from the following values:

     - **Never expire**
     - **1 day**
     - **7 days**
     - **30 days** \(default\)
     - **Specific date**: The maximum value is 90 days from today.

   - **Optional note**: Enter descriptive text for why you're blocking the URLs.


   When you're finished in the **Block URLs** flyout, select **Add**.

Back on the **URLs** tab, the entry is listed.

#### Use PowerShell to create block entries for URLs in the Tenant Allow/Block List

In [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), use the following syntax to create block entries for URLs in the Tenant Allow/Block List with either an expiration date or no expiration:

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate <Date> | -NoExpiration> [-Notes <String>]
```

This example adds a block entry for the URL contoso.com and all subdomains \(for example, contoso.com and xyz.abc.contoso.com\). Because we didn't use the ExpirationDate or NoExpiration parameters, the entry expires after 30 days.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries *contoso.com
```

For detailed syntax and parameter information, see [New-TenantAllowBlockListItems](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/new-tenantallowblocklistitems).

## Use the Microsoft Defender portal to view entries for URLs in the Tenant Allow/Block List

In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Tenant Allow/Block Lists** in the **Rules** section. Or, to go directly to the **Tenant Allow/Block Lists** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).

Select the **URLs** tab.

On the **URLs** tab, you can sort the entries by clicking on an available column header. The following columns are available:

- **Value**: The URL.
- **Action**: The available values are **Allow** or **Block**.
- **Override verdicts**: The available values are:

  - **Up to malware** for block entries.
  - **Up to regular confidence phishing** for allow entries created directly from Tenant Allow/Block List.
  - **Up to malware** for allow entries created via submissions. Allow entries created via submissions automatically update directly created allow entries.

- **Modified by**
- **Last updated**
- **Last used date**: The date the entry was last used in the filtering system to override the verdict.
- **Remove on**: The expiration date.
- **Notes**

To filter the entries, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-filter.png) **Filter**. The following filters are available in the **Filter** flyout that opens:

- **Action**: The available values are **Allow** and **Block**.
- **Never expire**: ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) or ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-off.png)
- **Last updated**: Select **From** and **To** dates.
- **Last used date**: Select **From** and **To** dates.
- **Remove on**: Select **From** and **To** dates.
- **Modified by**: Provide an incomplete or complete email address to search by it.

When you're finished in the **Filter** flyout, select **Apply**. To clear the filters, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-clear-filters.png) **Clear filters**.

Use the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-search.png) **Search** box and a corresponding value to find specific entries.

To group the entries, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-group.png) **Group** and then select **Action**. To ungroup the entries, select **None**.

### Use PowerShell to view entries for URLs in the Tenant Allow/Block List

In [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), use the following syntax to retrieve URL entries from the Tenant Allow/Block List, optionally filtered by action, URL value, or expiration:

```powershell
Get-TenantAllowBlockListItems -ListType Url [-Allow] [-Block] [-Entry <URLValue>] [<-ExpirationDate <Date> | -NoExpiration>]
```

This example returns all allowed and blocked URLs.

```powershell
Get-TenantAllowBlockListItems -ListType Url
```

This example filters the results by blocked URLs.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

For detailed syntax and parameter information, see [Get-TenantAllowBlockListItems](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-tenantallowblocklistitems).

## Use the Microsoft Defender portal to modify entries for URLs in the Tenant Allow/Block List

In existing URL entries, you can change the expiration date and note.

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Rules** section > **Tenant Allow/Block Lists**. Or, to go directly to the **Tenant Allow/Block Lists** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. Select the **URLs** tab
3. On the **URLs** tab, select the entry from the list by selecting the check box next to the first column, and then select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-edit.png) **Edit** action that appears.
4. In the **Edit URL** flyout that opens, the following settings are available:

   - **Block entries**:

     - **Remove block entry after**: Select from the following values:

       - **1 day**
       - **7 days**
       - **30 days**
       - **Never expire**
       - **Specific date**: The maximum value is 90 days from today.

     - **Optional note**

   - **Allow entries**:

     - **Remove allow entry after**: Select from the following values:

       - **1 day**
       - **7 days**
       - **30 days**
       - **45 days after last used date**
       - **Specific date**: The maximum value is 30 days from today.

     - **Optional note**


   When you're finished in the **Edit URL** flyout, select **Save**.

Tip

In the details flyout of an entry on the **URLs** tab, use ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-view-submission.png) **View submission** at the top of the flyout to go to the details of the corresponding entry on the **Submissions** page. This action is available if a submission was responsible for creating the entry in the Tenant Allow/Block List.

### Use PowerShell to modify entries for URLs in the Tenant Allow/Block List

In [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), use the following syntax to modify existing URL entries in the Tenant Allow/Block List \(for example, to change expiration dates or notes\):

```powershell
Set-TenantAllowBlockListItems -ListType Url <-Ids <Identity value> | -Entries <Value>> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

This example changes the expiration date of the block entry for the specified URL.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Entries "~contoso.com" -ExpirationDate "9/1/2022"
```

For detailed syntax and parameter information, see [Set-TenantAllowBlockListItems](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-tenantallowblocklistitems).

## Use the Microsoft Defender portal to remove entries for URLs from the Tenant Allow/Block List

1. In the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Policies & rules** > **Threat policies** > **Rules** section > **Tenant Allow/Block Lists**. Or, to go directly to the **Tenant Allow/Block List** page, use [https://security.microsoft.com/tenantAllowBlockList](https://security.microsoft.com/tenantAllowBlockList).
2. Select the **URLs** tab.
3. On the **URLs** tab, do one of the following steps:

   - Select the entry from the list by selecting the check box next to the first column, and then select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** action that appears.
   - Select the entry from the list by clicking anywhere in the row other than the check box. In the details flyout that opens, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** at the top of the flyout.

     Tip

     To see details about other entries without leaving the details flyout, use ![](https://learn.microsoft.com/en-us/defender-office-365/media/updownarrows.png) **Previous item** and **Next item** at the top of the flyout.

4. In the warning dialog that opens, select **Delete**.

Back on the **URLs** tab, the entry is no longer listed.

Tip

You can select multiple entries by selecting each check box, or select all entries by selecting the check box next to the **Value** column header.

### Use PowerShell to remove entries for URLs from the Tenant Allow/Block List

In [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), use the following syntax to remove URL entries from the Tenant Allow/Block List by entry ID or URL value:

```powershell
Remove-TenantAllowBlockListItems -ListType Url <-Ids <Identity value> | -Entries <Value>>
```

This example removes the block entry for the specified URL from the Tenant Allow/Block List.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Entries "*cohovineyard.com
```

For detailed syntax and parameter information, see [Remove-TenantAllowBlockListItems](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/remove-tenantallowblocklistitems).

## URL syntax for the Tenant Allow/Block List

- IPv4 and IPv6 addresses are allowed, but TCP/UDP ports aren't.
- Filename extensions aren't allowed \(for example, test.pdf\).
- Unicode isn't supported, but Punycode is.
- Hostnames are allowed if all of the following statements are true:

  - The hostname contains a period.
  - There is at least one character to the left of the period.
  - There are at least two characters to the right of the period.


  For example, `t.co` is allowed; `.com` or `contoso.` aren't allowed.

- Subpaths aren't implied for allow entries.

  For example, `contoso.com` doesn't include `contoso.com/a`.
- Wildcards \(\*\) are allowed in the following scenarios:

  - A period must follow a left wildcard to specify a subdomain. \(applicable only for block entries\)

    For example, `*.contoso.com` is allowed; `*contoso.com` isn't allowed.
  - A right wildcard must follow a forward slash \(/\) to specify a path.

    For example, `contoso.com/*` is allowed; `contoso.com*` or `contoso.com/ab*` aren't allowed.
  - `*.com*` is invalid \(not a resolvable domain and the right wildcard doesn't follow a forward slash\).
  - Wildcards aren't allowed in IP addresses.

- The tilde \(~\) character is available in the following scenarios:

  - A left tilde implies a domain and all subdomains.

    For example, `~contoso.com` includes `contoso.com` and `*.contoso.com`.

- A username or password isn't supported or required.
- Quotes \(' or "\) are invalid characters.
- A URL should include all redirects where possible.

### URL entry scenarios

The following scenarios describe valid URL entries and their matching results for allow and block actions.

#### Scenario: Top-level domain blocking

**Entry**: `*.<TLD>/*`

- **Block match**:

  - `a.TLD`
  - `TLD/abcd`
  - `b.abcd.TLD`
  - `TLD/contoso.com`
  - `TLD/q=contoso.com`
  - `www.abcd.com\xyz.TLD`
  - `www.abcd.com\xyz.TLD?q=1234`
  - `www.abcd.TLD`
  - `www.abcd.TLD/q=a@contoso.com`

#### Scenario: No wildcards

**Entry**: `contoso.com`

- **Allow match**: contoso.com
- **Allow not matched**:

  - `abc-contoso.com`
  - `contoso.com/a`
  - `abc.xyz.contoso.com/a/b/c`
  - `payroll.contoso.com`
  - `fabrikam.com.com/contoso.com`
  - `fabirkam.com/q=contoso.com`
  - `www.contoso.com`
  - `www.contoso.com/q=a@contoso.com`

- **Block match**:

  - `contoso.com`
  - `contoso.com/a`
  - `abc.xyz.contoso.com/a/b/c`
  - `payroll.contoso.com`
  - `fabrikam.com/contoso.com`
  - `fabrikam.com/q=contoso.com`
  - `www.contoso.com`
  - `www.contoso.com/q=a@contoso.com`

- **Block not matched**: `abc-contoso.com`

#### Scenario: Left wildcard \(subdomain\)

Tip

Allow entries of this pattern are supported only from [advanced delivery policy configuration](https://learn.microsoft.com/en-us/defender-office-365/advanced-delivery-policy-configure).

**Entry**: `*.contoso.com`

- **Allow match** and **Block match**:

  - `www.contoso.com`
  - `xyz.abc.contoso.com`

- **Allow not matched** and **Block not matched**:

  - `123contoso.com`
  - `contoso.com`
  - `fabrikam.com/contoso.com`
  - `www.contoso.com/abc`

#### Scenario: Right wildcard at top of path

**Entry**: `contoso.com/a/*`

- **Allow match** and **Block match**:

  - `contoso.com/a/b`
  - `contoso.com/a/b/c`
  - `contoso.com/a/?q=joe@t.com`

- **Allow not matched** and **Block not matched**:

  - `contoso.com`
  - `contoso.com/a`
  - `www.contoso.com`
  - `www.contoso.com/q=a@contoso.com`

#### Scenario: Left tilde

Tip

Allow entries of this pattern are supported only from [advanced delivery policy configuration](https://learn.microsoft.com/en-us/defender-office-365/advanced-delivery-policy-configure).

**Entry**: `~contoso.com`

- **Allow match** and **Block match**:

  - `contoso.com`
  - `www.contoso.com`
  - `xyz.abc.contoso.com`

- **Allow not matched** and **Block not matched**:

  - `123contoso.com`
  - `contoso.com/abc`
  - `www.contoso.com/abc`

#### Scenario: Right wildcard suffix

**Entry**: `contoso.com/*`

- **Allow match** and **Block match**:

  - `contoso.com/?q=whatever@fabrikam.com`
  - `contoso.com/a`
  - `contoso.com/a/b/c`
  - `contoso.com/ab`
  - `contoso.com/b`
  - `contoso.com/b/a/c`
  - `contoso.com/ba`

- **Allow not matched** and **Block not matched**: contoso.com

#### Scenario: Left wildcard subdomain and right wildcard suffix

Tip

Allow entries of this pattern are supported only from [advanced delivery policy configuration](https://learn.microsoft.com/en-us/defender-office-365/advanced-delivery-policy-configure).

**Entry**: `*.contoso.com/*`

- **Allow match** and **Block match**:

  - `abc.contoso.com/ab`
  - `abc.xyz.contoso.com/a/b/c`
  - `www.contoso.com/a`
  - `www.contoso.com/b/a/c`
  - `xyz.contoso.com/ba`

- **Allow not matched** and **Block not matched**: `contoso.com/b`

#### Scenario: Left and right tilde

Tip

Allow entries of this pattern are supported only from [advanced delivery policy configuration](https://learn.microsoft.com/en-us/defender-office-365/advanced-delivery-policy-configure).

**Entry**: `~contoso.com~`

- **Allow match** and **Block match**:

  - `contoso.com`
  - `contoso.com/a`
  - `www.contoso.com`
  - `www.contoso.com/b`
  - `xyz.abc.contoso.com`
  - `abc.xyz.contoso.com/a/b/c`
  - `contoso.com/b/a/c`
  - `fabrikam.com/contoso.com`

- **Allow not matched** and **Block not matched**:

  - `123contoso.com`
  - `contoso.org`
  - `fabrikam.com/q=contoso.com`

#### Scenario: IP address

**Entry**: `1.2.3.4`

- **Allow match** and **Block match**: `1.2.3.4`
- **Allow not matched** and **Block not matched**:

  - `1.2.3.4/a`
  - `11.2.3.4/a`

#### IP address with right wildcard

**Entry**: `1.2.3.4/*`

- **Allow match** and **Block match**:

  - `1.2.3.4/b`
  - `1.2.3.4/baaaa`

### Examples of invalid entries

The following entries are invalid:

- **Missing or invalid domain values**:

  - `contoso`
  - `*.contoso.*`
  - `*.com`
  - `*.pdf`

- **Wildcard on text or without spacing characters**:

  - `*contoso.com`
  - `contoso.com*`
  - `*1.2.3.4`
  - `1.2.3.4*`
  - `contoso.com/a*`
  - `contoso.com/ab*`

- **IP addresses with ports**:

  - `contoso.com:443`
  - `abc.contoso.com:25`

- **Non-descriptive wildcards**:

  - `*`
  - `*.*`

- **Middle wildcards**:

  - `conto\*so.com`
  - `conto~so.com`

- **Double wildcards**

  - `contoso.com/**`
  - `contoso.com/*/*`

## Related articles

- [Use the Submissions page to submit suspected spam, phish, URLs, legitimate email getting blocked, and email attachments to Microsoft](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin)
- [Report false positives and false negatives](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages)
- [Manage allows and blocks in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about)
- [Allow or block files in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-files-configure)
- [Allow or block emails in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-email-spoof-configure)
- [Allow or block IPv6 addresses in the Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-ip-addresses-configure)
