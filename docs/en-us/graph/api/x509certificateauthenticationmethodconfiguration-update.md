<!-- Source: https://learn.microsoft.com/en-us/graph/api/x509certificateauthenticationmethodconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Update x509CertificateAuthenticationMethodConfiguration

Namespace: microsoft.graph

Update the properties of the [X.509 certificate authentication method](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.AuthenticationMethod | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.AuthenticationMethod | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Authentication Policy Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /policies/authenticationMethodsPolicy/authenticationMethodConfigurations/x509Certificate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

The following properties can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateAuthorityScopes | [x509CertificateAuthorityScope](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthorityscope?view=graph-rest-1.0) collection | Defines configuration to allow a group of users to use certificates from specific issuing certificate authorities to successfully authenticate. |
| certificateUserBindings | [x509CertificateUserBinding](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateuserbinding?view=graph-rest-1.0) collection | Defines fields in the X.509 certificate that map to attributes of the Microsoft Entra user object in order to bind the certificate to the user. The **priority** of the object determines the order in which the binding is carried out. The first binding that matches will be used and the rest ignored. |
| authenticationModeConfiguration | [x509CertificateAuthenticationModeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmodeconfiguration?view=graph-rest-1.0) | Defines strong authentication configurations. This configuration includes the default authentication mode and the different rules for strong authentication bindings. |
| crlValidationConfiguration | [x509CertificateCRLValidationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificatecrlvalidationconfiguration?view=graph-rest-1.0) | Determines whether certificate based authentication should fail if the issuing CA doesn't have a valid certificate revocation list configured. |
| issuerHintsConfiguration | [x509CertificateIssuerHintsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateissuerhintsconfiguration?view=graph-rest-1.0) | Determines whether issuer\(CA\) hints are sent back to the client side to filter the certificates shown in certificate picker. |
| state | authenticationMethodState | The possible values are: `enabled`, `disabled`. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |

> **Note:** The `@odata.type` property with a value of `#microsoft.graph.x509CertificateAuthenticationMethodConfiguration` must be included in the body.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Request

The following is an example of an update request with the following settings:

- Enables the x509 certificate authentication method in the tenant.
- Configures only one user binding between the certificate **PrincipalName** and the Microsoft Entra ID **onPremisesUserPrincipalName** properties.
- Defines multi-factor authentication as requirement.
- Configures the binding rules for the strong authentication method against the rule type.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/x509Certificate
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.x509CertificateAuthenticationMethodConfiguration",
    "id": "X509Certificate",
    "state": "enabled",
    "certificateUserBindings": [
        {
            "x509CertificateField": "PrincipalName",
            "userProperty": "onPremisesUserPrincipalName",
            "priority": 1
        }
    ],
    "authenticationModeConfiguration": {
        "x509CertificateAuthenticationDefaultMode": "x509CertificateMultiFactor",
        "rules": [
            {
                "x509CertificateRuleType": "issuerSubject",
                "identifier": "CN=ContosoCA,DC=Contoso,DC=org ",
                "x509CertificateAuthenticationMode": "x509CertificateMultiFactor"
            },
            {
                "x509CertificateRuleType": "policyOID",
                "identifier": "1.2.3.4",
                "x509CertificateAuthenticationMode": "x509CertificateMultiFactor"
            }
        ]
    },
    "certificateAuthorityScopes": [
        {
            "subjectKeyIdentifier": "aaaaaaaabbbbcccc111122222222222222333333",
            "publicKeyInfrastructureIdentifier": "Contoso PKI",
            "includeTargets": [
            {
                "id": "aaaaaaaa-bbbb-cccc-1111-222222222222",
                "targetType": "group"
            }
            ]
        }
    ],
    "issuerHintsConfiguration": {
        "state": "enabled"
    },
    "crlValidationConfiguration": {
        "state": "disabled",
        "exemptedCertificateAuthoritiesSubjectKeyIdentifiers": []
    },
    "includeTargets": [
        {
            "targetType": "group",
            "id": "all_users",
            "isRegistrationRequired": false
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new X509CertificateAuthenticationMethodConfiguration
{
	OdataType = "#microsoft.graph.x509CertificateAuthenticationMethodConfiguration",
	Id = "X509Certificate",
	State = AuthenticationMethodState.Enabled,
	CertificateUserBindings = new List<X509CertificateUserBinding>
	{
		new X509CertificateUserBinding
		{
			X509CertificateField = "PrincipalName",
			UserProperty = "onPremisesUserPrincipalName",
			Priority = 1,
		},
	},
	AuthenticationModeConfiguration = new X509CertificateAuthenticationModeConfiguration
	{
		X509CertificateAuthenticationDefaultMode = X509CertificateAuthenticationMode.X509CertificateMultiFactor,
		Rules = new List<X509CertificateRule>
		{
			new X509CertificateRule
			{
				X509CertificateRuleType = X509CertificateRuleType.IssuerSubject,
				Identifier = "CN=ContosoCA,DC=Contoso,DC=org ",
				X509CertificateAuthenticationMode = X509CertificateAuthenticationMode.X509CertificateMultiFactor,
			},
			new X509CertificateRule
			{
				X509CertificateRuleType = X509CertificateRuleType.PolicyOID,
				Identifier = "1.2.3.4",
				X509CertificateAuthenticationMode = X509CertificateAuthenticationMode.X509CertificateMultiFactor,
			},
		},
	},
	CertificateAuthorityScopes = new List<X509CertificateAuthorityScope>
	{
		new X509CertificateAuthorityScope
		{
			SubjectKeyIdentifier = "aaaaaaaabbbbcccc111122222222222222333333",
			PublicKeyInfrastructureIdentifier = "Contoso PKI",
			IncludeTargets = new List<IncludeTarget>
			{
				new IncludeTarget
				{
					Id = "aaaaaaaa-bbbb-cccc-1111-222222222222",
					TargetType = AuthenticationMethodTargetType.Group,
				},
			},
		},
	},
	IssuerHintsConfiguration = new X509CertificateIssuerHintsConfiguration
	{
		State = X509CertificateIssuerHintsState.Enabled,
	},
	CrlValidationConfiguration = new X509CertificateCRLValidationConfiguration
	{
		State = X509CertificateCRLValidationConfigurationState.Disabled,
		ExemptedCertificateAuthoritiesSubjectKeyIdentifiers = new List<string>
		{
		},
	},
	IncludeTargets = new List<AuthenticationMethodTarget>
	{
		new AuthenticationMethodTarget
		{
			TargetType = AuthenticationMethodTargetType.Group,
			Id = "all_users",
			IsRegistrationRequired = false,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AuthenticationMethodsPolicy.AuthenticationMethodConfigurations["{authenticationMethodConfiguration-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAuthenticationMethodConfiguration()
id := "X509Certificate"
requestBody.SetId(&id) 
state := graphmodels.ENABLED_AUTHENTICATIONMETHODSTATE 
requestBody.SetState(&state) 


x509CertificateUserBinding := graphmodels.NewX509CertificateUserBinding()
x509CertificateField := "PrincipalName"
x509CertificateUserBinding.SetX509CertificateField(&x509CertificateField) 
userProperty := "onPremisesUserPrincipalName"
x509CertificateUserBinding.SetUserProperty(&userProperty) 
priority := int32(1)
x509CertificateUserBinding.SetPriority(&priority) 

certificateUserBindings := []graphmodels.X509CertificateUserBindingable {
	x509CertificateUserBinding,
}
requestBody.SetCertificateUserBindings(certificateUserBindings)
authenticationModeConfiguration := graphmodels.NewX509CertificateAuthenticationModeConfiguration()
x509CertificateAuthenticationDefaultMode := graphmodels.X509CERTIFICATEMULTIFACTOR_X509CERTIFICATEAUTHENTICATIONMODE 
authenticationModeConfiguration.SetX509CertificateAuthenticationDefaultMode(&x509CertificateAuthenticationDefaultMode) 


x509CertificateRule := graphmodels.NewX509CertificateRule()
x509CertificateRuleType := graphmodels.ISSUERSUBJECT_X509CERTIFICATERULETYPE 
x509CertificateRule.SetX509CertificateRuleType(&x509CertificateRuleType) 
identifier := "CN=ContosoCA,DC=Contoso,DC=org "
x509CertificateRule.SetIdentifier(&identifier) 
x509CertificateAuthenticationMode := graphmodels.X509CERTIFICATEMULTIFACTOR_X509CERTIFICATEAUTHENTICATIONMODE 
x509CertificateRule.SetX509CertificateAuthenticationMode(&x509CertificateAuthenticationMode) 
x509CertificateRule1 := graphmodels.NewX509CertificateRule()
x509CertificateRuleType := graphmodels.POLICYOID_X509CERTIFICATERULETYPE 
x509CertificateRule1.SetX509CertificateRuleType(&x509CertificateRuleType) 
identifier := "1.2.3.4"
x509CertificateRule1.SetIdentifier(&identifier) 
x509CertificateAuthenticationMode := graphmodels.X509CERTIFICATEMULTIFACTOR_X509CERTIFICATEAUTHENTICATIONMODE 
x509CertificateRule1.SetX509CertificateAuthenticationMode(&x509CertificateAuthenticationMode) 

rules := []graphmodels.X509CertificateRuleable {
	x509CertificateRule,
	x509CertificateRule1,
}
authenticationModeConfiguration.SetRules(rules)
requestBody.SetAuthenticationModeConfiguration(authenticationModeConfiguration)


x509CertificateAuthorityScope := graphmodels.NewX509CertificateAuthorityScope()
subjectKeyIdentifier := "aaaaaaaabbbbcccc111122222222222222333333"
x509CertificateAuthorityScope.SetSubjectKeyIdentifier(&subjectKeyIdentifier) 
publicKeyInfrastructureIdentifier := "Contoso PKI"
x509CertificateAuthorityScope.SetPublicKeyInfrastructureIdentifier(&publicKeyInfrastructureIdentifier) 


includeTarget := graphmodels.NewIncludeTarget()
id := "aaaaaaaa-bbbb-cccc-1111-222222222222"
includeTarget.SetId(&id) 
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
includeTarget.SetTargetType(&targetType) 

includeTargets := []graphmodels.IncludeTargetable {
	includeTarget,
}
x509CertificateAuthorityScope.SetIncludeTargets(includeTargets)

certificateAuthorityScopes := []graphmodels.X509CertificateAuthorityScopeable {
	x509CertificateAuthorityScope,
}
requestBody.SetCertificateAuthorityScopes(certificateAuthorityScopes)
issuerHintsConfiguration := graphmodels.NewX509CertificateIssuerHintsConfiguration()
state := graphmodels.ENABLED_X509CERTIFICATEISSUERHINTSSTATE 
issuerHintsConfiguration.SetState(&state) 
requestBody.SetIssuerHintsConfiguration(issuerHintsConfiguration)
crlValidationConfiguration := graphmodels.NewX509CertificateCRLValidationConfiguration()
state := graphmodels.DISABLED_X509CERTIFICATECRLVALIDATIONCONFIGURATIONSTATE 
crlValidationConfiguration.SetState(&state) 
exemptedCertificateAuthoritiesSubjectKeyIdentifiers := []string {

}
crlValidationConfiguration.SetExemptedCertificateAuthoritiesSubjectKeyIdentifiers(exemptedCertificateAuthoritiesSubjectKeyIdentifiers)
requestBody.SetCrlValidationConfiguration(crlValidationConfiguration)


authenticationMethodTarget := graphmodels.NewAuthenticationMethodTarget()
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
authenticationMethodTarget.SetTargetType(&targetType) 
id := "all_users"
authenticationMethodTarget.SetId(&id) 
isRegistrationRequired := false
authenticationMethodTarget.SetIsRegistrationRequired(&isRegistrationRequired) 

includeTargets := []graphmodels.AuthenticationMethodTargetable {
	authenticationMethodTarget,
}
requestBody.SetIncludeTargets(includeTargets)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationMethodConfigurations, err := graphClient.Policies().AuthenticationMethodsPolicy().AuthenticationMethodConfigurations().ByAuthenticationMethodConfigurationId("authenticationMethodConfiguration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

X509CertificateAuthenticationMethodConfiguration authenticationMethodConfiguration = new X509CertificateAuthenticationMethodConfiguration();
authenticationMethodConfiguration.setOdataType("#microsoft.graph.x509CertificateAuthenticationMethodConfiguration");
authenticationMethodConfiguration.setId("X509Certificate");
authenticationMethodConfiguration.setState(AuthenticationMethodState.Enabled);
LinkedList<X509CertificateUserBinding> certificateUserBindings = new LinkedList<X509CertificateUserBinding>();
X509CertificateUserBinding x509CertificateUserBinding = new X509CertificateUserBinding();
x509CertificateUserBinding.setX509CertificateField("PrincipalName");
x509CertificateUserBinding.setUserProperty("onPremisesUserPrincipalName");
x509CertificateUserBinding.setPriority(1);
certificateUserBindings.add(x509CertificateUserBinding);
authenticationMethodConfiguration.setCertificateUserBindings(certificateUserBindings);
X509CertificateAuthenticationModeConfiguration authenticationModeConfiguration = new X509CertificateAuthenticationModeConfiguration();
authenticationModeConfiguration.setX509CertificateAuthenticationDefaultMode(X509CertificateAuthenticationMode.X509CertificateMultiFactor);
LinkedList<X509CertificateRule> rules = new LinkedList<X509CertificateRule>();
X509CertificateRule x509CertificateRule = new X509CertificateRule();
x509CertificateRule.setX509CertificateRuleType(X509CertificateRuleType.IssuerSubject);
x509CertificateRule.setIdentifier("CN=ContosoCA,DC=Contoso,DC=org ");
x509CertificateRule.setX509CertificateAuthenticationMode(X509CertificateAuthenticationMode.X509CertificateMultiFactor);
rules.add(x509CertificateRule);
X509CertificateRule x509CertificateRule1 = new X509CertificateRule();
x509CertificateRule1.setX509CertificateRuleType(X509CertificateRuleType.PolicyOID);
x509CertificateRule1.setIdentifier("1.2.3.4");
x509CertificateRule1.setX509CertificateAuthenticationMode(X509CertificateAuthenticationMode.X509CertificateMultiFactor);
rules.add(x509CertificateRule1);
authenticationModeConfiguration.setRules(rules);
authenticationMethodConfiguration.setAuthenticationModeConfiguration(authenticationModeConfiguration);
LinkedList<X509CertificateAuthorityScope> certificateAuthorityScopes = new LinkedList<X509CertificateAuthorityScope>();
X509CertificateAuthorityScope x509CertificateAuthorityScope = new X509CertificateAuthorityScope();
x509CertificateAuthorityScope.setSubjectKeyIdentifier("aaaaaaaabbbbcccc111122222222222222333333");
x509CertificateAuthorityScope.setPublicKeyInfrastructureIdentifier("Contoso PKI");
LinkedList<IncludeTarget> includeTargets = new LinkedList<IncludeTarget>();
IncludeTarget includeTarget = new IncludeTarget();
includeTarget.setId("aaaaaaaa-bbbb-cccc-1111-222222222222");
includeTarget.setTargetType(AuthenticationMethodTargetType.Group);
includeTargets.add(includeTarget);
x509CertificateAuthorityScope.setIncludeTargets(includeTargets);
certificateAuthorityScopes.add(x509CertificateAuthorityScope);
authenticationMethodConfiguration.setCertificateAuthorityScopes(certificateAuthorityScopes);
X509CertificateIssuerHintsConfiguration issuerHintsConfiguration = new X509CertificateIssuerHintsConfiguration();
issuerHintsConfiguration.setState(X509CertificateIssuerHintsState.Enabled);
authenticationMethodConfiguration.setIssuerHintsConfiguration(issuerHintsConfiguration);
X509CertificateCRLValidationConfiguration crlValidationConfiguration = new X509CertificateCRLValidationConfiguration();
crlValidationConfiguration.setState(X509CertificateCRLValidationConfigurationState.Disabled);
LinkedList<String> exemptedCertificateAuthoritiesSubjectKeyIdentifiers = new LinkedList<String>();
crlValidationConfiguration.setExemptedCertificateAuthoritiesSubjectKeyIdentifiers(exemptedCertificateAuthoritiesSubjectKeyIdentifiers);
authenticationMethodConfiguration.setCrlValidationConfiguration(crlValidationConfiguration);
LinkedList<AuthenticationMethodTarget> includeTargets1 = new LinkedList<AuthenticationMethodTarget>();
AuthenticationMethodTarget authenticationMethodTarget = new AuthenticationMethodTarget();
authenticationMethodTarget.setTargetType(AuthenticationMethodTargetType.Group);
authenticationMethodTarget.setId("all_users");
authenticationMethodTarget.setIsRegistrationRequired(false);
includeTargets1.add(authenticationMethodTarget);
authenticationMethodConfiguration.setIncludeTargets(includeTargets1);
AuthenticationMethodConfiguration result = graphClient.policies().authenticationMethodsPolicy().authenticationMethodConfigurations().byAuthenticationMethodConfigurationId("{authenticationMethodConfiguration-id}").patch(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationMethodConfiguration = {
    '@odata.type': '#microsoft.graph.x509CertificateAuthenticationMethodConfiguration',
    id: 'X509Certificate',
    state: 'enabled',
    certificateUserBindings: [
        {
            x509CertificateField: 'PrincipalName',
            userProperty: 'onPremisesUserPrincipalName',
            priority: 1
        }
    ],
    authenticationModeConfiguration: {
        x509CertificateAuthenticationDefaultMode: 'x509CertificateMultiFactor',
        rules: [
            {
                x509CertificateRuleType: 'issuerSubject',
                identifier: 'CN=ContosoCA,DC=Contoso,DC=org ',
                x509CertificateAuthenticationMode: 'x509CertificateMultiFactor'
            },
            {
                x509CertificateRuleType: 'policyOID',
                identifier: '1.2.3.4',
                x509CertificateAuthenticationMode: 'x509CertificateMultiFactor'
            }
        ]
    },
    certificateAuthorityScopes: [
        {
            subjectKeyIdentifier: 'aaaaaaaabbbbcccc111122222222222222333333',
            publicKeyInfrastructureIdentifier: 'Contoso PKI',
            includeTargets: [
            {
                id: 'aaaaaaaa-bbbb-cccc-1111-222222222222',
                targetType: 'group'
            }
            ]
        }
    ],
    issuerHintsConfiguration: {
        state: 'enabled'
    },
    crlValidationConfiguration: {
        state: 'disabled',
        exemptedCertificateAuthoritiesSubjectKeyIdentifiers: []
    },
    includeTargets: [
        {
            targetType: 'group',
            id: 'all_users',
            isRegistrationRequired: false
        }
    ]
};

await client.api('/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/x509Certificate')
	.update(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\X509CertificateAuthenticationMethodConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodState;
use Microsoft\Graph\Generated\Models\X509CertificateUserBinding;
use Microsoft\Graph\Generated\Models\X509CertificateAuthenticationModeConfiguration;
use Microsoft\Graph\Generated\Models\X509CertificateAuthenticationMode;
use Microsoft\Graph\Generated\Models\X509CertificateRule;
use Microsoft\Graph\Generated\Models\X509CertificateRuleType;
use Microsoft\Graph\Generated\Models\X509CertificateAuthorityScope;
use Microsoft\Graph\Generated\Models\IncludeTarget;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTargetType;
use Microsoft\Graph\Generated\Models\X509CertificateIssuerHintsConfiguration;
use Microsoft\Graph\Generated\Models\X509CertificateIssuerHintsState;
use Microsoft\Graph\Generated\Models\X509CertificateCRLValidationConfiguration;
use Microsoft\Graph\Generated\Models\X509CertificateCRLValidationConfigurationState;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTarget;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new X509CertificateAuthenticationMethodConfiguration();
$requestBody->setOdataType('#microsoft.graph.x509CertificateAuthenticationMethodConfiguration');
$requestBody->setId('X509Certificate');
$requestBody->setState(new AuthenticationMethodState('enabled'));
$certificateUserBindingsX509CertificateUserBinding1 = new X509CertificateUserBinding();
$certificateUserBindingsX509CertificateUserBinding1->setX509CertificateField('PrincipalName');
$certificateUserBindingsX509CertificateUserBinding1->setUserProperty('onPremisesUserPrincipalName');
$certificateUserBindingsX509CertificateUserBinding1->setPriority(1);
$certificateUserBindingsArray []= $certificateUserBindingsX509CertificateUserBinding1;
$requestBody->setCertificateUserBindings($certificateUserBindingsArray);

$authenticationModeConfiguration = new X509CertificateAuthenticationModeConfiguration();
$authenticationModeConfiguration->setX509CertificateAuthenticationDefaultMode(new X509CertificateAuthenticationMode('x509CertificateMultiFactor'));
$rulesX509CertificateRule1 = new X509CertificateRule();
$rulesX509CertificateRule1->setX509CertificateRuleType(new X509CertificateRuleType('issuerSubject'));
$rulesX509CertificateRule1->setIdentifier('CN=ContosoCA,DC=Contoso,DC=org ');
$rulesX509CertificateRule1->setX509CertificateAuthenticationMode(new X509CertificateAuthenticationMode('x509CertificateMultiFactor'));
$rulesArray []= $rulesX509CertificateRule1;
$rulesX509CertificateRule2 = new X509CertificateRule();
$rulesX509CertificateRule2->setX509CertificateRuleType(new X509CertificateRuleType('policyOID'));
$rulesX509CertificateRule2->setIdentifier('1.2.3.4');
$rulesX509CertificateRule2->setX509CertificateAuthenticationMode(new X509CertificateAuthenticationMode('x509CertificateMultiFactor'));
$rulesArray []= $rulesX509CertificateRule2;
$authenticationModeConfiguration->setRules($rulesArray);

$requestBody->setAuthenticationModeConfiguration($authenticationModeConfiguration);
$certificateAuthorityScopesX509CertificateAuthorityScope1 = new X509CertificateAuthorityScope();
$certificateAuthorityScopesX509CertificateAuthorityScope1->setSubjectKeyIdentifier('aaaaaaaabbbbcccc111122222222222222333333');
$certificateAuthorityScopesX509CertificateAuthorityScope1->setPublicKeyInfrastructureIdentifier('Contoso PKI');
$includeTargetsIncludeTarget1 = new IncludeTarget();
$includeTargetsIncludeTarget1->setId('aaaaaaaa-bbbb-cccc-1111-222222222222');
$includeTargetsIncludeTarget1->setTargetType(new AuthenticationMethodTargetType('group'));
$includeTargetsArray []= $includeTargetsIncludeTarget1;
$certificateAuthorityScopesX509CertificateAuthorityScope1->setIncludeTargets($includeTargetsArray);

$certificateAuthorityScopesArray []= $certificateAuthorityScopesX509CertificateAuthorityScope1;
$requestBody->setCertificateAuthorityScopes($certificateAuthorityScopesArray);

$issuerHintsConfiguration = new X509CertificateIssuerHintsConfiguration();
$issuerHintsConfiguration->setState(new X509CertificateIssuerHintsState('enabled'));
$requestBody->setIssuerHintsConfiguration($issuerHintsConfiguration);
$crlValidationConfiguration = new X509CertificateCRLValidationConfiguration();
$crlValidationConfiguration->setState(new X509CertificateCRLValidationConfigurationState('disabled'));
$crlValidationConfiguration->setExemptedCertificateAuthoritiesSubjectKeyIdentifiers([]);
$requestBody->setCrlValidationConfiguration($crlValidationConfiguration);
$includeTargetsAuthenticationMethodTarget1 = new AuthenticationMethodTarget();
$includeTargetsAuthenticationMethodTarget1->setTargetType(new AuthenticationMethodTargetType('group'));
$includeTargetsAuthenticationMethodTarget1->setId('all_users');
$includeTargetsAuthenticationMethodTarget1->setIsRegistrationRequired(false);
$includeTargetsArray []= $includeTargetsAuthenticationMethodTarget1;
$requestBody->setIncludeTargets($includeTargetsArray);


$result = $graphServiceClient->policies()->authenticationMethodsPolicy()->authenticationMethodConfigurations()->byAuthenticationMethodConfigurationId('authenticationMethodConfiguration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.x509CertificateAuthenticationMethodConfiguration"
	id = "X509Certificate"
	state = "enabled"
	certificateUserBindings = @(
		@{
			x509CertificateField = "PrincipalName"
			userProperty = "onPremisesUserPrincipalName"
			priority = 
		}
	)
	authenticationModeConfiguration = @{
		x509CertificateAuthenticationDefaultMode = "x509CertificateMultiFactor"
		rules = @(
			@{
				x509CertificateRuleType = "issuerSubject"
				identifier = "CN=ContosoCA,DC=Contoso,DC=org "
				x509CertificateAuthenticationMode = "x509CertificateMultiFactor"
			}
			@{
				x509CertificateRuleType = "policyOID"
				identifier = "1.2.3.4"
				x509CertificateAuthenticationMode = "x509CertificateMultiFactor"
			}
		)
	}
	certificateAuthorityScopes = @(
		@{
			subjectKeyIdentifier = "aaaaaaaabbbbcccc111122222222222222333333"
			publicKeyInfrastructureIdentifier = "Contoso PKI"
			includeTargets = @(
				@{
					id = "aaaaaaaa-bbbb-cccc-1111-222222222222"
					targetType = "group"
				}
			)
		}
	)
	issuerHintsConfiguration = @{
		state = "enabled"
	}
	crlValidationConfiguration = @{
		state = "disabled"
		exemptedCertificateAuthoritiesSubjectKeyIdentifiers = @(
		)
	}
	includeTargets = @(
		@{
			targetType = "group"
			id = "all_users"
			isRegistrationRequired = $false
		}
	)
}

Update-MgPolicyAuthenticationMethodPolicyAuthenticationMethodConfiguration -AuthenticationMethodConfigurationId $authenticationMethodConfigurationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.x509_certificate_authentication_method_configuration import X509CertificateAuthenticationMethodConfiguration
from msgraph.generated.models.authentication_method_state import AuthenticationMethodState
from msgraph.generated.models.x509_certificate_user_binding import X509CertificateUserBinding
from msgraph.generated.models.x509_certificate_authentication_mode_configuration import X509CertificateAuthenticationModeConfiguration
from msgraph.generated.models.x509_certificate_authentication_mode import X509CertificateAuthenticationMode
from msgraph.generated.models.x509_certificate_rule import X509CertificateRule
from msgraph.generated.models.x509_certificate_rule_type import X509CertificateRuleType
from msgraph.generated.models.x509_certificate_authority_scope import X509CertificateAuthorityScope
from msgraph.generated.models.include_target import IncludeTarget
from msgraph.generated.models.authentication_method_target_type import AuthenticationMethodTargetType
from msgraph.generated.models.x509_certificate_issuer_hints_configuration import X509CertificateIssuerHintsConfiguration
from msgraph.generated.models.x509_certificate_issuer_hints_state import X509CertificateIssuerHintsState
from msgraph.generated.models.x509_certificate_c_r_l_validation_configuration import X509CertificateCRLValidationConfiguration
from msgraph.generated.models.x509_certificate_c_r_l_validation_configuration_state import X509CertificateCRLValidationConfigurationState
from msgraph.generated.models.authentication_method_target import AuthenticationMethodTarget
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = X509CertificateAuthenticationMethodConfiguration(
	odata_type = "#microsoft.graph.x509CertificateAuthenticationMethodConfiguration",
	id = "X509Certificate",
	state = AuthenticationMethodState.Enabled,
	certificate_user_bindings = [
		X509CertificateUserBinding(
			x509_certificate_field = "PrincipalName",
			user_property = "onPremisesUserPrincipalName",
			priority = 1,
		),
	],
	authentication_mode_configuration = X509CertificateAuthenticationModeConfiguration(
		x509_certificate_authentication_default_mode = X509CertificateAuthenticationMode.X509CertificateMultiFactor,
		rules = [
			X509CertificateRule(
				x509_certificate_rule_type = X509CertificateRuleType.IssuerSubject,
				identifier = "CN=ContosoCA,DC=Contoso,DC=org ",
				x509_certificate_authentication_mode = X509CertificateAuthenticationMode.X509CertificateMultiFactor,
			),
			X509CertificateRule(
				x509_certificate_rule_type = X509CertificateRuleType.PolicyOID,
				identifier = "1.2.3.4",
				x509_certificate_authentication_mode = X509CertificateAuthenticationMode.X509CertificateMultiFactor,
			),
		],
	),
	certificate_authority_scopes = [
		X509CertificateAuthorityScope(
			subject_key_identifier = "aaaaaaaabbbbcccc111122222222222222333333",
			public_key_infrastructure_identifier = "Contoso PKI",
			include_targets = [
				IncludeTarget(
					id = "aaaaaaaa-bbbb-cccc-1111-222222222222",
					target_type = AuthenticationMethodTargetType.Group,
				),
			],
		),
	],
	issuer_hints_configuration = X509CertificateIssuerHintsConfiguration(
		state = X509CertificateIssuerHintsState.Enabled,
	),
	crl_validation_configuration = X509CertificateCRLValidationConfiguration(
		state = X509CertificateCRLValidationConfigurationState.Disabled,
		exempted_certificate_authorities_subject_key_identifiers = [
		],
	),
	include_targets = [
		AuthenticationMethodTarget(
			target_type = AuthenticationMethodTargetType.Group,
			id = "all_users",
			is_registration_required = False,
		),
	],
)

result = await graph_client.policies.authentication_methods_policy.authentication_method_configurations.by_authentication_method_configuration_id('authenticationMethodConfiguration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
