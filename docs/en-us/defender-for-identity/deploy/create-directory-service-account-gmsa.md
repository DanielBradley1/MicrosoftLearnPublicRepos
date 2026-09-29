<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/create-directory-service-account-gmsa -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# Configure a gMSA directory service account for Defender for Identity

Create and configure a [group managed service account \(gMSA\)](https://learn.microsoft.com/en-us/windows-server/security/group-managed-service-accounts/getting-started-with-group-managed-service-accounts) for the sensor v2.x to use when reading Active Directory data \(querying objects, tracking changes, resolving entities\). This is separate from the [action account](https://learn.microsoft.com/en-us/defender-for-identity/deploy/manage-action-accounts) used to perform remediation actions like disabling users or resetting passwords. Before you begin, review the [prerequisites](#prerequisites) for creating a gMSA for sensor v2.x deployments.

Important

This configuration applies to the sensor v2.x only. The sensor v3.x uses LocalSystem for all AD interactions and doesn't require a gMSA or any other Directory Service Account. If all your sensors are v3.x, skip this page.

## Prerequisites

Before you create the gMSA account, make sure the following prerequisites are met:

- Make sure you have permissions to create gMSAs and security groups in Active Directory.
- Assign permissions that allow the sensor to retrieve the gMSA password.
- Choose how to configure password retrieval:

  - Assign the gMSA account directly to each of the sensors.
  - Use a group that contains all the sensors that need to use the gMSA account.

- Choose the appropriate group based on your deployment:

  - **Single-forest, single-domain deployment**:

    - Use the built-in Domain Controllers security group if you're not installing sensors on Active Directory Federation Services \(AD FS\) or Active Directory Certificate Services \(AD CS\) servers.

  - **Forest with multiple domains**:

    - If you use a single Directory service account \(DSA\), we recommend creating a universal group and adding each of the domain controllers and AD FS or AD CS servers to the universal group.
    - In multi-forest or multi-domain environments, make sure the domain where you create the gMSA trusts the sensors’ computer accounts.
    - **Option 1**: Use a gMSA per domain. Create a Domain Local group in each domain that includes only the sensors computer accounts from that domain so that only those sensors can retrieve the gMSAs' passwords and perform the local domain authentications.
    - **Option 2**: Use ashared gMSA across all domains. Create a Universal group at forest root that includes all sensors computer accounts so that all sensors can retrieve the gMSAs' password and perform the cross-domain authentications.

## Create the gMSA account

Important

If you are working in a single forest with multiple domains or sub domains and you intend to use a single gMSA account and single group at the root level, then the steps in this section must be performed with an account that has Enterprise Admin permissions.

1. If you've never used a gMSA account before, you might need to generate a new root key for the Microsoft Group Key Distribution Service \(KdsSvc\) within Active Directory. This step is required only once per forest. To generate a new root key for immediate use, run the following command:

   ```powershell
   Add-KdsRootKey -EffectiveImmediately
   ```


   Although the command name suggests that the key takes effect immediately, wait 10 hours for the KDS root key to replicate and become available on all domain controllers.


   If your test domain has only one domain controller, you can expedite the process by setting the key's effective time to 10 hours earlier.


   Important


   Don't use this technique in a production environment.


   ```powershell
   # For single-DC test environments only
   Add-KdsRootKey -EffectiveTime (Get-Date).AddHours(-10)
   ```

2. Run the PowerShell commands as an administrator. This script will:

   - Create a gMSA account.
   - Create a group for the gMSA account.
   - Add the specified computer accounts to that group.
   - Configure the gMSA to use AES128 and AES256 Kerberos encryption.

3. Before running the script:

   - Update the variable values to match your environment.
   - Make sure to give each gMSA a unique name for each forest or domain.

Define the gMSA creation variables, including the account name, host group, and computer accounts, then run the following script to provision the gMSA:

```powershell
# Variables:
# Specify the name of the gMSA you want to create:
$gMSA_AccountName = 'mdiSvc01'
# Specify the name of the group you want to create for the gMSA,
# or enter 'Domain Controllers' to use the built-in group when your environment is a single forest, and will contain only domain controller sensors.
$gMSA_HostsGroupName = 'mdiSvc01Group'
# Specify the computer accounts that will become members of the gMSA group and have permission to use the gMSA. 
# If you are using the 'Domain Controllers' group in the $gMSA_HostsGroupName variable, then this list is ignored
$gMSA_HostNames = 'DC1', 'DC2', 'DC3', 'DC4', 'DC5', 'DC6', 'ADFS1', 'ADFS2'

# Import the required PowerShell module:
Import-Module ActiveDirectory

# Set the group
if ($gMSA_HostsGroupName -eq 'Domain Controllers') {
    $gMSA_HostsGroup = Get-ADGroup -Identity 'Domain Controllers'
} else {
	# If this group is being created at the root of a forest and will be used across multiple domains or subdomains then the -GroupScope parameter should be changed to Universal
    $gMSA_HostsGroup = New-ADGroup -Name $gMSA_HostsGroupName -GroupScope DomainLocal -PassThru
    $gMSA_HostNames | ForEach-Object { Get-ADComputer -Identity $_ } |
        ForEach-Object { Add-ADGroupMember -Identity $gMSA_HostsGroupName -Members $_ }
}

# Specify the Kerberos encryption type as AES.
$kerberosEncType = ('AES128','AES256')

# Create the gMSA:
New-ADServiceAccount -Name $gMSA_AccountName -DNSHostName "$gMSA_AccountName.$env:USERDNSDOMAIN" `
 -PrincipalsAllowedToRetrieveManagedPassword $gMSA_HostsGroup -KerberosEncryptionType $kerberosEncType
```

## Refresh Kerberos tickets after changing group membership

The Kerberos ticket has a list of groups that an entity is a member of when the ticket is issued. If you add a computer account to the universal group after it already received a Kerberos ticket, it can't retrieve the gMSA's password until it gets a new ticket.

To refresh the Kerberos ticket, you can:

- **Wait for new Kerberos ticket to be issued**. Kerberos tickets are typically valid for 10 hours.
- **Reboot the server** to request a new Kerberos ticket with the new group membership.
- **Purge the existing Kerberos tickets** to force the domain controller to request a new Kerberos ticket. Run the following command to purge the tickets, from an administrator command prompt on the domain controller: `klist purge -li 0x3e7`

## Grant required directory service account permissions

The directory service account requires specific read permissions on Active Directory objects so that the sensor can query directory data. The following include details the required permissions and how to grant them:

The DSA requires read only permissions on **all** the objects in Active Directory, including the **Deleted Objects Container**.

The read-only permissions on the **Deleted Objects** container allows Defender for Identity to detect user deletions from your Active Directory.

Use the following code sample to help you grant the required read permissions on the **Deleted Objects** container, whether or not you're using a gMSA account.

Tip

If the DSA you want to grant the permissions to is a Group Managed Service Account \(gMSA\), you must first create a security group, add the gMSA as a member, and add the permissions to that group. For more information, see [Configure a Directory Service Account for Defender for Identity with a gMSA](https://learn.microsoft.com/en-us/defender-for-identity/deploy/create-directory-service-account-gmsa).

```powershell
# Declare the identity that you want to add read access to the deleted objects container:
$Identity = 'mdiSvc01'

# If the identity is a gMSA, first to create a group and add the gMSA to it:
$groupName = 'mdiUsr01Group'
$groupDescription = 'Members of this group are allowed to read the objects in the Deleted Objects container in AD'
if(Get-ADServiceAccount -Identity $Identity -ErrorAction SilentlyContinue) {
    $groupParams = @{
        Name           = $groupName
        SamAccountName = $groupName
        DisplayName    = $groupName
        GroupCategory  = 'Security'
        GroupScope     = 'Universal'
        Description    = $groupDescription
    }
    $group = New-ADGroup @groupParams -PassThru
    Add-ADGroupMember -Identity $group -Members ('{0}$' -f $Identity)
    $Identity = $group.Name
}

# Get the deleted objects container's distinguished name:
$distinguishedName = ([adsi]'').distinguishedName.Value
$deletedObjectsDN = 'CN=Deleted Objects,{0}' -f $distinguishedName

# Take ownership on the deleted objects container:
$params = @("$deletedObjectsDN", '/takeOwnership')
C:\Windows\System32\dsacls.exe $params

# Grant the 'List Contents' and 'Read Property' permissions to the user or group:
$params = @("$deletedObjectsDN", '/G', ('{0}\{1}:LCRP' -f ([adsi]'').name.Value, $Identity))
C:\Windows\System32\dsacls.exe $params
  
# To remove the permissions, uncomment the next 2 lines and run them instead of the two prior ones:
# $params = @("$deletedObjectsDN", '/R', ('{0}\{1}' -f ([adsi]'').name.Value, $Identity))
# C:\Windows\System32\dsacls.exe $params
```

For more information, see [Changing permissions on a deleted object container](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc816824\(v=ws.10\)).

## Verify that the gMSA account has the required rights

The Defender for Identity sensor service, *Azure Advanced Threat Protection Sensor*, runs as a *LocalService* that impersonates the DSA account. If the *Log on as a service* policy is configured but the permission wasn't granted to the gMSA account, the impersonation fails. In that case, you see the following health issue: **Directory services user credentials are incorrect.**

If you see the health issue **Directory services user credentials are incorrect**, check to see if the *Log on as a service policy* is configured either in a Group Policy setting or in a Local Security Policy.

### Check the Local Security Policy

To verify the local policy assignment, perform the following steps:

1. Run `secpol.msc`
2. Select **Local Policies** > **User Rights Assignment**
3. Open the **Log on as a service policy** setting.

   ![Screenshot of the log on as a service property.](https://learn.microsoft.com/en-us/defender-for-identity/media/log-on-as-a-service.png)
4. Once the policy is enabled, add the gMSA account to the list of accounts that can log on as a service.

### Check the Group Policy setting

To verify whether Group Policy configures this setting, perform the following steps:

1. Run `rsop.msc`
2. Go to **Computer Configuration -> Windows Settings -> Security Settings -> Local Policies -> User Rights Assignment -> Log on as a service.**

   [![Screenshot of the Log on as a service policy in the Group Policy Management Editor.](https://learn.microsoft.com/en-us/defender-for-identity/media/log-on-as-a-service-gpmc.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/log-on-as-a-service-gpmc.png#lightbox)
3. Once the setting is configured, add the gMSA account to the list of accounts that can log on as a service in the Group Policy Management Editor.

Note

If you use the Group Policy Management Editor to configure the **Log on as a service** setting, make sure to add both **NT Service\\All Services** and the gMSA account you created.

## Configure a directory service account in the Microsoft Defender portal

To connect your sensors with your Active Directory domains, configure Directory service accounts in Microsoft Defender portal.

1. In [Microsoft Defender portal](https://security.microsoft.com/), go to **Settings > Identities**.

   [![Screenshot that shows the settings page and how to access the Defender for Identity page.](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/settings-identities.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/detect-exclusions/settings-identities.png#lightbox)
2. Select **Directory service accounts** to see which accounts are associated with which domains.

   [![Screenshot that shows the Directory service accounts page in the Defender portal.](https://learn.microsoft.com/en-us/defender-for-identity/media/directory-service-accounts.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/directory-service-accounts.png#lightbox)
3. Select **Add credentials**
4. Enter the following details:

   - **Account name**
   - **Domain**
   - **Password**

5. You can choose if it's a **Group managed service account** \(gMSA\), or if it belongs to a **Single label domain**.

   [![Screenshot of the added credentials pane.](https://learn.microsoft.com/en-us/defender-for-identity/media/new-directory-service-account.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/new-directory-service-account.png#lightbox)

   | Field | Comments |
   | --- | --- |
   | **Account name** \(required\) | Enter the read-only AD username. For example: **DefenderForIdentityUser**.  <br>  <br>- You must use a **standard** AD user or gMSA account.  <br>- **Don't** use the UPN format for your username.  <br>- When using a gMSA, the user string should end with the `$` sign. For example: `mdisvc$`  <br>  <br>**NOTE:** We recommend that you avoid using accounts assigned to specific users. |
   | **Password** \(required for standard AD user accounts\) | For AD user accounts only, generate a strong password for the read-only user. For example: `PePR!BZ&}Y54UpC3aB`. |
   | **Group managed service account** \(required for gMSA accounts\) | For gMSA accounts only, select **Group managed service account**. |
   | **Domain** \(required\) | Enter the domain for the read-only user. For example: **contoso.com**.  <br>  <br>It's important that you enter the complete FQDN of the domain where the user is located. For example, if the user's account is in domain corp.contoso.com, you need to enter `corp.contoso.com` not `contoso.com`.  <br>  <br>For more information, see [Microsoft support for Single Label Domains](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/single-label-domains-support-policy). |

6. Select **Save**.
7. \(Optional\) Select an account to open the details pane and view its settings.

   [![Screenshot of an account details pane.](https://learn.microsoft.com/en-us/defender-for-identity/media/account-settings.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/account-settings.png#lightbox)

Note

You can use the same procedure to change the password for standard Active Directory user accounts. gMSA accounts don't require passwords.

## Troubleshooting

For more information, see [Sensor failed to retrieve the gMSA credentials](https://learn.microsoft.com/en-us/defender-for-identity/troubleshooting-known-issues#sensor-failed-to-retrieve-group-managed-service-account-gmsa-credentials).
