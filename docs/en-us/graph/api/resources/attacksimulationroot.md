<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-28 -->

# attackSimulationRoot resource type

Namespace: microsoft.graph

Represents an abstract type that provides the ability to launch a realistic phishing attack that organizations can learn from.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| **Attack simulation operation** |  |  |
| [Get attackSimulationOperation](https://learn.microsoft.com/en-us/graph/api/attacksimulationoperation-get?view=graph-rest-1.0) | [attackSimulationOperation](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationoperation?view=graph-rest-1.0) | Get an attack simulation campaign operation for a tracking ID. |
| **End user notification** |  |  |
| [List endUserNotification](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-endusernotifications?view=graph-rest-1.0) | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) collection | Get a list of [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) objects and their properties. |
| [Get endUserNotification](https://learn.microsoft.com/en-us/graph/api/endusernotification-get?view=graph-rest-1.0) | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) | Read the properties and relationships of an [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) object. |
| **Landing page** |  |  |
| [List landingPages](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-landingpage?view=graph-rest-1.0) | [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) collection | Get a list of the [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) objects and their properties. |
| [Get landingPage](https://learn.microsoft.com/en-us/graph/api/landingpage-get?view=graph-rest-1.0) | [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) | Get a [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) associated with an attack simulation campaign for a tenant. |
| **Login page** |  |  |
| [List loginPages](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-loginpage?view=graph-rest-1.0) | [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) collection | Get a list of the [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) objects and their properties. |
| [Get loginPage](https://learn.microsoft.com/en-us/graph/api/loginpage-get?view=graph-rest-1.0) | [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) | Get a [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) associated with an attack simulation campaign for a tenant. |
| **Payload** |  |  |
| [List payloads](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-payloads?view=graph-rest-1.0) | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) collection | Get the payload resources from the payloads navigation property. |
| [Get payload](https://learn.microsoft.com/en-us/graph/api/payload-get?view=graph-rest-1.0) | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) | Get the payload resource from the payloads navigation property. |
| **Simulation** |  |  |
| [List simulations](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-simulations?view=graph-rest-1.0) | [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) collection | Get a list of attack simulation campaigns for a tenant. |
| [Get simulations](https://learn.microsoft.com/en-us/graph/api/simulation-get?view=graph-rest-1.0) | [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) | Get an attack simulation campaigns for a tenant. |
| [Create simulations](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-post-simulation?view=graph-rest-1.0) | [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) | Create a new attack simulation campaigns for a tenant. |
| [Update simulations](https://learn.microsoft.com/en-us/graph/api/simulation-update?view=graph-rest-1.0) | [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) | Update a attack simulation campaigns for a tenant. |
| [Delete simulations](https://learn.microsoft.com/en-us/graph/api/simulation-delete?view=graph-rest-1.0) | [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) | Delete a attack simulation campaigns for a tenant. |
| **Simulation automation** |  |  |
| [List simulationAutomations](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-simulationautomations?view=graph-rest-1.0) | [simulationAutomation](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomation?view=graph-rest-1.0) collection | Get a list of attack simulation automations for a tenant. |
| [Get simulationAutomations](https://learn.microsoft.com/en-us/graph/api/simulationautomation-get?view=graph-rest-1.0) | [simulationAutomation](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomation?view=graph-rest-1.0) | Get an attack simulation automations for a tenant. |
| **Training** |  |  |
| [List trainings](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-trainings?view=graph-rest-1.0) | [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) collection | Get a list of the [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) objects and their properties. |
| [Get training](https://learn.microsoft.com/en-us/graph/api/training-get?view=graph-rest-1.0) | [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) | Get an attack simulation [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) for a tenant. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| endUserNotifications | [endUserNotification](https://learn.microsoft.com/en-us/graph/api/resources/endusernotification?view=graph-rest-1.0) collection | Represents an end user's notification for an attack simulation training. |
| landingPages | [landingPage](https://learn.microsoft.com/en-us/graph/api/resources/landingpage?view=graph-rest-1.0) collection | Represents an attack simulation training landing page. |
| loginPages | [loginPage](https://learn.microsoft.com/en-us/graph/api/resources/loginpage?view=graph-rest-1.0) collection | Represents an attack simulation training login page. |
| operations | [attackSimulationOperation](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationoperation?view=graph-rest-1.0) collection | Represents an attack simulation training operation. |
| payloads | [payload](https://learn.microsoft.com/en-us/graph/api/resources/payload?view=graph-rest-1.0) collection | Represents an attack simulation training campaign payload in a tenant. |
| simulationAutomations | [simulationAutomation](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomation?view=graph-rest-1.0) collection | Represents simulation automation created to run on a tenant. |
| simulations | [simulation](https://learn.microsoft.com/en-us/graph/api/resources/simulation?view=graph-rest-1.0) collection | Represents an attack simulation training campaign in a tenant. |
| trainings | [training](https://learn.microsoft.com/en-us/graph/api/resources/training?view=graph-rest-1.0) collection | Represents details about attack simulation trainings. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attackSimulationRoot"
}
```
