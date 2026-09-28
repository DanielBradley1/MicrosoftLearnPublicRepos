<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Build resilience in customer identity and access management with Azure AD B2C

Important

Effective May 1, 2025, Azure Active Directory B2C \(Azure AD B2C\) is no longer available for new customers to purchase. To learn more, see [Is Azure AD B2C still available to purchase?](https://learn.microsoft.com/en-us/azure/active-directory-b2c/faq?tabs=app-reg-ga#azure-ad-b2c-end-of-sale) in our FAQ.

[Azure AD B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/overview) is a customer identity and access management \(CIAM\) platform that is designed to help you launch your critical customer facing applications. We have built-in features for [resilience](https://azure.microsoft.com/blog/advancing-azure-active-directory-availability/) to help our service scale to your needs and improve resilience in the face of potential outage situations. In addition, when launching a mission critical application, it's important to consider various design and configuration elements in your application. Consider how the application is configured in Azure AD B2C to ensure you see resilient behavior in response to outage or failure scenarios. In this article, we discuss some of the best practices to help you increase resilience.

A resilient service continues to function despite disruptions. To improve resilience:

- Understand all the components
- Eliminate single points of failures
- Limit effects by isolating failing components
- Provide redundancy with fast failover mechanisms and recovery paths

As you develop your application, we recommend you consider how to [increase resilience of authentication and authorization in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview) with the identity components of your solution. This article attempts to address enhancements for resilience for Azure AD B2C applications. We group our recommendations by CIAM functions.

In the subsequent sections, we guide you to build resilience in the following areas:

- [End-user experience](https://learn.microsoft.com/en-us/entra/architecture/resilient-end-user-experience): Enable a fallback plan for your authentication flow and mitigate the potential impact from a disruption of Azure AD B2C authentication service.
- [Interfaces with external processes](https://learn.microsoft.com/en-us/entra/architecture/resilient-external-processes): Build resilience in your applications and interfaces by recovering from errors.
- [Developer best practices](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c-developer-best-practices): Avoid fragility because of common custom policy issues and improve error handling in the areas like interactions with claims verifiers, third-party applications, and REST APIs.
- [Monitoring and analytics](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-monitoring-alerting): Assess the health of your service by monitoring key indicators and detect failures and performance disruptions through alerting.
- [Build resilience in authentication infrastructure](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-infrastructure): Understand, contain, and mitigate the risk of disrupted authentication or authorization for resources.
- [Increase resilience of authentication and authorization in applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview): Use Microsoft identity platform to build apps your users and customers sign in to with Microsoft identities or social accounts.

Watch the following video to [build resilient and scalable flows](https://www.youtube.com/embed/8f_Ozpw9yTs). Learn how to design and configure resilient and scalable services using Azure AD B2C.
