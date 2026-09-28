<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-introduction -->
<!-- Sitemap-Last-Modified: 2024-09-20 -->

# Introduction to multilateral federation solutions

Research universities need to collaborate with one another. To accomplish collaboration, they require multilateral federation to enable authentication and access between universities globally.

## Challenges with multilateral federation solutions

Universities face many challenges. For example, a university might use one identity management system and a set of protocols. Other universities might use a different set of technologies, depending on their requirements. In general, universities can:

- Use different identity management systems.
- Use different protocols.
- Use customized solutions.
- Need support for a long history of legacy functionality.
- Need support for solutions that are built in different IT generations.

Many universities are also adopting the Microsoft 365 suite of productivity and collaboration tools. These tools rely on Microsoft Entra ID for identity management, which enables universities to configure:

- Single sign-on across multiple applications.
- Modern security controls, including passwordless authentication, multifactor authentication, and risk-based Conditional Access policies.
- Enhanced reporting and monitoring.

Because Microsoft Entra ID doesn't natively support multilateral federation, this content describes three solutions for federating authentication and access between universities with a typical research university architecture. These scenarios mention non-Microsoft products for illustrative purposes only and to represent the broader class of products. For example, this content uses Shibboleth as an example of a federation provider.

## Next steps

See these related articles about multilateral federation:

[Multilateral federation baseline design](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-baseline)

[Multilateral federation Solution 1: Microsoft Entra ID with Cirrus Bridge](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-one)

[Multilateral federation Solution 2: Microsoft Entra ID with Shibboleth as a Security Assertion Markup Language \(SAML\) proxy](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-two)

[Multilateral federation Solution 3: Microsoft Entra ID with AD FS and Shibboleth](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-solution-three)

[Multilateral federation decision tree](https://learn.microsoft.com/en-us/entra/architecture/multilateral-federation-decision-tree)
