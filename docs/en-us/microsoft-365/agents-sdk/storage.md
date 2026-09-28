<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/storage -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Use storage in your agent

Storage is a critical component of Microsoft 365 Agents SDK. It lets agents persist conversation state, user data, and other information across sessions. The SDK supports various storage options, including:

- In-memory storage
- Azure Cosmos DB
- Azure Blob Storage
- Custom storage providers

## Key storage options

The Agents SDK provides several built-in storage providers, each with its own use cases and benefits. You can choose the one that best fits your agent's needs. You can also implement your own custom storage provider.

1. Memory storage

   - Suitable for testing and development purposes.
   - Data is cleared when the agent restarts, so it's unsuitable for production.
   - Data is only available on the web app instance, so it's unsuitable when running in a cluster.

2. Azure Cosmos DB

   - A globally distributed, multimodel database ideal for production agents.
   - Supports partitioned storage for scalability and performance.

3. Azure Blob Storage

   - Optimized for storing unstructured data like text or binary files.
   - Commonly used for agent state and transcript storage.

4. Custom storage options by implementing `IStorage`

## Using different storage providers

### Memory storage

All samples use `MemoryStorage`. This storage is volatile and suitable for development and testing only. For production scenarios, use a more durable storage option like Azure Cosmos DB or Azure Blob Storage.

- [C#](#tabpanel_1_csharp)
- [JavaScript](#tabpanel_1_javascript)
- [Python](#tabpanel_1_python)

In `Program.cs`, register `MemoryStorage`:

```csharp
builder.Services.AddSingleton<IStorage, MemoryStorage>();
```

```javascript
import { MemoryStorage, AgentApplication, TurnState } from '@microsoft/agents-hosting'

const storage = new MemoryStorage()

const app = new AgentApplication<TurnState>({
  storage
})
```

```python
from microsoft_agents.hosting.core import AgentApplication, TurnState, MemoryStorage

storage = MemoryStorage()

app = AgentApplication[TurnState](
    storage=storage,
    adapter=adapter,
    authorization=authorization,
)
```

### Azure CosmosDb storage

- [C#](#tabpanel_2_csharp)
- [JavaScript](#tabpanel_2_javascript)
- [Python](#tabpanel_2_python)

1. Add a package dependency for `Microsoft.Agents.Storage.CosmosDb`.
2. In `Program.cs`, add \(or replace existing\) `IStorage` registration with:

   ```csharp
   builder.Services.AddSingleton<IStorage>(sp =>
   {
         var options = new CosmosDbPartitionedStorageOptions()
         {
            CosmosDbEndpoint = "your-cosmosdb-endpoint",
            DatabaseId = "your-database-id",
            ContainerId = "your-container-id",

            // Get a TokenCredential from your defined Connections
            TokenCredential = sp.GetService<IConnections>().GetConnection("ServiceConnection").GetTokenCredential()
         };

         return new CosmosDbPartitionedStorage(options);
   });
   ```

3. Learn more in [`CosmosDbPartitionedStorageOptions`](https://github.com/microsoft/Agents-for-net/blob/main/src/libraries/Storage/Microsoft.Agents.Storage.CosmosDb/CosmosDbPartitionedStorageOptions.cs).

1. Add a package dependency for `@microsoft/agents-hosting-storage-cosmos`.
2. Configure and create the storage, then pass it to `AgentApplication`:

   ```javascript
   import { AgentApplication, TurnState } from '@microsoft/agents-hosting'
   import { CosmosDbPartitionedStorage } from '@microsoft/agents-hosting-storage-cosmos'

   const storage = new CosmosDbPartitionedStorage({
     databaseId: process.env.COSMOS_DATABASE_ID,
     containerId: process.env.COSMOS_CONTAINER_ID,
     cosmosClientOptions: {
       endpoint: process.env.COSMOS_ENDPOINT,
       key: process.env.COSMOS_KEY,
     }
   })

   const app = new AgentApplication<TurnState>({
     storage
   })
   ```

3. Learn more in [`CosmosDbPartitionedStorageOptions`](https://github.com/microsoft/Agents-for-js/blob/main/packages/agents-hosting-storage-cosmos/src/cosmosDbPartitionedStorageOptions.ts).

1. Add a package dependency for `microsoft-agents-storage-cosmos`.
2. Configure and create the storage, then pass it to `AgentApplication`:

   ```python
   from microsoft_agents.hosting.core import AgentApplication, TurnState
   from microsoft_agents.storage.cosmos import CosmosDBStorage, CosmosDBStorageConfig

   config = CosmosDBStorageConfig(
       cosmos_db_endpoint="your-cosmosdb-endpoint",
       database_id="your-database-id",
       container_id="your-container-id",
       credential=your_token_credential,
   )

   storage = CosmosDBStorage(config)

   app = AgentApplication[TurnState](
       storage=storage,
       adapter=adapter,
       authorization=authorization,
   )
   ```

3. Learn more in [`CosmosDBStorageConfig`](https://github.com/microsoft/Agents-for-python/blob/main/libraries/microsoft-agents-storage-cosmos/microsoft_agents/storage/cosmos/cosmos_db_storage_config.py).

### Azure blob storage

- [C#](#tabpanel_3_csharp)
- [JavaScript](#tabpanel_3_javascript)
- [Python](#tabpanel_3_python)

1. Add a package dependency for `Microsoft.Agents.Storage.Blobs`.
2. In `Program.cs`, add \(or replace existing\) `IStorage` registration with:

   ```csharp
   builder.Services.AddSingleton<IStorage>(sp =>
   {
      // Get a TokenCredential from your defined Connections
      var tokenCredential = sp.GetService<IConnections>().GetConnection("ServiceConnection").GetTokenCredential();

      return new BlobsStorage(
         new Uri("{{your-blobs-storage-endpoint}}/agent-state"),
         tokenCredential);
   });
   ```

1. Add a package dependency for `@microsoft/agents-hosting-storage-blob`.
2. Configure and create the storage, then pass it to `AgentApplication`:

   ```javascript
   import { AgentApplication, TurnState } from '@microsoft/agents-hosting'
   import { BlobsStorage } from '@microsoft/agents-hosting-storage-blob'

   const storage = new BlobsStorage(
     process.env.BLOB_CONTAINER_ID,
     process.env.BLOB_STORAGE_CONNECTION_STRING
   )

   const app = new AgentApplication<TurnState>({
     storage
   })
   ```

1. Add a package dependency for `microsoft-agents-storage-blob`.
2. Configure and create the storage, then pass it to `AgentApplication`:

   ```python
   from microsoft_agents.hosting.core import AgentApplication, TurnState
   from microsoft_agents.storage.blob import BlobStorage, BlobStorageConfig

   # Using a connection string
   config = BlobStorageConfig(
       container_name="agent-state",
       connection_string="your-connection-string",
   )

   # Or using a TokenCredential
   config = BlobStorageConfig(
       container_name="agent-state",
       url="https://your-storage-account.blob.core.windows.net",
       credential=your_token_credential,
   )

   storage = BlobStorage(config)

   app = AgentApplication[TurnState](
       storage=storage,
       adapter=adapter,
       authorization=authorization,
   )
   ```

3. Learn more in [`BlobStorageConfig`](https://github.com/microsoft/Agents-for-python/blob/main/libraries/microsoft-agents-storage-blob/microsoft_agents/storage/blob/blob_storage_config.py).
