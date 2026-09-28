<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-three -->
<!-- Sitemap-Last-Modified: 2024-03-04 -->

# Solution 3: Microsoft Entra ID with AD FS and Shibboleth

In Solution 3, the federation provider is the primary identity provider \(IdP\). In this example, Shibboleth is the federation provider for the integration of multilateral federation apps, on-premises Central Authentication Service \(CAS\) apps, and any Lightweight Directory Access Protocol \(LDAP\) directories.

[![Diagram that shows a design integrating Shibboleth, Active Directory Federation Services, and Microsoft Entra ID.](https://learn.microsoft.com/en-us/entra/architecture/media/multilateral-federation-solution-three/shibboleth-adfs-azure-ad.png)](https://learn.microsoft.com/en-us/entra/architecture/media/multilateral-federation-solution-three/shibboleth-adfs-azure-ad.png#lightbox)

In this scenario, Shibboleth is the primary IdP. Participation in multilateral federations \(for example, with InCommon\) is done through Shibboleth, which natively supports this integration. On-premises CAS apps and the LDAP directory are also integrated with Shibboleth.

Student apps, faculty apps, and Microsoft 365 Apps are integrated with Microsoft Entra ID. Any on-premises instance of Active Directory is synced with Microsoft Entra ID. Active Directory Federation Services \(AD FS\) provides integration with third-party multifactor authentication. AD FS performs protocol translation and enables certain Microsoft Entra features, such as Microsoft Entra join for device management, Windows Autopilot, and passwordless features.

## Advantages

Here are some of the advantages of using this solution:

- **Customized authentication:** You can customize the experience for multilateral federation apps through Shibboleth.
- **Ease of execution:** The solution is simple to implement in the short term for institutions that already use Shibboleth as their primary IdP. You need to migrate student and faculty apps to Microsoft Entra ID and add an AD FS instance.
- **Minimal disruption:** The solution allows third-party multifactor authentication. You can keep existing multifactor authentication solutions, such as Duo, in place until you're ready for an update.

## Considerations and trade-offs

Here are some of the trade-offs of using this solution:

- **Higher complexity and security risk:** An on-premises footprint might mean higher complexity for the environment and extra security risks, compared to a managed service. Increased overhead and fees might also be associated with managing on-premises components.
- **Suboptimal authentication experience:** For multilateral federation and CAS apps, there's no cloud-based authentication mechanism and there might be multiple redirects.
- **No Microsoft Entra multifactor authentication support:** This solution doesn't enable Microsoft Entra multifactor authentication support for multilateral federation or CAS apps. You might miss potential cost savings.
- **No granular Conditional Access support:** The lack of granular Conditional Access support limits your ability to make granular decisions.
- **Significant ongoing staff allocation:** IT staff must maintain infrastructure and software for the authentication solution. Any staff attrition might introduce risk.

## Migration resources

The following resources can help with your migration to this solution architecture.

| Migration resource | Description |
| --- | --- |
| [Resources for migrating applications to Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/migration-resources) | List of resources to help you migrate application access and authentication to Microsoft Entra ID |

## Next steps

See these related articles about multilateral federation:

[Multilateral federation introduction](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-introduction)

[Multilateral federation baseline design](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-baseline)

[Multilateral federation Solution 1: Microsoft Entra ID with Cirrus Bridge](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-one)

[Multilateral federation Solution 2: Microsoft Entra ID with Shibboleth as a Security Assertion Markup Language \(SAML\) proxy](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-two)

[Multilateral federation decision tree](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-decision-tree)
