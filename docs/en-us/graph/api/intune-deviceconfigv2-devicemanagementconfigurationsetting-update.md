<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsetting-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update deviceManagementConfigurationSetting

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/auditPolicies/{deviceManagementAuditPolicyId}/settings/{deviceManagementConfigurationSettingId}
PATCH /deviceManagement/inventoryPolicies/{deviceManagementInventoryPolicyId}/settings/{deviceManagementConfigurationSettingId}
PATCH /deviceManagement/compliancePolicies/{deviceManagementCompliancePolicyId}/settings/{deviceManagementConfigurationSettingId}
PATCH /deviceManagement/configurationPolicies/{deviceManagementConfigurationPolicyId}/settings/{deviceManagementConfigurationSettingId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of this setting within the policy which contains it. Automatically generated. |
| settingInstance | [deviceManagementConfigurationSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinginstance?view=graph-rest-beta) | Setting Instance |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/auditPolicies/{deviceManagementAuditPolicyId}/settings/{deviceManagementConfigurationSettingId}
Content-type: application/json
Content-length: 26306

{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSetting",
  "settingInstance": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
    "settingDefinitionId": "Setting Definition Id value",
    "settingInstanceTemplateReference": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
      "settingInstanceTemplateId": "Setting Instance Template Id value"
    },
    "auditRuleInformation": {
      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
      "auditType": "registry",
      "auditRuleMetadata": {
        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
        "metadataType": "stig",
        "ruleId": "Rule Id value",
        "ruleName": "Rule Name value",
        "ruleDescription": "Rule Description value",
        "ruleVersion": "Rule Version value",
        "ruleSeverity": "Rule Severity value"
      }
    },
    "choiceSettingValue": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
      "settingValueTemplateReference": {
        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
        "settingValueTemplateId": "Setting Value Template Id value",
        "useTemplateDefault": true
      },
      "value": "Value value",
      "children": [
        {
          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
          "settingDefinitionId": "Setting Definition Id value",
          "settingInstanceTemplateReference": {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
            "settingInstanceTemplateId": "Setting Instance Template Id value"
          },
          "auditRuleInformation": {
            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
            "auditType": "registry",
            "auditRuleMetadata": {
              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
              "metadataType": "stig",
              "ruleId": "Rule Id value",
              "ruleName": "Rule Name value",
              "ruleDescription": "Rule Description value",
              "ruleVersion": "Rule Version value",
              "ruleSeverity": "Rule Severity value"
            }
          },
          "choiceSettingValue": {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
            "settingValueTemplateReference": {
              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
              "settingValueTemplateId": "Setting Value Template Id value",
              "useTemplateDefault": true
            },
            "value": "Value value",
            "children": [
              {
                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                "settingDefinitionId": "Setting Definition Id value",
                "settingInstanceTemplateReference": {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                  "settingInstanceTemplateId": "Setting Instance Template Id value"
                },
                "auditRuleInformation": {
                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                  "auditType": "registry",
                  "auditRuleMetadata": {
                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                    "metadataType": "stig",
                    "ruleId": "Rule Id value",
                    "ruleName": "Rule Name value",
                    "ruleDescription": "Rule Description value",
                    "ruleVersion": "Rule Version value",
                    "ruleSeverity": "Rule Severity value"
                  }
                },
                "choiceSettingValue": {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                  "settingValueTemplateReference": {
                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                    "settingValueTemplateId": "Setting Value Template Id value",
                    "useTemplateDefault": true
                  },
                  "value": "Value value",
                  "children": [
                    {
                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                      "settingDefinitionId": "Setting Definition Id value",
                      "settingInstanceTemplateReference": {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                        "settingInstanceTemplateId": "Setting Instance Template Id value"
                      },
                      "auditRuleInformation": {
                        "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                        "auditType": "registry",
                        "auditRuleMetadata": {
                          "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                          "metadataType": "stig",
                          "ruleId": "Rule Id value",
                          "ruleName": "Rule Name value",
                          "ruleDescription": "Rule Description value",
                          "ruleVersion": "Rule Version value",
                          "ruleSeverity": "Rule Severity value"
                        }
                      },
                      "choiceSettingValue": {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                        "settingValueTemplateReference": {
                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                          "settingValueTemplateId": "Setting Value Template Id value",
                          "useTemplateDefault": true
                        },
                        "value": "Value value",
                        "children": [
                          {
                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                            "settingDefinitionId": "Setting Definition Id value",
                            "settingInstanceTemplateReference": {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                              "settingInstanceTemplateId": "Setting Instance Template Id value"
                            },
                            "auditRuleInformation": {
                              "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                              "auditType": "registry",
                              "auditRuleMetadata": {
                                "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                "metadataType": "stig",
                                "ruleId": "Rule Id value",
                                "ruleName": "Rule Name value",
                                "ruleDescription": "Rule Description value",
                                "ruleVersion": "Rule Version value",
                                "ruleSeverity": "Rule Severity value"
                              }
                            },
                            "choiceSettingValue": {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                              "settingValueTemplateReference": {
                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                "settingValueTemplateId": "Setting Value Template Id value",
                                "useTemplateDefault": true
                              },
                              "value": "Value value",
                              "children": [
                                {
                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                  "settingDefinitionId": "Setting Definition Id value",
                                  "settingInstanceTemplateReference": {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                    "settingInstanceTemplateId": "Setting Instance Template Id value"
                                  },
                                  "auditRuleInformation": {
                                    "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                    "auditType": "registry",
                                    "auditRuleMetadata": {
                                      "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                      "metadataType": "stig",
                                      "ruleId": "Rule Id value",
                                      "ruleName": "Rule Name value",
                                      "ruleDescription": "Rule Description value",
                                      "ruleVersion": "Rule Version value",
                                      "ruleSeverity": "Rule Severity value"
                                    }
                                  },
                                  "choiceSettingValue": {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                    "settingValueTemplateReference": {
                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                      "settingValueTemplateId": "Setting Value Template Id value",
                                      "useTemplateDefault": true
                                    },
                                    "value": "Value value",
                                    "children": [
                                      {
                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                        "settingDefinitionId": "Setting Definition Id value",
                                        "settingInstanceTemplateReference": {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                          "settingInstanceTemplateId": "Setting Instance Template Id value"
                                        },
                                        "auditRuleInformation": {
                                          "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                          "auditType": "registry",
                                          "auditRuleMetadata": {
                                            "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                            "metadataType": "stig",
                                            "ruleId": "Rule Id value",
                                            "ruleName": "Rule Name value",
                                            "ruleDescription": "Rule Description value",
                                            "ruleVersion": "Rule Version value",
                                            "ruleSeverity": "Rule Severity value"
                                          }
                                        },
                                        "choiceSettingValue": {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                          "settingValueTemplateReference": {
                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                            "settingValueTemplateId": "Setting Value Template Id value",
                                            "useTemplateDefault": true
                                          },
                                          "value": "Value value",
                                          "children": [
                                            {
                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                              "settingDefinitionId": "Setting Definition Id value",
                                              "settingInstanceTemplateReference": {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                "settingInstanceTemplateId": "Setting Instance Template Id value"
                                              },
                                              "auditRuleInformation": {
                                                "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                "auditType": "registry",
                                                "auditRuleMetadata": {
                                                  "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                  "metadataType": "stig",
                                                  "ruleId": "Rule Id value",
                                                  "ruleName": "Rule Name value",
                                                  "ruleDescription": "Rule Description value",
                                                  "ruleVersion": "Rule Version value",
                                                  "ruleSeverity": "Rule Severity value"
                                                }
                                              },
                                              "choiceSettingValue": {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                "settingValueTemplateReference": {
                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                  "settingValueTemplateId": "Setting Value Template Id value",
                                                  "useTemplateDefault": true
                                                },
                                                "value": "Value value",
                                                "children": [
                                                  {
                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                    "settingDefinitionId": "Setting Definition Id value",
                                                    "settingInstanceTemplateReference": {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                      "settingInstanceTemplateId": "Setting Instance Template Id value"
                                                    },
                                                    "auditRuleInformation": {
                                                      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                      "auditType": "registry",
                                                      "auditRuleMetadata": {
                                                        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                        "metadataType": "stig",
                                                        "ruleId": "Rule Id value",
                                                        "ruleName": "Rule Name value",
                                                        "ruleDescription": "Rule Description value",
                                                        "ruleVersion": "Rule Version value",
                                                        "ruleSeverity": "Rule Severity value"
                                                      }
                                                    },
                                                    "choiceSettingValue": {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                      "settingValueTemplateReference": {
                                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                        "settingValueTemplateId": "Setting Value Template Id value",
                                                        "useTemplateDefault": true
                                                      },
                                                      "value": "Value value",
                                                      "children": [
                                                        {
                                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                          "settingDefinitionId": "Setting Definition Id value",
                                                          "settingInstanceTemplateReference": {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                            "settingInstanceTemplateId": "Setting Instance Template Id value"
                                                          },
                                                          "auditRuleInformation": {
                                                            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                            "auditType": "registry",
                                                            "auditRuleMetadata": {
                                                              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                              "metadataType": "stig",
                                                              "ruleId": "Rule Id value",
                                                              "ruleName": "Rule Name value",
                                                              "ruleDescription": "Rule Description value",
                                                              "ruleVersion": "Rule Version value",
                                                              "ruleSeverity": "Rule Severity value"
                                                            }
                                                          },
                                                          "choiceSettingValue": {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                            "settingValueTemplateReference": {
                                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                              "settingValueTemplateId": "Setting Value Template Id value",
                                                              "useTemplateDefault": true
                                                            },
                                                            "value": "Value value",
                                                            "children": [
                                                              {
                                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                "settingDefinitionId": "Setting Definition Id value",
                                                                "settingInstanceTemplateReference": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                                  "settingInstanceTemplateId": "Setting Instance Template Id value"
                                                                },
                                                                "auditRuleInformation": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                                  "auditType": "registry",
                                                                  "auditRuleMetadata": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                                    "metadataType": "stig",
                                                                    "ruleId": "Rule Id value",
                                                                    "ruleName": "Rule Name value",
                                                                    "ruleDescription": "Rule Description value",
                                                                    "ruleVersion": "Rule Version value",
                                                                    "ruleSeverity": "Rule Severity value"
                                                                  }
                                                                },
                                                                "choiceSettingValue": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                                  "settingValueTemplateReference": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                                    "settingValueTemplateId": "Setting Value Template Id value",
                                                                    "useTemplateDefault": true
                                                                  },
                                                                  "value": "Value value",
                                                                  "children": [
                                                                    {
                                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                      "settingDefinitionId": null,
                                                                      "settingInstanceTemplateReference": null,
                                                                      "auditRuleInformation": null,
                                                                      "choiceSettingValue": null
                                                                    }
                                                                  ]
                                                                }
                                                              }
                                                            ]
                                                          }
                                                        }
                                                      ]
                                                    }
                                                  }
                                                ]
                                              }
                                            }
                                          ]
                                        }
                                      }
                                    ]
                                  }
                                }
                              ]
                            }
                          }
                        ]
                      }
                    }
                  ]
                }
              }
            ]
          }
        }
      ]
    }
  }
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 26355

{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSetting",
  "id": "9acf977e-977e-9acf-7e97-cf9a7e97cf9a",
  "settingInstance": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
    "settingDefinitionId": "Setting Definition Id value",
    "settingInstanceTemplateReference": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
      "settingInstanceTemplateId": "Setting Instance Template Id value"
    },
    "auditRuleInformation": {
      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
      "auditType": "registry",
      "auditRuleMetadata": {
        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
        "metadataType": "stig",
        "ruleId": "Rule Id value",
        "ruleName": "Rule Name value",
        "ruleDescription": "Rule Description value",
        "ruleVersion": "Rule Version value",
        "ruleSeverity": "Rule Severity value"
      }
    },
    "choiceSettingValue": {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
      "settingValueTemplateReference": {
        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
        "settingValueTemplateId": "Setting Value Template Id value",
        "useTemplateDefault": true
      },
      "value": "Value value",
      "children": [
        {
          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
          "settingDefinitionId": "Setting Definition Id value",
          "settingInstanceTemplateReference": {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
            "settingInstanceTemplateId": "Setting Instance Template Id value"
          },
          "auditRuleInformation": {
            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
            "auditType": "registry",
            "auditRuleMetadata": {
              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
              "metadataType": "stig",
              "ruleId": "Rule Id value",
              "ruleName": "Rule Name value",
              "ruleDescription": "Rule Description value",
              "ruleVersion": "Rule Version value",
              "ruleSeverity": "Rule Severity value"
            }
          },
          "choiceSettingValue": {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
            "settingValueTemplateReference": {
              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
              "settingValueTemplateId": "Setting Value Template Id value",
              "useTemplateDefault": true
            },
            "value": "Value value",
            "children": [
              {
                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                "settingDefinitionId": "Setting Definition Id value",
                "settingInstanceTemplateReference": {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                  "settingInstanceTemplateId": "Setting Instance Template Id value"
                },
                "auditRuleInformation": {
                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                  "auditType": "registry",
                  "auditRuleMetadata": {
                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                    "metadataType": "stig",
                    "ruleId": "Rule Id value",
                    "ruleName": "Rule Name value",
                    "ruleDescription": "Rule Description value",
                    "ruleVersion": "Rule Version value",
                    "ruleSeverity": "Rule Severity value"
                  }
                },
                "choiceSettingValue": {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                  "settingValueTemplateReference": {
                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                    "settingValueTemplateId": "Setting Value Template Id value",
                    "useTemplateDefault": true
                  },
                  "value": "Value value",
                  "children": [
                    {
                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                      "settingDefinitionId": "Setting Definition Id value",
                      "settingInstanceTemplateReference": {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                        "settingInstanceTemplateId": "Setting Instance Template Id value"
                      },
                      "auditRuleInformation": {
                        "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                        "auditType": "registry",
                        "auditRuleMetadata": {
                          "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                          "metadataType": "stig",
                          "ruleId": "Rule Id value",
                          "ruleName": "Rule Name value",
                          "ruleDescription": "Rule Description value",
                          "ruleVersion": "Rule Version value",
                          "ruleSeverity": "Rule Severity value"
                        }
                      },
                      "choiceSettingValue": {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                        "settingValueTemplateReference": {
                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                          "settingValueTemplateId": "Setting Value Template Id value",
                          "useTemplateDefault": true
                        },
                        "value": "Value value",
                        "children": [
                          {
                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                            "settingDefinitionId": "Setting Definition Id value",
                            "settingInstanceTemplateReference": {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                              "settingInstanceTemplateId": "Setting Instance Template Id value"
                            },
                            "auditRuleInformation": {
                              "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                              "auditType": "registry",
                              "auditRuleMetadata": {
                                "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                "metadataType": "stig",
                                "ruleId": "Rule Id value",
                                "ruleName": "Rule Name value",
                                "ruleDescription": "Rule Description value",
                                "ruleVersion": "Rule Version value",
                                "ruleSeverity": "Rule Severity value"
                              }
                            },
                            "choiceSettingValue": {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                              "settingValueTemplateReference": {
                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                "settingValueTemplateId": "Setting Value Template Id value",
                                "useTemplateDefault": true
                              },
                              "value": "Value value",
                              "children": [
                                {
                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                  "settingDefinitionId": "Setting Definition Id value",
                                  "settingInstanceTemplateReference": {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                    "settingInstanceTemplateId": "Setting Instance Template Id value"
                                  },
                                  "auditRuleInformation": {
                                    "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                    "auditType": "registry",
                                    "auditRuleMetadata": {
                                      "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                      "metadataType": "stig",
                                      "ruleId": "Rule Id value",
                                      "ruleName": "Rule Name value",
                                      "ruleDescription": "Rule Description value",
                                      "ruleVersion": "Rule Version value",
                                      "ruleSeverity": "Rule Severity value"
                                    }
                                  },
                                  "choiceSettingValue": {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                    "settingValueTemplateReference": {
                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                      "settingValueTemplateId": "Setting Value Template Id value",
                                      "useTemplateDefault": true
                                    },
                                    "value": "Value value",
                                    "children": [
                                      {
                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                        "settingDefinitionId": "Setting Definition Id value",
                                        "settingInstanceTemplateReference": {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                          "settingInstanceTemplateId": "Setting Instance Template Id value"
                                        },
                                        "auditRuleInformation": {
                                          "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                          "auditType": "registry",
                                          "auditRuleMetadata": {
                                            "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                            "metadataType": "stig",
                                            "ruleId": "Rule Id value",
                                            "ruleName": "Rule Name value",
                                            "ruleDescription": "Rule Description value",
                                            "ruleVersion": "Rule Version value",
                                            "ruleSeverity": "Rule Severity value"
                                          }
                                        },
                                        "choiceSettingValue": {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                          "settingValueTemplateReference": {
                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                            "settingValueTemplateId": "Setting Value Template Id value",
                                            "useTemplateDefault": true
                                          },
                                          "value": "Value value",
                                          "children": [
                                            {
                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                              "settingDefinitionId": "Setting Definition Id value",
                                              "settingInstanceTemplateReference": {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                "settingInstanceTemplateId": "Setting Instance Template Id value"
                                              },
                                              "auditRuleInformation": {
                                                "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                "auditType": "registry",
                                                "auditRuleMetadata": {
                                                  "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                  "metadataType": "stig",
                                                  "ruleId": "Rule Id value",
                                                  "ruleName": "Rule Name value",
                                                  "ruleDescription": "Rule Description value",
                                                  "ruleVersion": "Rule Version value",
                                                  "ruleSeverity": "Rule Severity value"
                                                }
                                              },
                                              "choiceSettingValue": {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                "settingValueTemplateReference": {
                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                  "settingValueTemplateId": "Setting Value Template Id value",
                                                  "useTemplateDefault": true
                                                },
                                                "value": "Value value",
                                                "children": [
                                                  {
                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                    "settingDefinitionId": "Setting Definition Id value",
                                                    "settingInstanceTemplateReference": {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                      "settingInstanceTemplateId": "Setting Instance Template Id value"
                                                    },
                                                    "auditRuleInformation": {
                                                      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                      "auditType": "registry",
                                                      "auditRuleMetadata": {
                                                        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                        "metadataType": "stig",
                                                        "ruleId": "Rule Id value",
                                                        "ruleName": "Rule Name value",
                                                        "ruleDescription": "Rule Description value",
                                                        "ruleVersion": "Rule Version value",
                                                        "ruleSeverity": "Rule Severity value"
                                                      }
                                                    },
                                                    "choiceSettingValue": {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                      "settingValueTemplateReference": {
                                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                        "settingValueTemplateId": "Setting Value Template Id value",
                                                        "useTemplateDefault": true
                                                      },
                                                      "value": "Value value",
                                                      "children": [
                                                        {
                                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                          "settingDefinitionId": "Setting Definition Id value",
                                                          "settingInstanceTemplateReference": {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                            "settingInstanceTemplateId": "Setting Instance Template Id value"
                                                          },
                                                          "auditRuleInformation": {
                                                            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                            "auditType": "registry",
                                                            "auditRuleMetadata": {
                                                              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                              "metadataType": "stig",
                                                              "ruleId": "Rule Id value",
                                                              "ruleName": "Rule Name value",
                                                              "ruleDescription": "Rule Description value",
                                                              "ruleVersion": "Rule Version value",
                                                              "ruleSeverity": "Rule Severity value"
                                                            }
                                                          },
                                                          "choiceSettingValue": {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                            "settingValueTemplateReference": {
                                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                              "settingValueTemplateId": "Setting Value Template Id value",
                                                              "useTemplateDefault": true
                                                            },
                                                            "value": "Value value",
                                                            "children": [
                                                              {
                                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                "settingDefinitionId": "Setting Definition Id value",
                                                                "settingInstanceTemplateReference": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                                  "settingInstanceTemplateId": "Setting Instance Template Id value"
                                                                },
                                                                "auditRuleInformation": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                                  "auditType": "registry",
                                                                  "auditRuleMetadata": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                                    "metadataType": "stig",
                                                                    "ruleId": "Rule Id value",
                                                                    "ruleName": "Rule Name value",
                                                                    "ruleDescription": "Rule Description value",
                                                                    "ruleVersion": "Rule Version value",
                                                                    "ruleSeverity": "Rule Severity value"
                                                                  }
                                                                },
                                                                "choiceSettingValue": {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                                  "settingValueTemplateReference": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                                    "settingValueTemplateId": "Setting Value Template Id value",
                                                                    "useTemplateDefault": true
                                                                  },
                                                                  "value": "Value value",
                                                                  "children": [
                                                                    {
                                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                      "settingDefinitionId": null,
                                                                      "settingInstanceTemplateReference": null,
                                                                      "auditRuleInformation": null,
                                                                      "choiceSettingValue": null
                                                                    }
                                                                  ]
                                                                }
                                                              }
                                                            ]
                                                          }
                                                        }
                                                      ]
                                                    }
                                                  }
                                                ]
                                              }
                                            }
                                          ]
                                        }
                                      }
                                    ]
                                  }
                                }
                              ]
                            }
                          }
                        ]
                      }
                    }
                  ]
                }
              }
            ]
          }
        }
      ]
    }
  }
}
```
