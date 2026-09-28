<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-exchange-asmabc -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 4: Configure shared mailboxes, address books, and clients

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

This article provides information on configuring shared mailboxes, address books, and clients in Microsoft Exchange Online for education environments.

## Shared mailboxes \(optional\)

Shared mailboxes are used for collaboration between users, and they provide a group email and shared workspace for conversations, files, and calendar events. Shared mailboxes can be useful in the following examples:

1. Help Desk / IT Support: A single mailbox and email address where IT issues can be sent and a team of IT support staff can all access.
2. School System Inboxes: A single mailbox where parents, students, and community members can send issues and questions.
3. School Board: A single shared mailbox where school board members can all read and respond to issues and questions sent by email from constituents.

## Address books

The following guidance can help with address book management and administration:

1. Address book policies: Address book policies \(ABPs\) allow users to be segmented into specific groups and manage what email addresses users can see. It might not be desirable for students to see teachers’ email addresses for example; ABPs can accomplish this. ABPs can only be created via PowerShell.

   1. Turn on ABPs via PowerShell.
   2. Create ABPs.

      1. Address List role required. This role doesn't exist in any role group by default so needs to be added to an existing role group or a newly created role group
      2. Address book policies cmdlet \(New-AddressBookPolicy\) requires the following parameters:

         1. Name
         2. AddressLists
         3. GlobalAddressList
         4. OfflineAddressBook
         5. RoomList

      3. Example: New-AddressBookPolicy -Name "All Fabrikam ABP" -AddressLists "\\All Fabrikam","\\All Fabrikam Mailboxes","\\All Fabrikam DLs","\\All Fabrikam Contacts" -RoomList "\\All Fabrikam-Rooms" -OfflineAddressBook "\\Fabrikam-All-OAB" -GlobalAddressList "\\All Fabrikam"

2. Assign the ABP to users. Although this assignment can be done in the Exchange Administrator Console \(EAC\), for a large number of users, it isn't practical and PowerShell should be used. For example, to assign the “All Fabrikam ABP” policy to all users whose Department equals Fabrikam, two lines of PowerShell are used:

   1. $Fabrikam = Get-Mailbox -Filter "Department -eq 'Fabrikam'"
   2. $Fabrikam \| foreach {Set-Mailbox -Identity $\_.MicrosoftOnlineServicesID -AddressBookPolicy "All Fabrikam ABP"}

3. Address Lists: Multiple Global address lists are required to implement ABPs \(as indicated previously\) and provide the desired separation.

   1. By default, the Default Global Address List contains all recipients. Additional GALs can only be created via PowerShell.
   2. Users only see the GAL they belong to. If a user belongs to multiple GALs, the largest GAL is used.

4. Hierarchy: Hierarchical address books \(HABs\) represent address lists by using an organizational structure. Rather than all recipients listed alphabetically, HABs allow for a tiered structure. In an educational organizational structure, this could be a tier of schools, child tiers for grades, and then classrooms.

## Clients

A1 licensees use Outlook via browser/Outlook on the Web only. A3 and A5 licensees have access to the feature-complete Outlook desktop client and is recommended for those users. All email clients should support Modern Authentication and multifactor authentication \(MFA\).

The following list defines the policies governing email clients and mobility:

1. Authentication/Modern auth
2. Outlook
3. Outlook on the Web
4. Outlook for iOS and Android
5. Client access rules
