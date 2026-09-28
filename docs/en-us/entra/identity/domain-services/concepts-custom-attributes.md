<!-- Source: https://learn.microsoft.com/en-us/entra/identity/domain-services/concepts-custom-attributes -->
<!-- Sitemap-Last-Modified: 2025-03-10 -->

# Custom attributes for Microsoft Entra Domain Services

For various reasons, companies often can't modify code for legacy apps. For example, apps may use a custom attribute, such as a custom employee ID, and rely on that attribute for LDAP operations.

Microsoft Entra ID supports adding custom data to resources using [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview). Microsoft Entra Domain Services can synchronize the following types of extensions from Microsoft Entra ID, so you can also use apps that depend on custom attributes with Domain Services:

- [onPremisesExtensionAttributes](https://learn.microsoft.com/en-us/graph/extensibility-overview?tabs=http#extension-attributes) are a set of 15 attributes that can store extended user string attributes.
- [Directory extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview?tabs=http#directory-azure-ad-extensions) allow the schema extension of specific directory objects, such as users and groups, with strongly typed attributes through registration with an application in the tenant.

Both types of extensions can be configured by using Microsoft Entra Connect for users who are managed on-premises, or Microsoft Graph APIs for cloud-only users.

Note

The following types of extensions aren't supported for synchronization:

- Custom security attributes in Microsoft Entra ID
- Microsoft Graph schema extensions
- Microsoft Graph open extensions

## Requirements

The minimum SKU supported for custom attributes is the Enterprise SKU. If you use Standard, you need to [upgrade](https://learn.microsoft.com/en-us/entra/identity/domain-services/change-sku) the managed domain to Enterprise or Premium. For more information, see [Microsoft Entra Domain Pricing](https://azure.microsoft.com/pricing/details/active-directory-ds/).

## How custom attributes work

After you create a managed domain, click **Custom Attributes** under **Settings** to enable attribute synchronization. Click **Save** to confirm the change.

![Screenshot of how to enable custom attributes.](https://learn.microsoft.com/en-us/entra/identity/domain-services/media/concepts-custom-attributes/enable.png)

## Enable predefined attribute synchronization

Click **OnPremisesExtensionAttributes** to synchronize the attributes extensionAttribute1-15, also known as [Exchange custom attributes](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes).

## Synchronize Microsoft Entra directory extension attributes

These are the extended user or group attributes defined in your Microsoft Entra tenant.

Select **+ Add** to choose which custom attributes to synchronize. The list shows the available extension properties in your tenant. You can filter the list by using the search bar.

![Screenshot of how to add directory extension attributes.](https://learn.microsoft.com/en-us/entra/identity/domain-services/media/concepts-custom-attributes/add.png)

If you don't see the directory extension you are looking for, enter the extension's associated application appId and click **Search** to load only that application's defined extension properties. This search helps when multiple applications define many extensions in your tenant.

Note

If you would like to see directory extensions synchronized by Microsoft Entra Connect, click **Enterprise App** and look for the Application ID of the **Tenant Schema Extension App**. For more information, see [Microsoft Entra Connect Sync: Directory extensions](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/connect/how-to-connect-sync-feature-directory-extensions#configuration-changes-in-azure-ad-made-by-the-wizard).

Click **Select**, and then **Save** to confirm the change.

![Screenshot of how to save directory extension attributes.](https://learn.microsoft.com/en-us/entra/identity/domain-services/media/concepts-custom-attributes/select.png)

Domain Services back fills all synchronized users and groups with the onboarded custom attribute values. The custom attribute values gradually populate for objects that contain the directory extension in Microsoft Entra ID. During the backfill synchronization process, incremental changes in Microsoft Entra ID are paused, and the sync time depends on the size of the tenant.

To check the backfilling status, click **Domain Services Health** and verify the **Synchronization with Microsoft Entra ID** monitor has an updated timestamp within an hour since onboarding. Once updated, the backfill is complete.

## Reserved attributes for Active Directory Domain Services

The following attributes are reserved for Active Directory Domain Services in Windows Server. They can't be used for Microsoft Entra Domain Services.

| Name | Attribute |
| --- | --- |
| AccountDisabled | accountDisabled |
| AzureAdMailNickname | msDS-AzureADMailNickname |
| AadObjectId | msDS-aadObjectId |
| City | l |
| CommonName | cn |
| Company | company |
| Country | co |
| Department | department |
| Description | description |
| DisplayName | displayName |
| DistinguishedName | distinguishedName |
| EmployeeId | employeeId |
| ExchangeExtensions | extensionAttribute |
| ExchangeExtension1 | extensionAttribute1 |
| ExchangeExtension2 | extensionAttribute2 |
| ExchangeExtension3 | extensionAttribute3 |
| ExchangeExtension4 | extensionAttribute4 |
| ExchangeExtension5 | extensionAttribute5 |
| ExchangeExtension6 | extensionAttribute6 |
| ExchangeExtension7 | extensionAttribute7 |
| ExchangeExtension8 | extensionAttribute8 |
| ExchangeExtension9 | extensionAttribute9 |
| ExchangeExtension10 | extensionAttribute10 |
| ExchangeExtension11 | extensionAttribute11 |
| ExchangeExtension12 | extensionAttribute12 |
| ExchangeExtension13 | extensionAttribute13 |
| ExchangeExtension14 | extensionAttribute14 |
| ExchangeExtension15 | extensionAttribute15 |
| FacsimileTelephoneNumber | facsimileTelephoneNumber |
| GenerationSeq | msDS-generationSeq |
| GivenName | givenName |
| GroupType | groupType |
| LinkSeq | msDS-linkSeq |
| Mail | mail |
| Manager | manager |
| Member | member |
| MemberOf | memberOf |
| Mobile | mobile |
| ObjectClass | objectClass |
| ObjectGloballyUniqueIdentifier | objectGUID |
| Pager | pager |
| PhysicalDeliveryOfficeName | physicalDeliveryOfficeName |
| PostalCode | postalCode |
| PreferredLanguage | preferredLanguage |
| ProxyAddresses | proxyAddresses |
| PasswordLastSet | pwdLastSet |
| SamAccountName | sAMAccountName |
| SecurityDescriptor | nTSecurityDescriptor |
| SidHistory | sIDHistory |
| State | st |
| StreetAddress | streetAddress |
| Surname | sn |
| SupplementalCredentials | supplementalCredentials |
| TelephoneNumber | telephoneNumber |
| Title | title |
| UnicodePwd | unicodePwd |
| UserAccountControl | userAccountControl |
| UserPrincipalName | userPrincipalName |
| EscrowType | msDS-escrowType |
| EscrowOperation | msDS-escrowOperation |
| SourceAadObjectId | msDS-aadObjectId |
| TargetAadObjectId | msDS-targetAadObjectId |
| AadGraphLink | msDS-aadGraphLink |
| AadGraphDQLink | msDS-aadlink |
| EscrowCount | msDS-escrowCount |
| FirstSteadyStateTime | msDS-firstSteadyStateTime |
| LastSteadyStateTime | msDS-lastSteadyStateTime |
| QuarantineStartTime | msDS-quarantineStartTime |
| QuarantineSyncWaitPeriod | msDS-quarantineSyncWaitPeriod |
| SingleSyncRequests | msDS-singleSyncRequests |
| StringValues | msDS-stringValues |
| SyncRequestStatus | msDS-syncRequestStatus |
| SyncStatus | msDS-syncStatus |
| WhenChanged | whenChanged |
| DeletedObjectNumber | msDS-deletedObjectNumber |
| CustomAttributeState | msDS-customAttribute-state |
| CustomAttributeType | msDS-customAttribute-type |
| LegacyAadObjectId | msDS-AzureADObjectId |
| Name | name |
| Revision | revision |
| AdminDisplayName | adminDisplayName |
| AdminDescription | adminDescription |
| LdapDisplayName | lDAPDisplayName |
| AttributeId | attributeId |
| AttributeSyntax | attributeSyntax |
| OmSyntax | omSyntax |
| IsSingleValued | isSingleValued |
| MayContain | mayContain |
| SchemaUpdateNow | schemaUpdateNow |
| IsDefunct | isDefunct |

## Next steps

To configure onPremisesExtensionAttributes or directory extensions for cloud-only users in Microsoft Entra ID, see [Custom data options in Microsoft Graph](https://learn.microsoft.com/en-us/graph/extensibility-overview?tabs=http#custom-data-options-in-microsoft-graph).

To sync onPremisesExtensionAttributes or directory extensions from on-premises to Microsoft Entra ID, [configure Microsoft Entra Connect](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/connect/how-to-connect-sync-feature-directory-extensions).
