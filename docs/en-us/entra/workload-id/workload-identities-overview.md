<!-- Source: https://learn.microsoft.com/en-us/entra/workload-id/workload-identities-overview -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# What are workload identities?

A workload identity is an identity you assign to a software workload \(such as an application, service, script, or container\) to authenticate and access other services and resources. The terminology is inconsistent across the industry, but generally a workload identity is something you need for your software entity to authenticate with some system. For example, in order for GitHub Actions to access Azure subscriptions the action needs a workload identity which has access to those subscriptions. A workload identity could also be an AWS service role attached to an EC2 instance with read-only access to an Amazon S3 bucket.

In Microsoft Entra, workload identities are applications, service principals, and managed identities.

An [application](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json) is an abstract entity, or template, defined by its application object. The application object is the *global* representation of your application for use across all tenants. The application object describes how tokens are issued, the resources the application needs to access, and the actions that the application can take.

A [service principal](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json) is the *local* representation, or application instance, of a global application object in a specific tenant. An application object is used as a template to create a service principal object in every tenant where the application is used. The service principal object defines what the app can actually do in a specific tenant, who can access the app, and what resources the app can access.

A [managed identity](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json) is a special type of service principal that eliminates the need for developers to manage credentials.

Here are some ways that workload identities in Microsoft Entra ID are used:

- An app that enables a web app to access Microsoft Graph based on admin or user consent. This access could be either on behalf of the user or on behalf of the application.
- A managed identity used by a developer to provision their service with access to an Azure resource such as Azure Key Vault or Azure Storage.
- A service principal used by a developer to enable a CI/CD pipeline to deploy a web app from GitHub to Azure App Service.

## Workload identities, other machine identities, and human identities

At a high level, there are two types of identities: human and machine/non-human identities. Workload identities and device identities together make up a group called machine \(or non-human\) identities. Workload identities represent software workloads while device identities represent devices such as desktop computers, mobile, IoT sensors, and IoT managed devices. Machine identities are distinct from human identities, which represent people such as employees \(internal workers and front line workers\) and external users \(customers, consultants, vendors, and partners\).

![Diagram that shows different types of machine and human identities.](https://learn.microsoft.com/en-us/entra/workload-id/media/workload-identities-overview/identity-types.svg)

## Need for securing workload identities

More and more, solutions are reliant on non-human entities to complete vital tasks and the number of non-human identities is increasing dramatically. Recent cyber attacks show that adversaries are increasingly targeting non-human identities over human identities.

Human users typically have a single identity used to access a broad range of resources. Unlike a human user, a software workload may deal with multiple credentials to access different resources and those credentials need to be stored securely. It’s also hard to track when a workload identity is created or when it should be revoked. Enterprises risk their applications or services being exploited or breached because of difficulties in securing workload identities.

![Diagram that shows pain points in securing workload identities.](https://learn.microsoft.com/en-us/entra/workload-id/media/workload-identities-overview/pain-points.png)

Most identity and access management solutions on the market today are focused only on securing human identities and not workload identities. Microsoft Entra Workload ID helps resolve these issues when securing workload identities.

## Key scenarios

Here are some ways you can use workload identities.

Secure access with adaptive policies:

- Apply Conditional Access policies to service principals owned by your organization using [Conditional Access for workload identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/workload-identity?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json).
- Enable real-time enforcement of Conditional Access location and risk policies using [Continuous access evaluation for workload identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation-workload?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json).
- Manage [custom security attributes for an app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/custom-security-attributes-apps?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json)

Intelligently detect compromised identities:

- Detect risks \(like leaked credentials\), contain threats, and reduce risk to workload identities using [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/concept-workload-identity-risk?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json).

Simplify lifecycle management:

- Access Microsoft Entra protected resources without needing to manage secrets for workloads that run on Azure using [managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview?toc=/azure/active-directory/workload-identities?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json).
- Access Microsoft Entra protected resources without needing to manage secrets using [workload identity federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation) for supported scenarios such as GitHub Actions, workloads running on Kubernetes, or workloads running in compute platforms outside of Azure.
- Review service principals and applications that are assigned to privileged directory roles in Microsoft Entra ID using [access reviews for service principals](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-create-roles-and-resource-roles-review?toc=/azure/active-directory/workload-identities/toc.json&bc=/azure/active-directory/workload-identities/breadcrumb/toc.json).

## Agent identities for AI workloads

AI agents — autonomous software systems that reason, make decisions, and take actions on behalf of users or organizations — represent a distinct category of machine identity with unique security requirements. Unlike traditional workloads that execute predetermined logic, AI agents make dynamic decisions and adapt behavior, which requires purpose-built identity constructs with stronger governance controls.

[Microsoft Entra Agent ID](https://learn.microsoft.com/en-us/entra/agent-id/what-is-microsoft-entra-agent-id) provides these constructs through agent identities. Agent identities offer enforced human sponsorship, lifecycle governance from provisioning through deactivation, and at-scale management that apply centralized security policies across all agent instances of a given type. For more information, see [Microsoft Entra security for AI overview](https://learn.microsoft.com/en-us/entra/agent-id/security-for-ai-overview).

## Next steps

- Get answers to [frequently asked questions about workload identities](https://learn.microsoft.com/en-us/entra/workload-id/workload-identities-faqs).
