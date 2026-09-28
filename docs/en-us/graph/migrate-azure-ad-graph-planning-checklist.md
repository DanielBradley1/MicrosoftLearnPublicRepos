<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist -->
<!-- Sitemap-Last-Modified: 2025-01-28 -->

# Azure AD Graph app migration planning checklist

Use the following checklist to plan your migration from Azure Active Directory \(Azure AD\) Graph to Microsoft Graph.

## Step 1: Review the differences between the APIs

In many ways, Microsoft Graph resembles Azure AD Graph. Often, you can simply update the endpoint, version, and resource name in your code, and it should function as expected.

However, there are differences where some resources, properties, methods, and core capabilities have changed.

Look for differences in the following areas:

- [Request call syntax](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-request-differences) between the two services.
- [Feature differences](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-feature-differences), such as directory extensions, batching, differential queries, and so on.
- [Entity resource names](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-resource-differences) and their types.
- [Properties](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-property-differences) of request and response objects.
- [Methods](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-method-differences), including parameters and types.
- [Permissions](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-permissions-differences).

## Step 2: Examine API use

[Examine the APIs](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-audit-api-use) used by your app, the permissions they require, and compare to the list of known differences.

For production, ensure that the APIs your app requires are generally available in Microsoft Graph v1.0 and verify if they function the same as in Azure AD Graph or have differences.

For testing, use [Graph Explorer](https://aka.ms/ge) to experiment with API calls and develop new approaches. For best results, sign in with the credentials of a test user in a test tenant to verify the API behavior in a realistic environment.

## Step 3: Review app details

- [App registration](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-app-registration) and consent changes.
- Token acquisition and [authentication libraries](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-authentication-library).
- For .NET applications, use of [client libraries](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-client-libraries).

## Step 4: Deploy, test, and extend your app

Before updating your app for production, thoroughly test it and stage the rollout to your customer audience.

After switching to Microsoft Graph, you unlock many more datasets and features that are defined in [Major services and features in Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview-major-services).

## Next step

[Learn about the request call syntax](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-request-differences)
