<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-user-attribute-builder -->
<!-- Sitemap-Last-Modified: 2025-06-06 -->

# Native authentication SDK attribute builder

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In native authentication, the information you collect from the user during sign-up is configured in the user flow in the Microsoft Entra admin center. The name of the user attribute as it appears in the Microsoft Entra admin center is different from the variable name that you use when you reference it in your app.

Fortunately, the native authentication SDK enables you to build the user attributes and assign values to them before you use them in the SDKs `signUp()` method.

## Build user attributes

- [Android \(Kotlin\)](#tabpanel_1_android-kotlin)
- [iOS/macOS \(Swift\)](#tabpanel_1_ios-macos-swift)

To build user attributes in the Android SDK:

- Use the utility class `UserAttribute.Builder` that the SDK provides. The `UserAttributes.Builder` class contains methods whose parameter is the value that you collect from the user.
- Identify the user attributes that you want to build, then use the following code snippet to build them:

  ```kotlin
      //build the user attributes, both built-in and custom attributes
      val userAttributes = UserAttributes.Builder()
          .country(country)
          .city(city)
          .displayName(displayName)
          .givenName(givenName)
          .jobTitle(jobTitle)
          .postalCode(postalCode)
          .state(state)
          .streetAddress(streetAddress)
          .surname(surname)
          .build() 

      CoroutineScope(Dispatchers.Main).launch {
          //use the userAttributes variable in your signUp method 
          val actionResult = authAuthClientInstance.signUp(
              username = emailAddress,
              attributes = userAttributes
          )
      }  
  ```

- To build [custom attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-user-attributes#custom-user-attributes), use `UserAttribute.Builder` class `customAttribute()` method. The method accepts the custom attribute's programmable name, and the value of the attribute:

  ```kotlin
     val userAttributes = UserAttributes.Builder()
         .customAttribute("extension_2588abcdwhtfeehjjeeqwertc_loyaltyNumber", loyaltyNumber)
         .build() 

     CoroutineScope(Dispatchers.Main).launch {
         //use the userAttributes variable in your signUp method 
         val actionResult = authAuthClientInstance.signUp(
             username = emailAddress,
             attributes = userAttributes
         )
     }  
  ```

To build user attributes in the iOS/macOS MSAL SDK:

- Identify the user attributes that you want to build, then create a dictionary variable, where:

  - the `key` is the programmable name of the user attribute, as a string. The programmable name can be for built-in or custom attribute.
  - the `value` in the value of the user attribute that you collect from the user.

- Identify the user attributes that you want to build, then use the following code snippet to build them:

  ```swift
     let attributes = [
         "country": "United States",
         "city": "Redmond",
         "displayName": displayName,
         "givenName": givenName,
         "jobTitle": jobTitle,
         "postalCode": postalCode,
         "state": state,
         "streetAddress": streetAddress,
         "surname": surname
     ]

     authAuthClientInstance.signUp(username: email, attributes: attributes, delegate: self)
  ```

- To build [custom attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-user-attributes#custom-user-attributes), use `UserAttribute.Builder` class `customAttribute()` method. The method accepts the custom attribute's programmable name, and the value of the attribute:

  ```swift
          let attributes = [
              "country": "United States",
              "extension_2588abcdwhtfeehjjeeqwertc_loyaltyNumber", loyaltyNumber
          ]

          authAuthClientInstance.signUp(username: email, attributes: attributes, delegate: self)
  ```

To learn more about the programmable names of user profile attributes, see the [User profile attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-user-attributes) article.

## Related content

- [Native authentication challenge types](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-challenge-types)
- [iOS/macOS native authentication tutorials](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-ios-macos-app)
- [Android native authentication tutorials](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-android-app)
