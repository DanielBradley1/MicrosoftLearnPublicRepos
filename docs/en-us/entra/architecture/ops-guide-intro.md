<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/ops-guide-intro -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Microsoft Entra operations reference guide

This operations reference guide describes the checks and actions you should take to secure and maintain the following areas:

- **[Identity and access management](https://learn.microsoft.com/en-us/entra/architecture/ops-guide-iam)** - ability to manage the lifecycle of identities and their entitlements.
- **[Authentication management](https://learn.microsoft.com/en-us/entra/architecture/ops-guide-auth)** - ability to manage credentials, define authentication experience, delegate assignment, measure usage, and define access policies based on enterprise security posture.
- **[Governance](https://learn.microsoft.com/en-us/entra/architecture/ops-guide-govern)** - ability to assess and attest the access granted nonprivileged and privileged identities, audit, and control changes to the environment.
- **[Operations](https://learn.microsoft.com/en-us/entra/architecture/ops-guide-ops)** - optimize the operations Microsoft Entra ID.

Some recommendations here might not be applicable to all customers' environment, for example, AD FS best practices might not apply if your organization uses password hash sync.

Note

These recommendations are current as of the date of publishing but can change over time. Organizations should continuously evaluate their identity practices as Microsoft products and services evolve over time. Recommendations can change when organizations subscribe to a different Microsoft Entra ID P1 or P2 license.

## Stakeholders

Each section in this reference guide recommends assigning stakeholders to plan and implement key tasks successfully. The following table outlines the list of all the stakeholders in this guide:

| Stakeholder | Description |
| :--- | :--- |
| IAM Operations Team | This team handles managing the day to day operations of the Identity and Access Management system |
| Productivity Team | This team owns and manages the productivity applications such as email, file sharing and collaboration, instant messaging, and conferencing. |
| Application Owner | This team owns the specific application from a business and usually a technical perspective in an organization. |
| InfoSec Architecture Team | This team plans and designs the Information Security practices of an organization. |
| InfoSec Operations Team | This team runs and monitors the implemented Information Security practices of the InfoSec Architecture team. |

## Next steps

Get started with the [Identity and access management checks and actions](https://learn.microsoft.com/en-us/entra/architecture/ops-guide-iam).
