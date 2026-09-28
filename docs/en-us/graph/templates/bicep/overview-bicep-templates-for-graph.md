<!-- Source: https://learn.microsoft.com/en-us/graph/templates/bicep/overview-bicep-templates-for-graph -->
<!-- Sitemap-Last-Modified: 2025-07-29 -->

# Bicep templates for Microsoft Graph resources

Bicep templates let you define and deploy Microsoft Graph resources, like groups and applications, using [infrastructure as code](https://learn.microsoft.com/en-us/devops/deliver/what-is-infrastructure-as-code). To get started, you need:

- **Bicep files or templates**: Templates are written in the [Bicep](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview) language, a domain-specific language that uses declarative syntax to deploy resources for your infrastructure as code solutions.
- **Bicep tools**: Tools that let you author, deploy, and manage supported Microsoft Graph resources through the Bicep templates.

**Scenario**: Suppose you want to [call custom APIs from Azure Logic Apps](https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.logic/logic-app-custom-api) and secure your web app with Microsoft Entra ID. Instead of manually creating the two application identities for the logic app and web app, define Microsoft Graph application and service principal resources in a Bicep file. In the same file, also define the Azure logic app and Azure web app resources. This approach lets you deploy both Azure and Microsoft Graph resources together, so you maintain consistency throughout your development lifecycle.

This article explains how Bicep templates and the Microsoft Graph Bicep extension let you automate and deploy Microsoft Graph resources consistently throughout your development lifecycle.

## Microsoft Graph Bicep extension

Built on the [Bicep extensibility feature](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/bicep-extension), the Microsoft Graph Bicep extension lets you author, deploy, and manage a limited set of Microsoft Graph resources \(currently Microsoft Entra ID resources\) in Bicep template files with Azure resources. The following image shows this interaction.

![Screenshot of the Microsoft Graph Bicep extension in an IaC ecosystem.](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/overview/graph-bicep-extension.jpg)

This foundation lets you:

- Use familiar tools to deploy Azure resources with the Microsoft Graph resources you need, like applications and service principals, using infrastructure as code \(IaC\) and DevOps practices.
- Use Bicep templates and IaC practices to deploy and manage your tenant's Microsoft Graph resources.

### Benefits of the Microsoft Graph Bicep extension

- **Authoring experience**: You get the same first-class authoring experience in the [Bicep Extension for VS Code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep) and [Bicep extension for Visual Studio](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.visualstudiobicep) when you use it to create your Bicep files. The editor gives you rich type safety, IntelliSense, and syntax validation.

![Screenshot of Bicep file authoring example.](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/overview/graph-bicep-authoring.gif)

- **Support for both beta and v1.0 API versions**: The Microsoft Graph Bicep extension lets you reference both beta and v1.0 versions of supported Microsoft Graph resource types in the same Bicep file.
- **Repeatable results**: Deploy your infrastructure throughout the development lifecycle and know your resources deploy in a consistent way. Bicep files are idempotent, so you deploy the same file many times and get the same resource types in the same state. Create one file that represents the desired state instead of creating separate files for each update.
- **Orchestration**: You don't need to worry about the order of operations. Resource Manager orchestrates the deployment of interdependent resources so they're created in the right order. When possible, Resource Manager deploys resources in parallel so your deployments finish faster than serial deployments. Deploy the file with one command instead of running multiple commands.

## License requirements

You need the right licenses to deploy Microsoft Graph resources by using Bicep. If you also deploy Azure resources, you need a valid Azure subscription.

## National cloud support

In addition to the public cloud, Bicep extensibility and the Microsoft Graph Bicep extension are supported in these clouds.

| Cloud environment | Bicep extensibility | Microsoft Graph Bicep extension |
| --- | :---: | :---: |
| [Microsoft Cloud for US Government](https://learn.microsoft.com/en-us/azure/azure-government/documentation-government-welcome) | ![Yes](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/overview/green-check.svg) | ![Yes](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/overview/green-check.svg) |
| [Microsoft Azure](https://learn.microsoft.com/en-us/azure/china/overview-operations) and [Microsoft 365](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-operated-by-21vianet) operated by 21Vianet | ![Yes](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/overview/green-check.svg) | ![Yes](https://learn.microsoft.com/en-us/graph/templates/bicep/conceptual/media/overview/green-check.svg) |

## Get started

| Topic | Resources |
| --- | --- |
| Try out your first quickstart | Start by [installing Bicep tools](https://learn.microsoft.com/en-us/graph/templates/bicep/quickstart-install-bicep-tools), then author and deploy your first Bicep file with Microsoft Graph resources in minutes. |
| Learn more from the community | [John Savill's technical training on YouTube](https://www.youtube.com/watch?v=RyCjSp26xXg)  <br>*This resource is from the community, and Microsoft doesn't officially maintain it.* |
| Learn more about Bicep | - [Bicep overview](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview)  <br>- [Training modules for Bicep](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/learn-bicep) |
| Learn more about Microsoft Graph | - [Microsoft Graph overview](https://learn.microsoft.com/en-us/graph/overview)  <br>- [Authentication and authorization principles](https://learn.microsoft.com/en-us/graph/auth)  <br>- [Microsoft Graph tutorials](https://learn.microsoft.com/en-us/graph/tutorials) |
| Explore Microsoft Graph Bicep types | [Microsoft Graph Bicep resource reference](https://learn.microsoft.com/en-us/graph/templates/reference/overview) |
