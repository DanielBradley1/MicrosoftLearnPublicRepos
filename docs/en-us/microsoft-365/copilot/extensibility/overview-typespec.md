<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-typespec -->
<!-- Sitemap-Last-Modified: 2025-09-22 -->

# TypeSpec for Microsoft 365 Copilot overview

TypeSpec for Microsoft 365 Copilot is a domain-specific language \(DSL\) that you can use to create declarative agents and API plugins with a clean, expressive syntax. Built on the foundation of [TypeSpec](https://typespec.io/), this specialized language provides Microsoft 365-specific decorators and capabilities that streamline the development process for extending Microsoft 365 Copilot. TypeSpec serves as an alternative to manually authoring JSON manifest files, offering a more developer-friendly approach with enhanced productivity and maintainability.

TypeSpec for Microsoft 365 Copilot provides a high-level abstraction layer over complex JSON schemas and OpenAPI files. The language automatically generates the required manifest files and configurations, reducing development time and minimizing errors. With IntelliSense support, type safety, and comprehensive validation, you can focus on your agent's behavior rather than on configuration details.

Tip

[Work IQ Dev Tools](https://aka.ms/wiqd/docs) \(preview\) and [Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context) provide related pro-code workflows. To choose based on your capability, package route, and target experience, see [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools).

## Type safety and developer experience

TypeSpec for Microsoft 365 Copilot provides a strongly typed development experience that catches errors at compile time rather than runtime. The language includes comprehensive type checking for all Microsoft 365 Copilot-specific constructs, ensuring that your declarative agents and API plugins are correctly configured before you provision them. This type safety extends to all aspects of your agent definition, from basic metadata to complex capability configurations and API operation definitions.

IntelliSense support in Visual Studio Code and Visual Studio provides real-time feedback, auto-completion, and inline documentation. The language integrates with [Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context), offering a complete development workflow from creation through provisioning and publishing. Error messages are clear and actionable, helping you quickly identify and resolve issues during development.

## Simplified agent and plugin authoring

TypeSpec simplifies the process of creating declarative agents and API plugins by replacing verbose JSON configurations with intuitive, decorator-based syntax. Instead of manually crafting complex manifest files, you can use semantic decorators like `@agent`, `@instructions`, and `@capabilities` to define your agents. This approach reduces the likelihood of configuration errors and makes the codebase more maintainable and readable.

When working with complex API surfaces, TypeSpec helps where traditional OpenAPI files become unwieldy and difficult to manage. Large OpenAPI specifications with hundreds of endpoints, complex nested schemas, and intricate authentication patterns can be challenging to author, maintain, and understand. TypeSpec addresses these pain points by providing higher-level abstractions that automatically generate the underlying OpenAPI specifications. You can focus on defining business logic and API behavior using TypeSpec's expressive syntax, while the compiler handles the details of OpenAPI compliance, schema validation, and cross-reference management.

The language provides built-in decorators for all Microsoft 365 Copilot capabilities, including web search, OneDrive and SharePoint integration, Teams messages, code interpreter, and more. API plugins benefit from automatic OpenAPI specification generation, where TypeSpec operations are converted into REST API definitions. This automation eliminates the need to maintain separate API documentation and ensures consistency between your TypeSpec definitions and the resulting API contracts.

## Automatic manifest generation and validation

TypeSpec for Microsoft 365 Copilot automatically generates valid manifest files from your TypeSpec definitions. The language compiler analyzes your TypeSpec code and produces the appropriate JSON manifests for declarative agents and API plugins, ensuring they conform to the latest schema requirements. This generation process includes comprehensive validation, catching common configuration errors before they reach production.

The automatic generation extends beyond basic manifest creation to include complex configurations such as Adaptive Cards, authentication settings, and capability-specific metadata. TypeSpec validates all references, ensures proper data binding for Adaptive Cards, and verifies that all required properties are present. This validation occurs during the build process, so you get immediate feedback and don't provision invalid configurations.

## Examples

Here are practical examples demonstrating TypeSpec for Microsoft 365 Copilot syntax:

### Basic declarative agent

```typescript
import "@typespec/http";
import "@typespec/openapi3";
import "@microsoft/typespec-m365-copilot";

using TypeSpec.Http;
using TypeSpec.M365.Copilot.Agents;

@agent(
  "Customer Support Assistant",
  "An AI agent that helps with customer support inquiries and ticket management"
)
@instructions("""
  You are a customer support specialist. Help users with their inquiries,
  provide troubleshooting steps, and escalate complex issues when necessary.
  Always maintain a helpful and professional tone.
""")
@conversationStarter(#{
  title: "Check Ticket Status",
  text: "What's the status of my support ticket?"
})
namespace CustomerSupportAgent {
  // Agent capabilities defined here
}
```

### Agent with capabilities

```typescript
import "@typespec/http";
import "@microsoft/typespec-m365-copilot";

using TypeSpec.Http;
using TypeSpec.M365.Copilot.Agents;

@agent(
  "Multi-Capability Assistant",
  "An AI agent that can search the web, access SharePoint content, and execute Python code"
)
@instructions("""
  You are a versatile assistant that can help users with research, data analysis, and document management.
  Use web search for current information, access SharePoint for company documents, and execute Python code for calculations and data analysis.
  Always provide clear explanations of your findings and methodology.
""")
namespace MyAgent {
  op webSearch is AgentCapabilities.WebSearch<Sites = [
    {
      url: "https://learn.microsoft.com"
    }
  ]>;

  op oneDriveSearch is AgentCapabilities.OneDriveAndSharePoint<
   ItemsByUrl = [
      {
        url: "https://contoso.sharepoint.com/sites/projects"
      }
    ]
  >;

  op codeInterpreter is AgentCapabilities.CodeInterpreter;
}
```

### API plugin with operations

```typescript
import "@typespec/http";
import "@microsoft/typespec-m365-copilot";

using TypeSpec.Http;
using TypeSpec.M365.Copilot.Agents;
using TypeSpec.M365.Copilot.Actions;

@agent(
  "Project Management Assistant",
  "An AI agent that helps manage projects and tasks through API operations"
)
@instructions("""
  You are a project management assistant that helps users create, track, and manage projects.
  Use the available API operations to list projects, get project details, and create new projects.
  Always provide clear status updates and help users organize their work effectively.
""")
@service
@server("https://api.contoso.com")
@actions(#{
  nameForHuman: "Project Management API",
  descriptionForHuman: "Manage projects and tasks",
  descriptionForModel: "API for creating, updating, and tracking project tasks"
})
namespace ProjectAPI {
  model Project {
    id: string;
    name: string;
    description?: string;
    status: "active" | "completed" | "on-hold";
    createdDate: utcDateTime;
  }

  model CreateProjectRequest {
    name: string;
    description?: string;
    status?: "active" | "on-hold";
  }

  @route("/projects")
  @get op listProjects(): Project[];

  @route("/projects/{id}")
  @get op getProject(@path id: string): Project;

  @route("/projects")
  @post op createProject(@body project: CreateProjectRequest): Project;
}
```

## Get started

To start building with TypeSpec for Microsoft 365 Copilot, see the following resources:

- [Decorators for TypeSpec for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/typespec-decorators) - Reference for the Microsoft 365 Copilot decorators, including `@agent`, `@instructions`, `@capabilities`, and more.
- [Declarative agent capabilities in TypeSpec for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/typespec-capabilities) - Guide to agent capabilities like web search, OneDrive integration, Teams messages, and code interpreter.
- [Authentication support in TypeSpec for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/typespec-authentication) - Authentication patterns and security configurations for TypeSpec-based agents and plugins.
- [Create declarative agents by using Microsoft 365 Agents Toolkit and TypeSpec](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-typespec) - Step-by-step tutorial for creating a declarative agent by using TypeSpec and Agents Toolkit.
- [Build API plugins with TypeSpec for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-api-plugins-typespec) - Guide to creating API plugins with REST operations, Adaptive Cards, and authentication.
- [Start with a sample](https://github.com/pnp/copilot-pro-dev-samples/tree/main/samples) - Community-provided samples.

## Related content

- [Microsoft 365 Agents Toolkit overview](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/overview-agents-toolkit?context=/microsoft-365/copilot/extensibility/context) - Overview of the generally available Microsoft 365 Agents Toolkit.
- [TypeSpec language documentation](https://typespec.io/) - Official TypeSpec language specification and guides
