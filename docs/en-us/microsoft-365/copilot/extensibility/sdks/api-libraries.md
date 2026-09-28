<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/sdks/api-libraries -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# Microsoft 365 Copilot APIs client libraries

The Microsoft 365 Copilot APIs client libraries are designed to facilitate the development of high-quality, efficient, and resilient AI solutions that access the Copilot APIs. These libraries include service and core libraries.

The service libraries offer models and request builders that provide a rich, typed experience for working with Microsoft 365 Copilot APIs.

The core libraries offer advanced features to facilitate interactions with the Copilot APIs. These features include embedded support for retry handling, secure redirects, transparent authentication, and payload compression. These capabilities help you enhance the quality of your AI solution's communications with the Copilot APIs without adding complexity. Additionally, the core libraries simplify routine tasks such as paging through collections and creating batch requests.

## Supported languages

The Copilot APIs client libraries are currently available for the following languages:

- [C#](https://github.com/microsoft/Agents-M365Copilot/tree/main/dotnet)
- [TypeScript](https://github.com/microsoft/Agents-M365Copilot/tree/main/typescript)
- [Python](https://github.com/microsoft/Agents-M365Copilot/tree/main/python)

## Client libraries in preview status

The Copilot APIs client libraries can be in preview status when initially released or after a significant update. Avoid using the preview release of these libraries in production solutions, regardless of whether your solution uses version 1.0 or the beta version of the Copilot APIs.

## Client libraries support

The Copilot API libraries are open-source projects on GitHub. If you encounter a bug, file an issue with the details on the [Issues](https://github.com/microsoft/Agents-M365Copilot/issues) tab. Contributors review and release fixes as needed.

## Install the libraries

The Copilot API client libraries are included as a module in the Microsoft 365 Agents SDK. These libraries can be included in your projects via GitHub and popular platform package managers.

### Install the Copilot APIs .NET client libraries

The Copilot APIs .NET client libraries are available in the following NuGet packages:

- [Microsoft.Agents.M365Copilot](https://github.com/microsoft/Agents-M365Copilot/tree/main/dotnet/src/Microsoft.Agents.M365Copilot) - Contains the models and request builders for accessing the v1.0 endpoint. Microsoft.Agents.M365Copilot has a dependency on Microsoft.Agents.M365Copilot.Core. The same dependency structure applies to both the TypeScript and Python libraries as well.
- [Microsoft.Agents.M365Copilot.Beta](https://github.com/microsoft/Agents-M365Copilot/tree/main/dotnet/src/Microsoft.Agents.M365Copilot.Beta) - Contains the models and request builders for accessing the beta endpoint. Microsoft.Agents.M365Copilot.Beta has a dependency on Microsoft.Agents.M365Copilot.Core. The same dependency structure applies to both the TypeScript and Python libraries as well.
- [Microsoft.Agents.M365Copilot.Core](https://github.com/microsoft/Agents-M365Copilot/tree/main/dotnet/src/Microsoft.Agents.M365Copilot.Core) - The core library for making calls to the Copilot APIs.

To install the Microsoft.Agents.M365Copilot packages into your project, use the [dotnet CLI](https://learn.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli), the [Package Manager UI in Visual Studio](https://learn.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio), or the [Package Manager Console in Visual Studio](https://learn.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio).

### dotnet CLI

For the v1.0 endpoint:

```dotnetcli
dotnet add package Microsoft.Agent.M365Copilot
```

For the beta endpoint:

```dotnetcli
dotnet add package Microsoft.Agent.M365Copilot.Beta
```

### Package Manager Console

For the v1.0 endpoint:

```powershell
Install-Package Microsoft.Agent.M365Copilot
```

For the beta endpoint:

```powershell
Install-Package Microsoft.Agent.M365Copilot.Beta
```

### Install the Copilot APIs Python client libraries

The Copilot APIs Python client libraries are available in the Python Package Index.

For the v1.0 endpoint:

```py
pip install microsoft-agents-m365copilot
```

For the beta endpoint:

```py
pip install microsoft-agents-m365copilot-beta
```

### Install the Copilot APIs TypeScript client libraries

The Copilot APIs TypeScript client libraries are available in npm.

For the v1.0 endpoint:

```Shell
npm install @microsoft/agents-m365copilot –save
```

For the beta endpoint:

```Shell
npm install @microsoft/agents-m365copilot-beta –save
```

## Create a Copilot APIs client and make an API call

The following code example shows how to create an instance of a Microsoft 365 Copilot APIs client with an authentication provider in the supported languages. The authentication provider handles acquiring access tokens for the application. Many different authentication providers are available for each language and platform. The different authentication providers support different client scenarios. For details about which provider and options are appropriate for your scenario, see [Choose an Authentication Provider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers).

The example also shows how to make a call to the Retrieval API. To call this API, you first need to create a request object, and then run the POST method on the request.

The client ID is the app registration ID that is generated when you [register your app in the Azure portal](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).

- [C#](#tabpanel_1_csharp)
- [Python](#tabpanel_1_python)
- [TypeScript](#tabpanel_1_typescript)

```csharp
using Azure.Identity;
using Microsoft.Agents.M365Copilot;
using Microsoft.Agents.M365Copilot.Models;
using Microsoft.Agents.M365Copilot.Copilot.Retrieval;

var scopes = new[] {"Files.Read.All", "Sites.Read.All"};

// Multi-tenant apps can use "common",
// single-tenant apps must use the tenant ID from the Azure portal
var tenantId = "YOUR_TENANT_ID";

// Value from app registration
var clientId = "YOUR_CLIENT_ID";

// using Azure.Identity;
var deviceCodeCredentialOptions = new DeviceCodeCredentialOptions
{
   ClientId = clientId,
   TenantId = tenantId,
   // Callback function that receives the user prompt
   // Prompt contains the generated device code that user must
   // enter during the auth process in the browser
   DeviceCodeCallback = (deviceCodeInfo, cancellationToken) =>
   {
       Console.WriteLine(deviceCodeInfo.Message);
       return Task.CompletedTask;
   },
};

// https://learn.microsoft.com/dotnet/api/azure.identity.devicecodecredential
var deviceCodeCredential = new DeviceCodeCredential(deviceCodeCredentialOptions);


//Create the client
AgentsM365CopilotServiceClient client = new AgentsM365CopilotServiceClient (deviceCodeCredential, scopes, baseURL);

try
{
  var requestBody = new RetrievalPostRequestBody
  {
      DataSource = RetrievalDataSource.SharePoint,
      QueryString = "What is the latest in my organization?",
      MaximumNumberOfResults = 10
  };

  var result = await client.Copilot.Retrieval.PostAsync(requestBody);
  Console.WriteLine($"Retrieval post: {result}");

  if (result != null)
  {
    Console.WriteLine("Retrieval response received successfully");
    Console.WriteLine("\nResults:");
    Console.WriteLine(result.RetrievalHits.Count.ToString());
    if (result.RetrievalHits != null)
    {
       foreach (var hit in result.RetrievalHits)
       {
         Console.WriteLine("\n---");
         Console.WriteLine($"Web URL: {hit.WebUrl}");
         Console.WriteLine($"Resource Type: {hit.ResourceType}");
         if (hit.Extracts != null && hit.Extracts.Any())
         {
            Console.WriteLine("\nExtracts:");
            foreach (var extract in hit.Extracts)
            {
              Console.WriteLine($"  {extract.Text}");
            }
          }
          if (hit.SensitivityLabel != null)
          {
            Console.WriteLine("\nSensitivity Label:");
            Console.WriteLine($"  Display Name: {hit.SensitivityLabel.DisplayName}");
            Console.WriteLine($"  Tooltip: {hit.SensitivityLabel.Tooltip}");
            Console.WriteLine($"  Priority: {hit.SensitivityLabel.Priority}");
            Console.WriteLine($"  Color: {hit.SensitivityLabel.Color}");
            if (hit.SensitivityLabel.IsEncrypted.HasValue)
            {
              Console.WriteLine($"  Is Encrypted: {hit.SensitivityLabel.IsEncrypted.Value}");
            }
          }
        }
      }
      else
      {
        Console.WriteLine("No retrieval hits found in the response");
      }
  }
}
catch (Exception ex)
{
    Console.WriteLine($"Error making retrieval request: {ex.Message}");
    Console.Error.WriteLine(ex);
}
```

```python
import asyncio
import os
from datetime import datetime

from azure.identity import DeviceCodeCredential
from kiota_abstractions.api_error import APIError
from microsoft_agents_m365copilot.agents_m365_copilot_service_client import AgentsM365CopilotServiceClient
from microsoft_agents_m365copilot.generated.copilot.retrieval.retrieval_post_request_body import RetrievalPostRequestBody
from microsoft_agents_m365copilot.generated.models.retrieval_data_source import RetrievalDataSource

scopes = ['Files.Read.All', 'Sites.Read.All']

# Multi-tenant apps can use "common",
# single-tenant apps must use the tenant ID from the Azure portal
TENANT_ID = 'YOUR_TENANT_ID'

# Values from app registration
CLIENT_ID = 'YOUR_CLIENT_ID'

# Define a proper callback function that accepts all three parameters
def auth_callback(verification_uri: str, user_code: str, expires_on: datetime):
    print(f"\nTo sign in, use a web browser to open the page {verification_uri}")
    print(f"Enter the code {user_code} to authenticate.")
    print(f"The code will expire at {expires_on}")

# Create device code credential with correct callback
credentials = DeviceCodeCredential(
    client_id=CLIENT_ID,
    tenant_id=TENANT_ID,
    prompt_callback=auth_callback
)

client = AgentsM365CopilotServiceClient(credentials=credentials, scopes=scopes)

async def retrieve():
    try:
        # Print the URL being used
        print(f"Using API base URL: {client.request_adapter.base_url}\n")
        
        # Create the retrieval request body
        retrieval_body = RetrievalPostRequestBody()
        retrieval_body.data_source = RetrievalDataSource.SharePoint
        retrieval_body.query_string = "What is the latest in my organization?"
        
        # Try more parameters that might be required
        # retrieval_body.maximum_number_of_results = 10
        
        # Make the API call
        print("Making retrieval API request...")
        retrieval = await client.copilot.retrieval.post(retrieval_body)
        
        # Process the results
        if retrieval and hasattr(retrieval, "retrieval_hits"):
            print(f"Received {len(retrieval.retrieval_hits)} hits")
            for r in retrieval.retrieval_hits:
                print(f"Web URL: {r.web_url}\n")
                for extract in r.extracts:
                    print(f"Text:\n{extract.text}\n")
        else:
            print(f"Retrieval response structure: {dir(retrieval)}")
    except APIError as e:
        print(f"Error: {e.error.code}: {e.error.message}")
        if hasattr(e, 'error') and hasattr(e.error, 'inner_error'):
            print(f"Inner error details: {e.error.inner_error}")
        raise e


# Run the async function
asyncio.run(retrieve())
```

```typescript
import { createBaseAgentsM365CopilotServiceClient, RetrievalDataSourceObject } from '@microsoft/agents-m365copilot';
import { DeviceCodeCredential } from '@azure/identity';
import { FetchRequestAdapter } from '@microsoft/kiota-http-fetchlibrary';
import { AzureIdentityAuthenticationProvider } from '@microsoft/kiota-authentication-azure';

async function main() {
    // Initialize authentication with Device Code flow
    const credential = new DeviceCodeCredential({
        tenantId: "YOUR_TENANT_ID",
        clientId: "YOUR_CLIENT_ID",
        userPromptCallback: (info) => {
            console.log(`\nTo sign in, use a web browser to open the page ${info.verificationUri}`);
            console.log(`Enter the code ${info.userCode} to authenticate.`);
            console.log(`The code will expire at ${info.expiresOn}`);          
        }
    });
    // Create request adapter with auth
    const authProvider = new AzureIdentityAuthenticationProvider(credential, ["Files.Read.All", "Sites.Read.All"]);
    const adapter = new FetchRequestAdapter(authProvider);

    // Create client instance
    const client = createBaseAgentsM365CopilotServiceClient(adapter);

    try {
        console.log(`Using API base URL: ${adapter.baseUrl}\n`);
        // Create the retrieval request body
        const retrievalBody = {
            dataSource: RetrievalDataSourceObject.SharePoint,
            queryString: "What is the latest in my organization?"
        };

        // Make the API call
        console.log("Making retrieval API request...");
        const retrieval = await client.copilot.retrieval.post(retrievalBody);

        // Process the results
        if (retrieval?.retrievalHits) {
            console.log(`\nReceived ${retrieval.retrievalHits.length} hits`);
            for (const hit of retrieval.retrievalHits) {
                console.log(`\nWeb URL: ${hit.webUrl}`);
                for (const extract of hit.extracts || []) {
                    console.log(`Text:\n${extract.text}\n`);
                }
            }
        }
    } catch (error) {
        console.error('Error:', error);
        throw error;
    }
}  

main().catch((error) => {
    console.error('An error occurred:', error);
});
```

## Related content

- [Overview of the Microsoft 365 Copilot Retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/overview)
- [Use the Retrieval API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/copilotroot-retrieval)
