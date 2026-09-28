<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-decision-tree -->
<!-- Sitemap-Last-Modified: 2024-03-04 -->

# Decision tree

Use this decision tree to determine the multilateral federation solution that's best suited for your environment.

[![Diagram that shows a decision matrix with key criteria to help choose between three solutions.](https://learn.microsoft.com/en-us/entra/architecture/media/multilateral-federation-decision-tree/tradeoff-decision-matrix.png)](https://learn.microsoft.com/en-us/entra/architecture/media/multilateral-federation-decision-tree/tradeoff-decision-matrix.png#lightbox)

## Migration resources

The following resources can help with your migration to the solutions covered in this content.

| Migration resource | Description | Relevant for migrating to... |
| --- | --- | --- |
| [Resources for migrating applications to Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/migration-resources) | List of resources to help you migrate application access and authentication to Microsoft Entra ID | Solution 1, Solution 2, and Solution 3 |
| [Microsoft Entra custom claims provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview) | Overview of the Microsoft Entra custom claims provider | Solution 1 |
| [Custom security attributes](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-manage) | Steps for managing access to custom security attributes | Solution 1 |
| [Microsoft Entra single sign-on \(SSO\) integration with Cirrus Bridge](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cirrus-identity-bridge-for-azure-ad-tutorial) | Tutorial to integrate Cirrus Bridge with Microsoft Entra ID | Solution 1 |
| [Cirrus Bridge overview](https://blog.cirrusidentity.com/documentation/azure-bridge-setup-rev-6.0) | Cirrus Identity documentation for configuring Cirrus Bridge with Microsoft Entra ID | Solution 1 |
| [Configuring Shibboleth as a Security Assertion Markup Language \(SAML\) proxy](https://shibboleth.atlassian.net/wiki/spaces/KB/pages/1467056889/Using+SAML+Proxying+in+the+Shibboleth+IdP+to+connect+with+Azure+AD) | Shibboleth article that describes how to use the SAML proxying feature to connect the Shibboleth identity provider \(IdP\) to Microsoft Entra ID | Solution 2 |
| [Microsoft Entra multifactor authentication deployment considerations](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-getstarted) | Guidance for configuring Microsoft Entra multifactor authentication | Solution 1 and Solution 2 |

## Next steps

See these related articles about multilateral federation:

[Multilateral federation introduction](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-introduction)

[Multilateral federation baseline design](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-baseline)

[Multilateral federation Solution 1: Microsoft Entra ID with Cirrus Bridge](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-one)

[Multilateral federation Solution 2: Microsoft Entra ID with Shibboleth as a SAML proxy](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-two)

[Multilateral federation Solution 3: Microsoft Entra ID with AD FS and Shibboleth](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-three)
