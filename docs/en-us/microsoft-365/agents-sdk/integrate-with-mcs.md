<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/integrate-with-mcs -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Integrate with Copilot Studio

As a developer, you have the flexibility to use the technology stack of your choice for AI Services when working with the Microsoft 365 Agents SDK. This flexibility includes the ability to use agents built in Microsoft Copilot Studio. Copilot Studio lets business users and makers create agents easily in an SaaS-based environment. Makers can then share the agents they build with developers to integrate in their own custom web or native applications. You can carry out integration in either of two ways:

- Reference one or more agents built in Copilot Studio from your agent built with the Agents SDK. You can also integrate with other agents, such as those created with Azure.
- Use the Microsoft 365 Agents SDK to integrate Copilot Studio directly within your web or native apps.

## Use the Copilot Studio client library

There is a full guide and samples available to help you get started with the Copilot Studio client library in the Agents SDK. The library and samples are available in .NET, JavaScript, and Python.

Clone the appropriate sample from the Agents SDK repo and access the relevant readme for details and instructions.

- [.NET sample](https://github.com/microsoft/Agents/tree/main/samples/dotnet/copilotstudio-client)
- [JavaScript sample](https://github.com/microsoft/Agents/tree/main/samples/nodejs/copilotstudio-client)
- [Python sample](https://github.com/microsoft/Agents/tree/main/samples/python/copilotstudio-client)

Each sample is configured as a console app so that you can get started quickly. In this console app, you interact with a live Copilot Studio agent.

Note

Currently, you can only use the Copilot Studio client library with Copilot Studio agents created by using the standard harness. Agents using the GitHub Copilot harness aren't yet officially supported.

## Related content

- [Integrate your Copilot Studio agent with the Microsoft 365 Agents SDK](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-integrate-web-or-native-app-m365-agents-sdk)
