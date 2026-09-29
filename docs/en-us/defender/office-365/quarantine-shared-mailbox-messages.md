<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/quarantine-shared-mailbox-messages -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# View and release quarantined messages from shared mailboxes

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Users can manage quarantined messages where they're one of the recipients as described in [Find and release quarantined messages as a user](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user). But what about **shared mailboxes** where the user has Full Access and Send As or Send on Behalf permissions to the mailbox as described in [Shared mailboxes in Exchange Online](https://learn.microsoft.com/en-us/exchange/collaboration-exo/shared-mailboxes)?

Previously, the ability for users to manage quarantined messages sent to a shared mailbox required admins to leave automapping enabled for the shared mailbox \(it's enabled by default when an admin gives a user access to another mailbox\). However, depending on the size and number of mailboxes that the user has access to, performance can suffer as Outlook tries to open *all* mailboxes that the user has access to. Because Outlook performance can suffer when it tries to open all accessible mailboxes, many admins choose to [remove automapping for shared mailboxes](https://learn.microsoft.com/en-us/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Now, automapping is no longer required for users to manage quarantined messages that were sent to shared mailboxes. There are two different methods to access quarantined messages that were sent to a shared mailbox:

- If the following statements are all true:

  - An admin has configured [quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#anatomy-of-a-quarantine-policy) to allow quarantine notifications \(formerly known as end-user spam notifications\).
  - The user has access to quarantine notifications of the shared mailbox.
  - The user has Full Access permissions to the shared mailbox \(assigned directly or through a cloud-only security group\).


  The user can select **Review** in the notification to go to quarantine in the Microsoft Defender portal. Selecting **Review** in the quarantine notification only allows access to quarantined messages that were sent to the shared mailbox. Users can't manage their own quarantine messages when they access quarantine by selecting **Review** in a shared mailbox notification.

- The user can open the [Find and release quarantined messages as a user](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user) page and select **Filter** to filter the results by **Recipient address** \(the email address of the shared mailbox\). On the main **Quarantine** page, the user can select the **Recipient** column header to sort by messages that were sent to the shared mailbox.

## Requirements and limitations for shared mailbox quarantine actions

- In Microsoft 365 operated by 21Vianet in China, quarantine isn't currently available in the Microsoft Defender portal. Quarantine is available only in the classic Exchange admin center \(classic EAC\).
- *Quarantine policies* define what users can do with quarantined messages based on why the message was quarantined for [supported features](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#step-2-assign-a-quarantine-policy-to-supported-features). Default quarantine policies enforce the historical capabilities for the security feature that quarantined the message as listed in the "View your quarantined messages" table in [Find and release quarantined messages as a user](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user#view-your-quarantined-messages). Admins can create and apply custom quarantine policies that define less restrictive or more restrictive capabilities for users. For more information, see [Create quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies#step-1-create-quarantine-policies-in-the-microsoft-defender-portal).
- The first user to act on the quarantined message decides the fate of the message for everyone who uses the shared mailbox. For example, if a shared mailbox is accessed by 10 users, and a user decides to delete the quarantine message, the message is deleted for all 10 users. Likewise, if a user decides to release the message, it's released to the shared mailbox and is accessible by all other users of the shared mailbox.
- Currently, the **Block sender** button isn't available in the **Details** flyout for quarantined messages that were sent to the shared mailbox.
- If you use nested security groups to grant access to a shared mailbox, we recommend no more than two levels of nested groups. For example, Group A is a member of Group B, which is a member of Group C. To assign permissions to a shared mailbox, don't add the user to Group A, and then assign Group C to the shared mailbox.
- Users can manage quarantined messages sent to a shared mailbox when Full Access permission is assigned directly or through a cloud-only security group. Currently, quarantine management for shared mailboxes isn't supported with on-premises AD synchronized groups. Users receive a "Not authorized" error when access is granted through an on-premises Active Directory group that's synced to the cloud. Confirm that the user has access using one of the supported methods.
- As of July 2022, users with primary SMTP addresses that are different from their user principal names \(UPNs\) should be able to access quarantined messages for the shared mailbox.
- To manage quarantined messages for the shared mailbox in [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell), the user needs to use the [Get-QuarantineMessage](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-quarantinemessage) cmdlet with the shared mailbox email address for the value of the *RecipientAddress* parameter to identify the messages. For example, the following command lists quarantined messages for the shared mailbox so you can identify the message to release:

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```


  After running **Get-QuarantineMessage**, the user can select a quarantined message from the returned list to view or take action on.


  The following PowerShell example shows all of the quarantined messages that were sent to the shared mailbox, and then releases the first message in the list from quarantine \(the first message in the list is 0, the second is 1, and so on\).


  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```


  For detailed syntax and parameter information, see the following articles:


  - [Get-QuarantineMessage](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/preview-quarantinemessage)
  - [Release-QuarantineMessage](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/release-quarantinemessage)
