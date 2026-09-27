<!-- Source: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Microsoft Intune Data Warehouse API

The Intune Data Warehouse API lets you access your Intune data in a machine-readable format for use in your favorite analytics tool. You can use the API to build reports that provide insight into your enterprise mobile environment. The API uses the OData protocol, which follows standard patterns for:

- Request and response headers
- Status codes
- HTTP methods
- URL conventions
- Media types
- Payload formats
- Query options

The OData \(Open Data Protocol\) is an Organization for the Advancement of Structured Information Standards \(OASIS\) standard that defines the best practice for building and consuming RESTful APIs. The Intune Data Warehouse uses OData version 4.0.

This reference section provides an overview of endpoints, supported HTTP methods, return payload formats, and documentation of the Intune Data Warehouse data model.

Important

You can try out the latest functionality of the Data Warehouse by using the beta version. To use the beta version, your URL must contain the query parameter `api-version=beta`. The beta version offers features before they are made generally available as a supported service. As Intune adds new features, the beta version may change behavior and data contracts. Any custom code or reporting tools dependent on the beta version may break with ongoing updates.

## OData custom client

You can access the Intune Data Warehouse data model through RESTful endpoints. To gain access to your data, your client must authorize with Microsoft Entra ID using OAuth 2.0. You first set up a web app and a client app in Azure, grant permissions to the client. Your local client gets authorization and can then communicate with the Data Warehouse endpoints.

For more information, see [Get data from the Data Warehouse API with a REST client](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/setup-rest-client).

Note

You can access the [GitHub Intune Data Warehouse repo](https://github.com/Microsoft/Intune-Data-Warehouse) on Github for code samples.

## Interacting with the API

The API requires authorization with Microsoft Entra ID. Microsoft Entra ID uses OAuth 2.0. Once authorized, you can get data from the API using an HTTP GET verb and contacting the exposed entity collections. For details see:

- [Authorization](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-api-endpoints#authorization)
- [API URL Structure](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-api-endpoints#api-url-structure)

## Intune Data Warehouse data model

OData defines an abstract data model and a protocol that let any client access information exposed by any data source. The data model documentation topic contains an explanation of the namespaces, entities, and return objects in the Intune Data Warehouse data model. For more information, see [Data Warehouse Data Model](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-data-model).

## Next steps

Learn more about working with Microsoft Entra ID by reading the [Authentication Scenarios for Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-scenarios).

Find OData resources at [odata.org](https://www.odata.org).

Review the OData Version 4.0 standard at [OData Version 4.0](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html).
