<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessscenario-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# Use the business scenarios API in Microsoft Graph \(preview\)

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The business scenarios API allows for the creation and management of business scenarios that configure and manage the integration of data into Microsoft Graph.

## Structure of a business scenario

A business scenario is represented by the [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) entity. A **businessScenario** resource specifies general information about the scenario, the apps that use that scenario, and configurations for entities that apps can manage to support the scenario. Apps can identify the instance of **businessScenario** by the **uniqueName** property using a reverse domain name format.

### Entities available in business scenarios

The business scenarios API is designed to allow Microsoft Graph services to extend it to support service-specific scenarios that are specific to customers.

Currently, [Planner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario-planner-overview?view=graph-rest-beta) has extended the API. The API supports custom scenario data for Planner in the [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) entity.

Note

Do you have a scenario that requires bringing in custom data as entities to another Microsoft 365 service? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Creating a business scenario

Business scenarios can be created by applications using the delegated permission `BusinessScenarioConfig.ReadWrite.OwnedBy`. Creating a business scenario requires specifying a display name and a unique name. The unique name should be in the reverse DNS format to prevent conflict between independent scenarios. The reverse DNS format takes the domain name the scenario creator owns and reverses it. For example, if a developer who owns `apps.contoso.com` creates a scenario, the unique name of the scenario should start with `com.contoso.apps`. Then further segments can be added to differentiate scenarios or groups of scenarios; for example, `com.contoso.apps.customerSupport.ticketManagement`. The unique name of the scenario must be distinct from every other scenario deployed in a tenant.

For more information, see [Create businessScenario](https://learn.microsoft.com/en-us/graph/api/solutionsroot-post-businessscenarios?view=graph-rest-beta).

## Configuring behaviors for entities

Each service supported through business scenarios provides configurations in the scenario. Applications need to have the `BusinessScenarioConfig.Read.OwnedBy` permission to be able to access these configurations, and the `BusinessScenarioConfig.ReadWrite.OwnedBy` permission to be able to change them. Each configuration is specific for the service. For more details, see the following service-specific topics:

- [Planner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario-planner-overview?view=graph-rest-beta) provides the following configurations:

  - [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta)
  - [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta)

## Creating and managing data for a business scenario

Each service supported through business scenarios provides access to data within a scenario. Applications need to be listed as an owner in a scenario to work with the data in the scenario. Applications also need to have the `BusinessScenarioData.Read.OwnedBy` permission to be able to read the data, and the `BusinessScenarioData.ReadWrite.OwnedBy` permission to be able to create new data, or to modify previously created data. For more details, see the following service-specific topics:

- [Planner](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario-planner-overview?view=graph-rest-beta), with the following supported entities:

  - [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta)

## Deleting a business scenario

Applications that own a business scenario can delete the scenario if they have the `BusinessScenarioConfig.ReadWrite.OwnedBy` permission. Deleting the scenario removes all the data associated with the scenario as well.

For more information, see [Delete businessScenario](https://learn.microsoft.com/en-us/graph/api/businessscenario-delete?view=graph-rest-beta).

## Common use cases

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| Create, read, update, and delete business scenarios | [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) | [Methods of businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta#methods) |
| Configure business scenarios for Planner | [plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta) [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) | [Methods of plannerPlanConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannerplanconfiguration?view=graph-rest-beta#methods) [Methods of plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta#methods) |
| Create, read, update, and delete business scenario tasks in Planner | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) | [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta#methods) |

## Next steps

The business scenarios API allows apps to model and integrate real work business processes with a Microsoft 365 service over Microsoft Graph. To learn more:

- Drill down on the methods and properties of the resources most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
