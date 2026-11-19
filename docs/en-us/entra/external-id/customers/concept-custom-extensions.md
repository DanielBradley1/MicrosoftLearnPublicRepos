<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-custom-extensions -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Custom authentication extensions in Microsoft Entra External ID

Custom authentication extensions add business logic at specific events in Microsoft Entra External ID sign-up and sign-in flows. An extension listens for an event and calls a REST API endpoint where you define a workflow action. For example, an extension can validate submitted sign-up attributes or add claims from an external system before token issuance.

**Applies to external tenants:** Feature support varies by authentication approach and API or SDK version. Compare Microsoft-hosted authentication, Embedded native authentication, and Bring Your Own UX \(BYO UX\) in the [authentication approach overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach). Check feature availability in the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability).

## Event coverage by authentication approach

Important

The Native Authentication API V2 is in preview. The [Native Authentication API V1](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api-v1) remains generally available. See the [Supplemental Terms of Use for Microsoft Azure Previews](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) for legal terms that apply to preview features.

Tenant, application, and user-flow configuration define the extension and the event listener. The event also needs a supported execution point in the selected integration. Sharing tenant policies doesn't imply that every authentication approach executes every event.

Confirm event availability for your approach and API or SDK version in the [custom authentication extension event comparison](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#custom-authentication-extension-applicability).

Use the event's documented inputs and responses. Support for the four documented events doesn't establish password-migration hooks, password-update synchronization, or arbitrary context propagation. For architectural guidance, see [Choose an authentication approach](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach).

Configure two components: a custom authentication extension and a REST API. The extension specifies the REST API endpoint, when to call it, and the credentials for the call. You can create extensions at the following points in the authentication flow:

- During sign-up, before or after attribute collection.
- When sending an email one-time passcode through a configured email provider.
- Upon token issuance, before the configured claims are added to the application's token.

[![Diagram of attribute collection and token issuance extension points.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-custom-extensions/authentication-flow-events-inline.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/concept-custom-extensions/authentication-flow-events-expanded.png#lightbox)

When an applicable event runs, Microsoft Entra ID calls your REST API with the event's defined payload. The REST API returns one of the actions supported by that event. Use the event's documented payload to determine which application context is available.

## Attribute collection start and submit events

Use these events with Microsoft-hosted authentication to prefill fields, validate entries, modify attributes, or block self-service sign-up. `OnAttributeCollectionStart` and `OnAttributeCollectionSubmit` aren't supported for Embedded native authentication or Bring Your Own UX. Ordinary attribute collection through the Native Authentication API doesn't enable these extension events; follow the [attribute collection contract](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-user-attributes) instead.

- **OnAttributeCollectionStart** - This event runs before attribute collection. It can prefill attributes or block sign-up, for example based on the customer's email domain. The supported actions are:

  - **continueWithDefaultBehavior** - Continue with the configured attribute collection.
  - **setPreFillValues** - Prefill attributes in the sign-up form.
  - **showBlockPage** - Show an error message and block the user from signing up.

- **OnAttributeCollectionSubmit** - The OnAttributeCollectionSubmit event occurs after the user enters and submits attributes. This event can be used for scenarios like validating or modifying the information provided by the user. For example, you can validate an invitation code or partner number, modify an address format, or return an error.

  - **continueWithDefaultBehavior** - Continue with the sign-up flow.
  - **modifyAttributeValues** - Overwrite the values the user submitted in the sign-up form.
  - **showValidationError** - Return an error based on the submitted values.
  - **showBlockPage** - Show an error message and block the user from signing up.

To configure the attribute collection start and submit events, you create a custom authentication extension REST API. When an event fires, Microsoft Entra ID sends an HTTP request to your REST API endpoint. The REST API can be an Azure Function, Azure Logic App, or another publicly available API endpoint. Your REST API endpoint is responsible for defining the workflow actions to take.

For details, see [Add attribute collection custom extensions to your user flow](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-attribute-collection?context=/entra/external-id/customers/context/customers-context).

For attribute collection without these extension events, see [Native authentication user attributes](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-user-attributes).

## Email one-time passcode send event

The `OnOtpSend` event lets a configured provider send email one-time passcodes. It doesn't register an MFA method or make email eligible as both the first and second factor. The service's current transaction still determines the required verification.

For setup, see [Configure a custom email provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-email-otp-get-started).

## Token issuance start event

The token issuance start event occurs after a user completes all authentication challenges, just before a security token is issued.

When users authenticate to your application with Microsoft Entra ID, a security token is returned to your application. The security token contains claims that are statements about the user, such as name, unique identifier, or application roles. Beyond the default set of claims that are contained in the security token, you can define your own custom claims from external systems using a REST API you develop.

In some cases, key data might be stored in systems external to Microsoft Entra, such as a secondary email, billing tier, or sensitive information. It's not always feasible for the information in the external system to be stored in the Microsoft Entra directory. For these scenarios, you can use a custom authentication extension and a custom claims provider to add this external data into tokens returned to your application.

A token issuance event extension involves the following components:

- **Custom claims provider**. A custom claims provider is a type of custom authentication extension that fetches data from external systems. The custom claims provider specifies the attributes to be added to the security token that is returned to your application. Multiple claims providers can share the same custom extension, so a different set of attributes can be added to the security token for each application.
- **REST API endpoint**. When an event fires, Microsoft Entra ID sends an HTTP request to your REST API endpoint. The REST API can be an Azure Function, Azure Logic App, or some other publicly available API endpoint. Your REST API endpoint interfaces with various data stores, including downstream databases, existing APIs, Lightweight Directory Access Protocol \(LDAP\) directories, or other stores that contain the attributes you want to add to the token configuration.

  The REST API returns an HTTP response, or action, back to Microsoft Entra ID containing the attributes. These attributes aren't automatically added to a token. Instead, an application's claims mapping policy must be configured for any attribute to be included in the token.

For details, see:

- [About custom authentication extensions](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-overview?context=/entra/external-id/customers/context/customers-context).
- [Configure a custom claims provider for a token issuance event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration?context=/azure/active-directory/external-identities/customers/context/customers-context) using a custom claims provider.

## Related content

To learn more about custom authentication extensions, see the following articles in the Microsoft identity platform documentation:

- [Custom authentication extensions](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-overview).
- [Create a REST API with a token issuance start event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-setup).
- [Configure a custom claims provider for a token issuance event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration).
- [Configure custom authentication extensions for attribute collection start and submit events](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-attribute-collection) with a sample OpenID Connect application.

See the [Microsoft Entra External ID Developer Center](https://aka.ms/ciam/dev) for the latest developer content and resources.
