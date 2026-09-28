<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-implement -->
<!-- Sitemap-Last-Modified: 2025-10-15 -->

# Implement a cloud-first approach

It's mainly a process and policy-driven phase to stop, or limit as much as possible, adding new dependencies to Active Directory Domain Services \(AD DS\) and implement a cloud-first approach for new demand of IT solutions.

It's key at this point to identify the internal processes that would lead to adding new dependencies on AD DS. For example, most organizations would have a change management process that has to be followed before the implementation of new scenarios, features, and solutions. We strongly recommend making sure that these change approval processes are updated to:

- Include a step to evaluate whether the proposed change would add new dependencies on AD DS.
- Evaluate Microsoft Entra alternatives when possible.

## Attributes

You can enrich user attributes in Microsoft Entra ID to make more user attributes available for inclusion. Examples of common scenarios that require rich user attributes include:

- App provisioning: The data source of app provisioning is Microsoft Entra ID, and necessary user attributes must be in there.
- Application authorization: A token that Microsoft Entra ID issues can include claims generated from user attributes so that applications can make authorization decisions based on the claims in the token. It can also contain attributes coming from external data sources through a [custom claims provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview).
- Group membership population and maintenance: Dynamic membership groups enable dynamic population of groups based on user attributes, such as department information.

These two links provide guidance on making schema changes:

- [Understand the Microsoft Entra schema and custom expressions](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/concept-attributes)
- [Attributes synchronized by Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/reference-connect-sync-attributes-synchronized)

These links provide more information on this topic but aren't specific to changing the schema:

- [Use Microsoft Entra schema extension attributes in claims - Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/schema-extensions)
- [What are custom security attributes in Microsoft Entra ID \(preview\)?](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview)
- [Customize Microsoft Entra attribute mappings in application provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes)
- [Provide optional claims to Microsoft Entra apps - Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/optional-claims)

- [Attribute-based application provisioning with scoping filters](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) or [What is Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview) \(for application access\)

## Groups

A cloud-first approach for groups involves creating new groups in the cloud. If you need them on-premises, [provision groups to Active Directory Domain Services \(AD DS\) by using Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-configure-entra-to-active-directory). Convert the Group Source of Authority \(SOA\) of existing on-premises groups to manage them from Microsoft Entra.

These links provide more information about groups:

- [Create or edit a dynamic group and get status in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-create-rule)
- [Use self-service groups for user-initiated group management](https://learn.microsoft.com/en-us/entra/identity/users/groups-self-service-management)
- [Attribute-based application provisioning with scoping filters](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts) or [What is Microsoft Entra entitlement management?](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview) \(for application access\)
- [Compare groups](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/compare-groups)
- [Restrict guest access permissions in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/users-restrict-guest-permissions)

## Users

If there are users in your organization that do not have application dependencies to Active Directory, you can take a cloud-first approach by provisioning those users directly to Microsoft Entra ID. If there are users that do not require access to Active Directory, but have Active Directory accounts provisioned to them, their source of authority can be changed allowing you to clean their Active Directory account.

## Devices

Client workstations are traditionally joined to Active Directory and managed via Group Policy objects \(GPOs\) or device management solutions such as Microsoft Configuration Manager. Your teams will establish a new policy and process to prevent newly deployed workstations from being domain joined. Key points include:

- Mandate [Microsoft Entra join](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join) for new Windows client workstations to achieve "no more domain join."
- Manage workstations from the cloud by using unified endpoint management \(UEM\) solutions such as [Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune).

[Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/windows-autopilot) can help you establish a streamlined onboarding and device provisioning, which can enforce these directives.

[Windows Local Administrator Password Solution \(LAPS\)](https://learn.microsoft.com/en-us/entra/identity/devices/howto-manage-local-admin-passwords) enables a cloud-first solution to manage the passwords of local administrator accounts.

For more information, see [Learn more about cloud-native endpoints](https://learn.microsoft.com/en-us/mem/solutions/cloud-native-endpoints/cloud-native-endpoints-overview).

## Applications

Traditionally, application servers are often joined to an on-premises Active Directory domain so that they can use Windows Integrated Authentication \(Kerberos or NTLM\), directory queries through LDAP, and server management through GPO or Microsoft Configuration Manager.

The organization has a process to evaluate Microsoft Entra alternatives when it's considering new services, apps, or infrastructure. Directives for a cloud-first approach to applications should be as follows. \(New on-premises applications or legacy applications should be a rare exception when no modern alternative exists.\)

- Provide a recommendation to change the procurement policy and application development policy to require modern protocols \(OIDC/OAuth2 and SAML\) and authenticate by using Microsoft Entra ID. New apps should also support [Microsoft Entra app provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/what-is-hr-driven-provisioning) and have no dependency on LDAP queries. Exceptions require explicit review and approval.

  Important

  Depending on the anticipated demands of applications that require legacy protocols, you can choose to deploy [Microsoft Entra Domain Services](https://learn.microsoft.com/en-us/entra/identity/domain-services/overview) when more current alternatives won't work.
- Provide a recommendation to create a policy to prioritize use of cloud-native alternatives. The policy should limit deployment of new application servers to the domain. Common cloud-native scenarios to replace domain member servers include:

  - File servers:

    - SharePoint or OneDrive provides collaboration support across Microsoft 365 solutions and built-in governance, risk, security, and compliance.
    - [Azure Files](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-introduction) offers fully managed file shares in the cloud that are accessible via the industry-standard SMB or NFS protocol. Customers can use native [Microsoft Entra authentication to Azure Files](https://learn.microsoft.com/en-us/azure/virtual-desktop/create-profile-container-azure-ad) over the internet without line of sight to a domain controller.
    - Microsoft Entra ID works with third-party applications in the Microsoft [application gallery](https://learn.microsoft.com/en-us/microsoft-365/enterprise/integrated-apps-and-azure-ads).

  - Print servers:

    - If your organization has a mandate to procure [Universal Print](https://learn.microsoft.com/en-us/universal-print/)-compatible printers, see [Partner integrations](https://learn.microsoft.com/en-us/universal-print/fundamentals/universal-print-partner-integrations).
    - Bridge with the [Universal Print connector](https://learn.microsoft.com/en-us/universal-print/fundamentals/universal-print-connector-overview) for incompatible printers.

## Next steps

- [Introduction](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-introduction)
- [Cloud transformation posture](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-posture)
- [Establish a Microsoft Entra footprint](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-establish)
- [Transition to the cloud](https://learn.microsoft.com/en-us/entra/architecture/road-to-the-cloud-migrate)
