<!-- Source: https://learn.microsoft.com/en-us/entra/standards/configure-for-fedramp-high-impact -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Configure Microsoft Entra ID to meet FedRAMP High Impact level

The [Federal Risk and Authorization Management Program](https://www.fedramp.gov/) \(FedRAMP\) is an assessment and authorization process for cloud service providers \(CSPs\). Specifically, the process is for CSPs that create cloud solution offerings \(CSOs\) for use with federal agencies. Azure and Azure Government have earned a [Provisional Authority to Operate \(P-ATO\) at the High Impact level](https://learn.microsoft.com/en-us/compliance/regulatory/offering-fedramp) from the Joint Authorization Board, the highest bar for FedRAMP accreditation.

Azure provides the capability to fulfill all control requirements to achieve a FedRAMP high rating for your CSO, or as a federal agency. It's your organization’s responsibility to complete additional configurations or processes to be compliant. This responsibility applies to both CSPs seeking a FedRAMP high authorization for their CSO, and federal agencies seeking an Authority to Operate \(ATO\).

## Microsoft and FedRAMP

Microsoft Azure supports more services at [FedRAMP High Impact](https://learn.microsoft.com/en-us/azure/azure-government/compliance/azure-services-in-fedramp-auditscope) levels than any other CSP. And while this level in the Azure public cloud meets the needs of many US government customers, agencies with more stringent requirements might rely on the Azure Government cloud. Azure Government provides additional safeguards, such as the heightened screening of personnel.

Microsoft is required to recertify its cloud services each year to maintain its authorizations. To do so, Microsoft continuously monitors and assesses its security controls, and demonstrates that the security of its services remains in compliance. For more information, see [Microsoft cloud services FedRAMP authorizations](https://marketplace.fedramp.gov/), and [Microsoft FedRAMP Audit Reports](https://aka.ms/MicrosoftFedRAMPAuditDocuments). To receive other FedRAMP reports, send email to [Azure Federal Documentation](mailto:AzFedDoc@microsoft.com).

There are multiple paths towards FedRAMP authorization. You can reuse the existing authorization package of Azure and the guidance here to significantly reduce the time and effort required to obtain an ATO or a P-ATO.

## Scope of guidance

The FedRAMP high baseline is made up of 421 controls and control enhancements from [NIST 800-53 Security Controls Catalog Revision 4](https://csrc.nist.gov/pubs/itlb/2015/01/release-of-nist-special-publication-80053a-revisio/final). Where applicable, we included clarifying information from the [800-53 Revision 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final). This article set covers a subset of these controls that are related to identity, and which you must configure.

We provide prescriptive guidance to help you achieve compliance with controls you're responsible for configuring in Microsoft Entra ID. To fully address some identity control requirements, you might need to use other systems. Other systems might include a security information and event management tool, such as Microsoft Sentinel. If you're using Azure services outside of Microsoft Entra ID, there will be other controls you need to consider, and you can use the capabilities Azure already has in place to meet the controls.

The following is a list of FedRAMP resources:

- [Federal Risk and Authorization Management Program](https://www.fedramp.gov/)
- [Agency Guide for FedRAMP Authorizations](https://www.fedramp.gov/assets/resources/documents/Agency_Authorization_Playbook.pdf)
- [Managing compliance in the cloud at Microsoft](https://www.microsoft.com/trustcenter/common-controls-hub)
- [Microsoft Government Cloud](https://go.microsoft.com/fwlink/p/?linkid=2087246)
- [Azure Compliance Offerings](https://aka.ms/azurecompliance)
- [FedRAMP High Azure Policy built-in initiative definition](https://learn.microsoft.com/en-us/azure/governance/policy/samples/fedramp-high)
- [Microsoft Purview portal](https://learn.microsoft.com/en-us/purview/purview-portal)
- [Microsoft Purview Compliance Manager](https://learn.microsoft.com/en-us/purview/compliance-manager)

## Next steps

[Configure access controls](https://learn.microsoft.com/en-us/entra/standards/fedramp-access-controls)

[Configure identification and authentication controls](https://learn.microsoft.com/en-us/entra/standards/fedramp-identification-and-authentication-controls)

[Configure other controls](https://learn.microsoft.com/en-us/entra/standards/fedramp-other-controls)
