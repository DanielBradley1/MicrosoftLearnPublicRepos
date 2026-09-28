<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/sap-employee-read-write-scenarios -->
<!-- Sitemap-Last-Modified: 2025-12-17 -->

# SAP SuccessFactors employee read and write scenarios

## SAP SuccessFactors employee read scenarios

Each of the Read topic has its own prompts, configurations, and so on, but the actual execution of SAP SuccessFactors is encapsulated in the **SuccessFactors System Get Common Execution** topic expecting the following inputs:

- **Filter parameters**: Generally passing *Employee ID* and *User ID* for filtering query for Employee Read topics.
- **ScenarioName**: Config Name, which is used by Dataverse call to get scenario configuration.
- **userIdentifier**: User ID.

A common orchestrator then returns a ModelResponse and LabelResponse, which the Large Language Model \(LLM\) then parses using the following instructions to generate an answer for the user:

- Extract the input from the following response \(map the Label response *value* as key in model response attribute then provide model value\).
- Provide the response to the user in a human readable form.
- Format the response properly to make it clean and readable.
- Use only data values from the variable named `successfactorsModelResponse` and use the variable named `successfactorsLabelResponse` for labeling the data.
- **Response example:**

  - Label Response:`key`:`company`,`value`:`company`
  - Model Response: `company`:`12345`
  - Example Output: Your company is 12345 \(Contoso Germany\)

The "Get Employee ID" and "Get Service Anniversary" topics are exceptions to this common execution method, which is further explained in their respective sections.

Authorization for all the topics is as follows:

- Authorization is done using the *permissionsMetadata* part of the starter configuration. The *permissionsMetadata* and *User ID* are used to create the query string for OData connector in *SuccessFactors Check User Permissions* flow.
- You should include *permissionMetadata* or *rolePermission* in the starter config file, as there's no other authorization check if both of those fields are missing.

### Get Base Compensation

| Get Base Compensation | Details |
| --- | --- |
| **Description** | Returns the users' compensation data, such as compensation ratio and salary. |
| **Prompts** | <li>&gt;How much can I expect to earn annually, what is my salary? </li><br><br><li>Show me only my base salary details</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetBaseCompensationAndCompaRatio`. |
| **Filter** | Filters on *personIdExternal* using *ESS \_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'"`. |
| **Values queried** | CompaRatio  <br>Currency  <br>AnnualBaseSalary. |

**Configuration:**

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetBaseCompensationAndCompaRatio", 
    "rootEntity": "EmpEmployment", 
    "filter": "personIdExternal eq '{personIdExternalVal}' and userId eq 
'{userIdVal}'", 
    "requestEntities": [ 
        { 
            "key": "CompaRatio", 
            "valuePath": "compInfoNav/empCompensationCalculatedNav/compaRatio", 
            "labelPath": "EmpCompensationCalculated/compaRatio" 
        }, 
        { 
            "key": "Currency", 
            "valuePath": "compInfoNav/empCompensationCalculatedNav/currency", 
            "labelPath": "EmpCompensationCalculated/currency" 
        }, 
        { 
            "key": "AnnualBaseSalary", 
            "valuePath": 
"compInfoNav/empCompensationCalculatedNav/yearlyBaseSalary", 
            "labelPath": "EmpCompensationCalculated/yearlyBaseSalary" 
        } 
    ], 
    "permissionsMetadata": [ 
        { 
            "permType": "DATA_MODEL", 
            "permLongValue": -1, 
            "permStringValue": "$_payCompGroup_AnnualizedSalary_read" 
        } 
    ] 
} 
```

### Get Company Code

| Get Company Code | Details |
| --- | --- |
| **Description** | Returns users' company code information. |
| **Prompts** | <li>What is my company code? </li><br><br><li> Get employee view on company code. </li><br><br><li>Display my company code </li><br><br><li>Give me my company code, what is my company code? </li><br><br><li>Show me only my company code details.</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetCompanyCode`. |
| **Filter** | Filters on *personIdExternal* using *ESS\_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq'{userIdVal}'"`. |
| **Values queried** | CompanyCode.  <br>CompanyName \(*No label is retrieved for company name as it is*\). |

**Configuration**:

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetCompanyCode", 
"rootEntity": "EmpEmployment", 
"filter": "personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'", 
"requestEntities": [ 
{ 
"key": "CompanyCode", 
"valuePath": "jobInfoNav/company", 
"labelPath": "EmpJob/company" 
}, 
{ 
"key": "CompanyName", 
"valuePath": "jobInfoNav/companyNav/name", 
"labelPath": "" 
} 
], 
"permissionsMetadata": [ 
{ 
"permType": "DATA_MODEL", 
"permLongValue": -1, 
"permStringValue": "$_jobInfo_company_read" 
} 
] 
} 
```

### Get Cost Center

| Get Cost Center | Details |
| --- | --- |
| **Description** | Returns users' current cost center. |
| **Prompts** | <li>What is my Cost Center?</li><br><br><li>Can you show me the cost center I&#39;m assigned to?</li><br><br><li>Can you show me my cost center?</li><br><br><li>Show me only my cost center details.</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetCostCenter`. |
| **Filter** | Filters on *personIdExternal* using *ESS\_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'"`. |
| **Values queried** | CostCenterCode.  <br>CostCenterName \(*CostCenterName label isn't retrieved as it isn't necessary for topic*\). |

**Configuration**:

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetCostCenter", 
"rootEntity": "EmpEmployment", 
"filter": "personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'", 
"requestEntities": [ 
{ 
"key": "CostCenterCode", 
"valuePath": "jobInfoNav/costCenter", 
"labelPath": "EmpJob/costCenter" 
}, 
{ 
"key": "CostCenterName", 
"valuePath": "jobInfoNav/costCenterNav/name", 
"labelPath": "" 
} 
], 
"permissionsMetadata": [ 
{ 
"permType": "DATA_MODEL", 
"permLongValue": -1, 
"permStringValue": "$_jobInfo_cost-center_read" 
} 
] 
} 
```

### Get Hire Date

| Get Hire Data | Details |
| --- | --- |
| **Description** | Returns the users' hire date. |
| **Prompts** | <li>When is my original start date? </li><br><br><li>Get my hire date. </li><br><br><li>Get my start date. </li><br><br><li>Show me only my hire date details.</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetHireDate`. |
| **Filter** | Filters on *personIdExternal* using *ESS\_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq'{userIdVal}'"`. |
| **Values queried** | HireDate. |

**Configuration**:

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetHireDate", 
"rootEntity": "EmpEmployment", 
"filter": "personIdExternal eq '{personIdExternalVal}' and userId eq 
'{userIdVal}'", 
"requestEntities": [ 
{ 
"key": "HireDate", 
"valuePath": "originalStartDate", 
"labelPath": "EmpEmployment/originalStartDate" 
} 
], 
"permissionsMetadata": [ 
{ 
"permType": "DATA_MODEL", 
"permLongValue": -1, 
"permStringValue": "$_employmentInfo_seniorityDate_read" 
} 
] 
} 
```

### Get Service Anniversary

| Get Service Anniversary | Details |
| --- | --- |
| **Description** | This topic performs a calculated functionality using the "HireDate" value with some PowerFx functions as follows:<br><br>**Years worked**<br><br><li><code>RoundDown(DateDiff(Topic.startDate, Now(), TimeUnit.Years), 0)</code> <br>This formula calculates the number of complete years the employee worked. It finds the difference between current date and employee&#39;s start date and then rounds down to the nearest whole number</li><br><br><li><code>DateDiff(Topic.startDate, Now(), TimeUnit.Years)</code> <br>This part of the formula calculates the difference in years between the employee&#39;s start date (<code>Topic.startDate</code>) and the current date (`Now()`).</li><br><br><li><code>RoundDown(..., 0)</code> <br>This function takes the result of DateDiff and rounds it down to the nearest whole number. The <code>0</code> value indicates the number of decimal places to round to, which in this case is zero, meaning it returns an integer value representing the complete years worked. <p><strong>Service Anniversary Intervals in Years</strong> </p><p></p></li><br><br><li><code>RoundDown(Topic.yearsWorked / Topic.serviceAnniversaryDuration, 0)</code> <br>Calculates how many complete intervals of the service anniversary duration the employee worked. It divides the total years worked by the service anniversary duration and rounds down to the nearest whole number. <p><strong>Upcoming Service Anniversary Count</strong> </p></li><br><br><li><code>Topic.serviceAnniversaryDuration \* (Topic.serviceAnniversaryIntervalsInYears + 1)</code> <br>This formula calculates the upcoming service anniversary count by multiplying the service anniversary duration by one more than the complete intervals already worked.<p><strong>Calculated Service Anniversary Date</strong> <br><code>DateAdd(Topic.startDate, Topic.serviceAnniversaryDuration \*(RoundDown(Topic.yearsWorked / Topic.serviceAnniversaryDuration, 0) + 1), TimeUnit.Years)</code></p><p></p></li><br><br><li><code>RoundDown(Topic.yearsWorked / Topic.serviceAnniversaryDuration, 0)</code> <br>This part of the formula calculates how many complete intervals of the service anniversary duration the employee worked. It divides the total years worked by the service anniversary duration and rounding down to the nearest whole number.</li><br><br><li><code>Topic.serviceAnniversaryDuration \* (RoundDown(Topic.yearsWorked /Topic.serviceAnniversaryDuration, 0) + 1)</code> <br>This part of the formula calculates the total service anniversary intervals (plus one) to be added to the start date.</li><br><br><li><code>DateAdd(Topic.startDate, ..., TimeUnit.Years)</code><br>Finally, this function adds the calculated intervals to the start date to determine the upcoming service anniversary date.</li> |
| **Prompts** | <li>When is my next service anniversary?</li><br><br><li>Next anniversary</li><br><br><li>Service anniversary</li><br><br><li>Show my service anniversary date </li><br><br><li>What is my service anniversary date?</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetHireDate` |
| **Filter** | Filters on *personIdExternal* using *ESS\_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'"` |
| **Values queried** | HireDate |

**Configuration**:

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetHireDate", 
"rootEntity": "EmpEmployment", 
"filter": "personIdExternal eq '{personIdExternalVal}' and userId eq 
'{userIdVal}'", 
"requestEntities": [ 
{ 
"key": "HireDate", 
"valuePath": "originalStartDate", 
"labelPath": "EmpEmployment/originalStartDate" 
} 
], 
"permissionsMetadata": [ 
{ 
"permType": "DATA_MODEL", 
"permLongValue": -1, 
"permStringValue": "$_employmentInfo_seniorityDate_read" 
} 
] 
} 
```

### Get Employee ID

| Get Employee ID | Details |
| --- | --- |
| **Description** | Reads *ESS\_UserContext\_Employee\_Id* and returns it to the user. There's no config required for this topic. |
| **Prompts** | <li>What is my employee ID?</li><br><br><li>Show my employee ID?</li><br><br><li>What is my employee number?</li> |

### Get Job Info

| Get Job Info | Details |
| --- | --- |
| **Description** | Returns job information to the user, including Job Code, Job Title, Job Function, and Job Function Type. |
| **Prompts** | <li>What is my job code? </li><br><br><li>What is a job code? </li><br><br><li>What is my role? </li><br><br><li>What is my job info? </li><br><br><li>What is my job title? </li><br><br><li>Show me only my job details.</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetJobInfo`. |
| **Filter** | Filters on *personIdExternal* using *ESS\_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'"`. |
| **Values queried** | JobCode  <br>JobTitle  <br>JobFunction  <br>JobFunctionType. |

**Configuration**:

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetJobInfo", 
"rootEntity": "EmpEmployment", 
"filter": "personIdExternal eq '{personIdExternalVal}' and userId eq 
'{userIdVal}'", 
"requestEntities": [ 
        { 
            "key": "JobCode", 
            "valuePath": "jobInfoNav/jobCodeNav/name", 
            "labelPath": "EmpJob/jobCode" 
        }, 
        { 
            "key": "JobTitle", 
            "valuePath": "jobInfoNav/jobTitle", 
            "labelPath": "EmpJob/jobTitle" 
        }, 
        { 
            "key": "JobFunction", 
            "valuePath": "jobInfoNav/jobCodeNav/jobFunction", 
            "labelPath": "FOJobCode/jobFunction" 
        }, 
        { 
            "key": "JobFunctionType", 
            "valuePath": "jobInfoNav/jobCodeNav/jobFunctionNav/jobFunctionType", 
            "labelPath": "FOJobFunction/jobFunctionType" 
        } 
    ], 
    "permissionsMetadata": [ 
        { 
            "permType": "DATA_MODEL", 
            "permLongValue": -1, 
            "permStringValue": "$_jobInfo_job-code_read" 
        } 
    ] 
} 
```

### Get Position Number

| Get Position Number | Details |
| --- | --- |
| **Description** | Returns position number acquired from SuccessFactors. |
| **Prompts** | <li>What is my position ID? </li><br><br><li> Get my position number. </li><br><br><li> Show me only my position details.</li> |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetPositionNumber`. |
| **Filter** | Filters on *personIdExternal* using *ESS\_UserContext\_Employee\_Id* and *user ID* using *ESS\_UserContext\_User\_Id*<br><br>Expression: `"personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'"`. |
| **Values queried** | JobCode. |

**Configuration**:

```json
{ 
    "scenario": "HRSAPSuccessFactorsHCMEmployeeGetPositionNumber", 
"rootEntity": "EmpEmployment", 
"filter": "personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}' 
and tolower(jobInfoNav/positionNav/effectiveStatus) eq 'a'", 
"requestEntities": [ 
{ 
"key": "JobCode", 
"valuePath": "jobInfoNav/position", 
"labelPath": "EmpJob/position" 
} 
], 
"permissionsMetadata": [ 
{ 
"permType": "DATA_MODEL", 
"permLongValue": -1, 
"permStringValue": "$_jobInfo_position_read" 
} 
] 
} 
```

## SAP SuccessFactors employee write scenarios

Employee **write** topics logic is as follows:

### 1. Get user data

Get user data and Picklist data \(if necessary\) by using `SuccessFactors System Get Common Execution`, which expects the following inputs:

**FilterParams**: The following example shows a user data request, but picklist data request follow the same rules for prepping the filterParams.

Example format used in Topic:

```json
"{""personIdExternalVal"": """ & Global.ESS_UserContext_Employee_Id & """,""userIdVal"": """ & Global.ESS_UserContext_User_Id & """}" 
```

Snippet of Template configuration:

```json
{ 
  ... 
  "filter": "personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'", 
  ... 
} 
```

The keys present in the `filterParam` must match what is expected in the Template configuration. In the examples above `personIdExternalVal` would be used as a key to insert `Global.ESS_UserContext_Employee_Id` into the filter expression.

**ScenarioName**: Configuration name, which is used by the Dataverse call to get scenario configuration **userIdentifier**: `User Id`

`SuccessFactors System Get Common Execution` then returns a `ModelResponse` and `LabelResponse`, which are parsed for the user's data, and then stored in variables.

### 2. Confirm information

Present the user their current information asking for their confirmation to update or cancel to trigger the respective flow using either inline messaging or with an adaptive card.

### 3. Submit update

If the user submits their update, then data is collected and used to call the `SuccessFactors System Update Common Execution`. This flow will `UPSERT` user data in SuccessFactors using the **OData** connector. `SuccessFactors System Update Common Execution` requires the following inputs:

- `TargetUserId`: User ID
- `var_requestParam`: An array of objects

Example Format used in Topic:

```json
"[{""key"":""personIdExternalVal"", ""value"":"""&Global.ESS_UserContext_Employee_Id&"""},         {""key"":""countryVal"", ""value"":"""&First(Topic.var_parsedModel).country&"""},{""key"":""startDateVal"", ""value"":"""&DateDiff(Date(1970, 1, 1), First(Topic.var_parsedModel).startDate, TimeUnit.Seconds) * 1000&"""},{""key"":""genericString1Val"", ""value"":"""&Topic.id_raceAndEthnicity&"""}]" 
```

Snippet from Template configuration

```json
{ 
    "__metadata": { 
        "uri": "PerGlobalInfoUSA" 
    },   
    "personIdExternal": "personIdExternalVal", 
    "country": "countryVal", 
    "startDate": "/Date(startDateVal)/", 
    "genericString1": "genericString1Val", 
 } 
```

The keys present in the `var_requestParam` must match what is expected in the Template configuration. In the previous examples `personIdExternalVal` would be used as a key to insert `Global.ESS_UserContext_Employee_Id` into the request body.

- `var_scenarioName`: Configuration name, which is used by Dataverse call to get scenario configuration.

### 4. Success or fail notification to user

If `SuccessFactors System Update Common Execution` succeeds, then Copilot responds to a user that their update succeeded. If the operation fails, the user gets a failure message.

### Multi-country/region configurations

To accommodate support for multiple country/regions and their respective entities, distinct configurations are established tailored to each scenario. These configurations adhere to the established naming convention, with the addition of `_<CountryCode>` appended at the end. This differentiation serves not only to distinguish between configurations but also to ensure retrieval of the appropriate configuration from the topics. Within the topic, the correct configuration is identified by appending `UserContext_Country_Code` to the standard configuration name.

For example: `Concatenate("msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateRaceAndEthnicity_", Global.ESS_UserContext_Country_Code)`

For all Write configurations, ensure that `requestBody` is a string by including single quotes outside the brackets. This is the expected data type for query flow.

### Customizations

Customizations to the Template configuration will generally require these changes:

#### 1. Adding fields to Get Config:

[![Screenshot of the parse value field with var\_veteranInfo.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-parse-value.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-parse-value.png#lightbox)

[![Screenshot of the Edit schema window that's highlighted NewField value.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-edit-schema.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-edit-schema.png#lightbox)

#### 2. Adding fields to Adaptive card:

After adding fields to get schema, they can be accessed in the adaptive card design formula:

[![Screenshot of the adaptive card fields.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-adaptive-cards-fields.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-adaptive-cards-fields.png#lightbox)

The adaptive card `label` property is set by the value stored in the pared `label` variable and the `value` property is set using the `var_veteranInfo` variable, which stores the parsed user data.

If another input type needs to be added to the adaptive card to collect data for another field, then use the following input control code:

```json
{
type: "Input.ChoiceSet",
placeholder: "No Selection",
id: "id_veteran",
label: Lookup(Topic.var_parsedLabel, key="genericNumber1").value,
value: First(Topic.var_veteranInfo).genericNumber1,
choices: Topic.var_veteranPicklist
}
```

After updating the code, you must update the output binding schema with the string given in `id` property. In the previous example, `id` = `id_veteran`. Therefore, the output binding schema must have a variable with the same name set with the correct data type. For example:

```
kind: Record
properties:
  actionSubmitId: String
  id_challenged_veteran: String
  id_special_disabled_veteran: String
  id_veteran: String
```

[![Screenshot of the employee output binding schema window.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-edit-output-binding-schema.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-edit-output-binding-schema.png#lightbox)

#### 3. Adding fields to update

After adding the new field to update configuration, it must be updated with the `var_requestParam` to include added field and the values to send to update with.

Refer to the built-in "write" scenarios for further guidance to extend other scenarios.

**Authorization**

- Authorization is done using the `permissionsMetadata`/`rolePermission` that is part of the Template configuration. The `permissionsMetadata` and User ID are used to create the query string for OData Connector in `SuccessFactors Check User Permissions flow`. If `SuccessFactors Check User Permissions flow` doesn't find `permissionsMetadata` it runs roleBased Permissions flow using role permission and user roles variable
- It's important to include permissionMetadata or rolePermission in template configuration file as there's no other authorization check if both of those fields are missing.

### Veteran Info

| Veteran info | Description |
| --- | --- |
| Description | Retrieves the employee's current veteran information and presents it in an adaptive card, which the employee can edit and submit to update their veteran info |
| Validations & Errors | If employee's `Country_Code` does not exist in `SuccessFactors_VeteranInfo_Countries` environment variable then Topic won't run and instead return a "Sorry, this capability isn't available in `<ESS_UserContext_Country_Code>` at this moment." message |
| Prompts | <li>Can I update my Veteran status?</li><br><br><li>Is there a process to update my military/veteran status?</li><br><br><li>Do I have to provide my military/veteran details?</li> |
| Adaptive Card | There are two adaptive cards for each support country/region, which are picked using a switch statement based on the employees `ESS_SuccessFactors_UserContext_Country_Code`<br><br><span class="mx-imgBorder"><br><a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-adaptive-card-condition-options.png#lightbox" data-linktype="relative-path"><br><img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-adaptive-card-condition-options.png" alt="Screenshot of the adaptive condition options." data-linktype="relative-path"><br></a><br></span> |

#### Get configurations

There are differences between where the data is stored between country/region. You must have a two template configurations. These configurations differ in:

- `RootEntity`
- `RequestEntities`

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeGetVeteranInfo_USA` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetVeteranInfo_USA` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id` and `userId` using `ESS_UserContext_User_Id` |
| **Values queried** | <li><code>Country</code>: necessary to make the <code>upsert</code> call for the employee. <code>PerGlobalInfoUSA</code> expects this value in the <code>requestbody</code>. This value needs to be fetched and included in the <code>update_parameters</code></li><br><br><li><code>StartDate</code>: <code>StartDate</code> is necessary to make the upsert call for the employee. When making an <code>upsert</code> call to <code>PerGlobalInfoUSA</code>, request body expects the <code>startDate</code> saved in the data in epoch format. The <code>starteDate</code> is fetched and included in the <code>update_parameters</code></li><br><br><li><code>Veteran</code>: Employee&#39;s veteran status as a yes/no value.</li><br><br><li><code>ChallengedVeteran</code>: Employee&#39;s challenged veteran designation as a yes/no value.</li><br><br><li><code>SpecialDisabledVeteran</code>: Employee&#39;s special veteran who has a disability designation as a yes/no value.</li> |

**Configuration**

```json
	{
  "scenario": "VeteranInformation",
  "rootEntity": "PerGlobalInfoUSA",
  "filter": "personIdExternal eq {personIdExternalVal} and personNav/employmentNav/userId eq '{userIdVal}'",
  "requestEntities": [
    {
      "key": "Country",
      "valuePath": "country",
      "labelPath": ""
    },    
    {
      "key": "StartDate",
      "valuePath": "startDate",
      "labelPath": ""
    },
    {
      "key": "Veteran",
      "valuePath": "genericNumber1",
      "labelPath": "PerGlobalInfoUSA/genericNumber1"
    },
    {
      "key": "ChallengedVeteran",
      "valuePath": "genericNumber2",
      "labelPath": "PerGlobalInfoUSA/genericNumber2"
    },
    {
      "key": "SpecialDisabledVeteran ",
      "valuePath": "genericNumber6",
      "labelPath": "PerGlobalInfoUSA/genericNumber6"
    }
  ], 
  "permissionsMetadata": [],
  "rolePermissions": []
}
```

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeGetVeteranInfo_GBR` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetVeteranInfo_GBR` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id` and `userId` using `ESS_UserContext_User_Id` |
| **Values queried** | <li><code>Country</code>: Required to make the <code>upsert</code> call for the employee. <code>PerGlobalInfoGBR</code> expects this value in the <code>requestbody</code>. This value needs to be fetched and included in the update_parameters. </li><br><br><li><code>StartDate</code>: Required to make the <code>upsert</code> call for the employee. When making an <code>upsert</code> call to <code>PerGlobalInfoGBR</code> request body expects the <code>startDate</code> saved in epoch format. The <code>starteDate</code> value is fetched and included in the <code>update_parameters</code></li><br><br><li><code>Veteran</code>: Employee&#39;s veteran status as <code>MILITARYSTATUS_GBR</code> picklist values</li> |

**Configuration**:

```json
	{
  "scenario": "VeteranInformation",
  "rootEntity": "PerGlobalInfoGBR",
  "filter": "personIdExternal eq {personIdExternalVal} and personNav/employmentNav/userId eq '{userIdVal}'",
  "requestEntities": [
{
      "key": "Country",
      "valuePath": "country",
      "labelPath": ""
    },    
{
      "key": "StartDate",
      "valuePath": "startDate",
      "labelPath": ""
    },
{
      "key": "Veteran",
      "valuePath": "genericNumber1",
      "labelPath": "PerGlobalInfoGBR/genericNumber1"
    }
  ], 
  "permissionsMetadata": [],
  "rolePermissions": []
}
```

#### Picklist Configuration

There are differences between where the data is stored between countries therefore it's required to have two template configurations. These configurations differ in:

- `RootEntity`
- `RequestEntities`

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeGetPicklistVeteranInfo_USA` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetPicklistVeteranInfo_USA` |
| **Filter** | Filters for `picklistId` `'yesNo'` and locale, which is `ESS_UserContext_Locale` |
| **Values queried** | <li><code>optionId</code>: Value used for data corresponding to label name. </li><br><br><li><code>Label</code>: Human readable name</li> |

**Configuration**

```json
{
    "scenario": "VeteranInfo_USA",
    "rootEntity": "PicklistLabel",
    "filter": "picklistOption/picklist/picklistId eq 'yesNo' and locale eq '{localeValue}'",
    "requestEntities": [
                {
            "key": "optionId",
            "valuePath": "optionId",
            "labelPath": ""
        },
        {
            "key": "label",
            "valuePath": "label",
            "labelPath": ""
        }
        ],
    "permissionsMetadata": [],
        "rolePermissions": []
}
```

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeGetPicklistVeteranInfo_GBR` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetPicklistVeteranInfo_GBR` |
| **Filter** | Filters for `picklistId` `'MILITARYSTATUS_GBR'` and locale, which is `ESS_UserContext_Locale` |
| **Values queried** | <li><code>optionId</code>: Value used for data corresponding to label name</li><br><br><li><code>Label</code>: Human readable name</li> |

**Configuration**:

```json

	{
    "scenario": "MilitaryStatus_GBR",
    "rootEntity": "PicklistLabel",
    "filter": "picklistOption/picklist/picklistId eq 'MILITARYSTATUS_GBR' and locale eq '{localeValue}'",
    "requestEntities": [
                {
            "key": "optionId",
            "valuePath": "optionId",
            "labelPath": ""
        },
        {
            "key": "label",
            "valuePath": "label",
            "labelPath": ""
        }
        ],
    "permissionsMetadata": [],
    "rolePermissions": []
}
```

#### Write Configuration

The difference between countries/regions in these write configurations are the uri/RootEntity and number of fields being different, such as GBR configuration doesn't have `genericNumber2` & `genericNumber6` as they are not used.

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeUpdateVeteranInfo_USA` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateVeteranInfo_USA` |
| **Request Body** | <li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li><br><br><li><code>Country</code>: Required to make the <code>upsert</code> call for the employee. <code>PerGlobalInfoUSA</code> expects this value in the <code>requestbody</code>. Therefore it&#39;s fetched and included in the update_parameters</li><br><br><li><code>StartDate</code>: Necessary to make the <code>upsert</code> call for the employee. When making an <code>upsert</code> call to <code>PerGlobalInfoUSA</code> request body expects the <code>startDate</code> that is saved in the data in epoch format. Therefore, <code>startDate</code> is fetched and included it in <code>update_parameters</code>.</li><br><br><li><code>genericNumber1</code>: Veteran status value input option collected from employee</li><br><br><li><code>genericNumber2</code>: Challenged veteran value input option collected from employee</li><br><br><li><code>genericNumber6</code>: Special veteran who has disabilities input option value collected from employee</li> |

**Configuration**:

```json
	{
    "scenario": "UpdateVeteranInformation",
    "requestBody": '{
        "__metadata": {
            "uri": "PerGlobalInfoUSA"
        },  
        "personIdExternal": "personIdExternalVal",
        "country": "countryVal",
        "startDate": "/Date(startDateVal)/",
        "genericNumber1": "genericNumber1Val",
        "genericNumber2": "genericNumber2Val",
        "genericNumber6": "genericNumber6Val",
    }',
    "permissionsMetadata": [],
    "rolePermissions": []
}
```

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeUpdateVeteranInfo_GBR` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateVeteranInfo_GBR` |
| **Request Body** | <li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li><br><br><li><code>Country</code>: Necessary to make the <code>upsert</code> call for the employee. <code>PerGlobalInfoGBR</code> expects this value in the <code>requestbody</code>. This value is fetched and included in the update_parameters</li><br><br><li><code>StartDate</code>: <code>StartDate</code> is necessary to make the <code>upsert</code> call for the employee. When making an upsert call to <code>PerGlobalInfoGBR</code>, request body expects the <code>startDate</code> saved in epoch format. <code>startDate</code> is fetched and included in the update_parameters</li><br><br><li><code>genericNumber1</code>: Veteran status value collected from user</li> |

**Configuration**

```
{
    "scenario": "UpdateVeteranInformation",
    "requestBody": '{
        "__metadata": {
            "uri": "PerGlobalInfoGBR"
        },
        "personIdExternal": "personIdExternalVal",
        "country": "countryVal",
        "startDate": "/Date(startDateVal)/",
        "genericNumber1": "genericNumber1Val"
    }',
    "permissionsMetadata": [],
    "rolePermissions": []
}
```

**Customizations** Adding an additional country/region requires the following:

1. Add all the respective template configurations
2. If new country/region has different fields or collects a different data type, then input the text and add a new condition for the new country/region. Then, set up the adaptive card as required for country/region and any other requirements.

### Race & Ethnicity

| Race & Ethnicity | Description |
| --- | --- |
| **Description** | Retrieves the employee's current ethnicity information and presents it in an adaptive card, which the employee can edit and submit to update their information. |
| **Validations & Errors** | If user's `Country_Code` does not exist in the `SuccessFactors_RaceAndEthnicity_Countries` environment variable, then Topic won't run and instead return "Sorry, this capability isn't available in `<ESS_UserContext_Country_Code>` at this moment." |
| **Prompts** | <li>I want to update my Race/ethnicity information</li><br><br><li>How to update my Race/ethnicity information</li><br><br><li>What is the process to update my Race/ ethnicity information?</li> |
| **Adaptive card** | Although race & ethnicity topic support two countries/regions, the fields for both country/regions are the same. It isn't required to have multiple adaptive cards. As more countries/regions are added, a switch statement is added to the flow when a new country/region with different fields needs to be supported. |

#### Get configurations

There are differences between where the data is stored between countries/regions. Therefore, two template configurations are required. These configurations differ in:

- `RootEntity`

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeGetRaceAndEthnicity_USA` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetRaceAndEthnicity_USA` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id` and `userId` using `ESS_UserContext_User_Id` |
| **Values queried** | <li><code>Country</code>: Required to make the <code>upsert</code> call for the employee. <code>PerGlobalInfoUSA</code> expects this value in the <code>requestbody</code>. This value is fetched and included in the <code>update_parameters</code>.</li><br><br><li><code>StartDate</code>: Required to make the <code>upsert</code> call for the employee. When making an <code>upsert</code> call to <code>PerGlobalInfoUSA</code>, request body expects the <code>startDate</code> saved in epoch format. <code>startDate</code> is fetched and included in the <code>update_parameters</code></li><br><br><li><code>EthnicGroup</code>: Employee&#39;s ethnic group as an <code>ETHNIC-GROUP_USA</code> picklist value</li> |

**Configuration**

```JSON
	{
  "scenario": "RaceAndEthnicity",
  "rootEntity": "PerGlobalInfoUSA",
  "filter": "personIdExternal eq {personIdExternalVal} and personNav/employmentNav/userId eq '{userIdVal}'",
  "requestEntities": [
    {
      "key": "EthnicGroup",
      "valuePath": "genericString1",
      "labelPath": "PerGlobalInfoUSA/genericString1"
    },
{
      "key": "Country",
      "valuePath": "country",
      "labelPath": ""
    },
{
      "key": "startDate",
      "valuePath": "startDate",
      "labelPath": ""
    }
  ], 
  "permissionsMetadata": [],
  "rolePermissions": []
}
```

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeGetRaceAndEthnicity_GBR` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeGetRaceAndEthnicity_GBR` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id` and `userId` using `ESS_UserContext_User_Id` |
| **Values queried** | <li><code>Country</code>: Required to make the <code>upsert</code> call for the employee. <code>PerGlobalInfoGBR</code> expects country in the <code>requestbody</code> therefore it&#39;s fetched and included in the <code>update_parameters</code>.</li><br><br><li><code>StartDate</code>: Required to make the <code>upsert</code> call for the employee. When making an <code>upsert</code> call to <code>PerGlobalInfoGBR</code> request body expects the <code>startDate</code> saved in epoch format. Therefore, <code>startDate</code> is fetched and included in the update_parameters</li><br><br><li><code>EthnicGroup</code>: Employee&#39;s ethnic group as an <code>ETHNICGROUP_GBR picklist</code> value</li> |

**Configuration**

```json

{
  "scenario": "RaceAndEthnicity",
  "rootEntity": "PerGlobalInfoGBR",
  "filter": "personIdExternal eq {personIdExternalVal} and personNav/employmentNav/userId eq '{userIdVal}'",
  "requestEntities": [
    {
      "key": "EthnicGroup",
      "valuePath": "genericString1",
      "labelPath": "PerGlobalInfoGBR/genericString1"
    },
{
      "key": "Country",
      "valuePath": "country",
      "labelPath": ""
    },
{
      "key": "startDate",
      "valuePath": "startDate",
      "labelPath": ""
    }
  ], 
  "permissionsMetadata": [],
  "rolePermissions": []
}
```

##### Picklist Configuration

The only difference between countries in picklist config is the `picklistId` each is pointing to.

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetPicklistRaceAndEthnicity_USA` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetPicklistRaceAndEthnicity_USA` |
| **Filter** | Filters for `picklistId` `'ETHNIC-GROUP_USA'` and `locale` which is `ESS_UserContext_Locale` |
| **Values queried** | <li><code>optionId</code>: Value used for data corresponding to label name.</li><br><br><li><code>Label</code>: Human readable name</li> |

**Configuration**

```json

{
    "scenario": "RaceAndEthnicity_USA",
    "rootEntity": "PicklistLabel",
    "filter": "picklistOption/picklist/picklistId eq 'ETHNIC-GROUP_USA' and locale eq '{localeValue}'",
    "requestEntities": [
                {
            "key": "optionId",
            "valuePath": "optionId",
            "labelPath": ""
        },
        {
            "key": "label",
            "valuePath": "label",
            "labelPath": ""
        }
        ],
    "permissionsMetadata": [],
        "rolePermissions": []
}
```

**Picklist configuration in Race & Ethnicity** \| Configuration \| Description \| \| --- \| --- \| \|**Template configuration** \| `HRSAPSuccessFactorsHCMGetPicklistRaceAndEthnicity_GBR`\| \|**Scenario name**\| `msdyn_HRSAPSuccessFactorsHCMGetPicklistRaceAndEthnicity_GBR`\| \|**Filter** \| Filters for `picklistId 'ETHNICGROUP_GBR'` and `locale` which is `ESS_UserContext_Locale | |**Values queried**|<li>`optionId`: Value used for data corresponding to label name<li>`Label`: Human readable name\|

**Configuration**

```json
	{
    "scenario": "RaceAndEthnicity_GBR",
    "rootEntity": "PicklistLabel",
    "filter": "picklistOption/picklist/picklistId eq 'ETHNICGROUP_GBR' and locale eq '{localeValue}'",
    "requestEntities": [
                {
            "key": "optionId",
            "valuePath": "optionId",
            "labelPath": ""
        },
        {
            "key": "label",
            "valuePath": "label",
            "labelPath": ""
        }
        ],
    "permissionsMetadata": [],
        "rolePermissions": []
}
```

#### Write Configuration

The difference between countries in these `write` configurations is:

- `RootEntity`

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeUpdateRaceAndEthnicity_USA` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateRaceAndEthnicity_USA` |
| **Request Body** | <li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li><br><br><li><code>Country</code>: Required to make the <code>upsert</code> call for the employee.</li><br><br><li><code>PerGlobalInfoUSA</code> expects this value in the <code>requestbody</code> therefore this value is fetched and included in the <code>update_parameters</code></li><br><br><li><code>StartDate</code>:<code>StartDate</code> is required to make the <code>upsert</code> call for the employee. When making an <code>upsert</code> call to <code>PerGlobalInfoUSA</code> request body expects <code>startDate</code> saved in epoch format. Therefore, this value is fetched and included in <code>update_parameters</code>.</li><br><br><li><code>genericString1</code>: Ethnic group value collected from employee</li> |

**Configuration**:

```json
	{
    "scenario": "UpdateRaceAndEthnicity",
    "requestBody": '{
        "__metadata": {
            "uri": "PerGlobalInfoUSA"
        },
        "personIdExternal": "personIdExternalVal",
        "country": "countryVal",
        "startDate": "/Date(startDateVal)/",
        "genericString1": "genericString1Val"
    }',
    "permissionsMetadata": [],
    "rolePermissions": []
}
```

| Configuration | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeUpdateRaceAndEthnicity_GBR` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateRaceAndEthnicity_GBR` |
| **Request Body** | <li><code>personIdExternal</code>: ESS_UserContext_Employee_Id<code>&lt;li&gt;</code>Country<code>: This value is necessary to make the </code>upsert<code>call for the employee.</code>PerGlobalInfoGBR<code>expects this value in the</code>requestbody<code>. This value is fetched and included in </code>update_parameters<code>&lt;li&gt;</code>StartDate<code>: </code>StartDate<code>is necessary to make the</code>upsert<code>call for the employee. When making an</code>upsert<code>call to</code>PerGlobalInfoGBR<code>request body expects the</code>startDate<code>saved in epoch format. </code>startDate<code> is fetched and included in the update_parameters&lt;li&gt;</code>genericString1`: Ethnic group value collected from employee</li> |

**Configuration**

```json


	{
    "scenario": "UpdateRaceAndEthnicity",
    "requestBody": '{
        "__metadata": {
            "uri": "PerGlobalInfoGBR"
        },
        "personIdExternal": "personIdExternalVal",
        "country": "countryVal",
        "startDate": "/Date(startDateVal)/",
        "genericString1": "genericString1Val"
    }',
    "permissionsMetadata": [],
    "rolePermissions": []
}
```

**Customizations** Adding an additional country/region requires the following:

1. Adding all the respective template configurations
2. If the new country/region has different fields or collects a different data type, then input the text and add a new condition for the new country/region. Then, set up the adaptive card as required for country and any other requirements

### Emergency Contact

| Race & Ethnicity | Description |
| --- | --- |
| **Description** | Retrieves the employee's current emergency contacts, presents them to employees, and asks if they would like to update or add an emergency contact. Depending on their answer they are presented with an adaptive card to either update a current contact or a blank card for them to add a contact |
| **Prompts** | <li>Update my current/existing emergency contact</li><br><br><li>My emergency contact has changed; can I update it in the system?</li><br><br><li>How/where can I update my emergency contact?</li><br><br><li>I want to add new emergency contact</li><br><br><li>Add my emergency contact</li> |
| **Adaptive card** | Two kinds of adaptive cards are used in the following examples:<br><br><li>Update emergency contact</li><br><br><li>Add emergency contact<br><strong>Initial message</strong><br><span class="mx-imgBorder"><br><a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-update-emergency-contact1.png#lightbox" data-linktype="relative-path"><br><img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-update-emergency-contact1.png" alt="Screenshot of a prompt and response asking to update emergency contact information." data-linktype="relative-path"><br></a><br></span><br> <br><strong>Update emergency contact</strong><br><span class="mx-imgBorder"><br><a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-update-emergency-contact2.png#lightbox" data-linktype="relative-path"><br><img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-update-emergency-contact2.png" alt="Screenshot of an emergency contact picker list." data-linktype="relative-path"><br></a><br></span><br> <br><strong>Add emergency contact</strong><br><span class="mx-imgBorder"><br><a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-add-emergency-contact.png#lightbox" data-linktype="relative-path"><br><img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-add-emergency-contact.png" alt="Screenshot of how an employee can pick an emergency contact from a picker list." data-linktype="relative-path"><br></a><br></span><br></li> |

#### Get configurations - emergency contact and pick list for relationship type

Retrieving the existing emergency contact information along with relationship type is the first step in the flow \| Configuration \| Description \| \| --- \| --- \| \|**Template configuration** \|`HRSAPSuccessFactorsHCMEmployeeGetEmergencyContact`\| \|**Scenario name**\| `msdyn_HRSAPSuccessFactorsHCMEmployeeGetEmergencyContact`\| \|**Filter**\|Filters on `personIdExternal` using `ESS_UserContext_Employee_Id` and if `emergencyContactNav/primaryFlag` is equal to 'Y'\| \|**Values queried**\|

<li><code>name</code>: Emergency Contact name. No Label is necessary, so it is not fetched</li>

<li><code>phone</code>: Emergency Contact phone number. No Label is necessary, so it is not fetched. </li>

<li><code>relationship</code>: Relationship type of emergency contact. Values come from <code>relation</code> picklist Id. No Label is necessary, so it is not fetched</li>

<li><code>primaryFlag</code>: Boolean value for if emergency contact is primary contact. No label is necessary, so it is not fetched|<p></p>
<p><strong>Configuration</strong>:</p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeGetEmergencyContact&quot;,
    &quot;rootEntity&quot;: &quot;PerPerson&quot;,
    &quot;filter&quot;: &quot;emergencyContactNav/primaryFlag eq &#39;Y&#39; and personIdExternal eq &#39;{personIdExternalVal}&#39;&quot;,
    &quot;requestEntities&quot;: [
        {
            &quot;key&quot;: &quot;name&quot;,
            &quot;valuePath&quot;: &quot;emergencyContactNav/name&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        },
        {
            &quot;key&quot;: &quot;phone&quot;,
            &quot;valuePath&quot;: &quot;emergencyContactNav/phone&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        },
        {
            &quot;key&quot;: &quot;relationship&quot;,
            &quot;valuePath&quot;: &quot;emergencyContactNav/relationship&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }, 
        {
            &quot;key&quot;: &quot;primaryFlag&quot;,
            &quot;valuePath&quot;: &quot;emergencyContactNav/primaryFlag&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }
    ],
    &quot;permissionsMetadata&quot;: [],
        &quot;rolePermissions&quot;: []
}
</code></pre>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMGetPicklistRelationshipType</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMGetPicklistRelationshipType</code></td>
</tr>
<tr>
<td><strong>Filter</strong></td>
<td>Filters on <code>picklistId</code> in <code>relation</code> and <code>locale</code> which is <code>ESS_UserContext_Locale</code></td>
</tr>
<tr>
<td><strong>Values queried</strong></td>
<td><li><code>optionId</code>: Value used for data corresponding to label name</li><li><code>Label</code>: Human readable name</li></td>
</tr>
</tbody>
</table>
<p>Configuration</p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMGetPicklistRelationshipType&quot;,
    &quot;rootEntity&quot;: &quot;PicklistLabel&quot;,
    &quot;filter&quot;: &quot;picklistOption/picklist/picklistId eq &#39;relation&#39; and locale eq &#39;{localeValue}&#39;&quot;,
    &quot;requestEntities&quot;: [ 
                {
            &quot;key&quot;: &quot;optionId&quot;,
            &quot;valuePath&quot;: &quot;optionId&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        },
        {
            &quot;key&quot;: &quot;label&quot;,
            &quot;valuePath&quot;: &quot;label&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }
        ],
    &quot;permissionsMetadata&quot;: [],
        &quot;rolePermissions&quot;: []
}
</code></pre>
<h5 id="update-emergency-contact">Update emergency contact</h5>
<p>Updating the emergency contact information
| Configuration | Description |
| --- | --- |
|<strong>Template configuration</strong>|<code>HRSAPSuccessFactorsHCMEmployeeUpdateEmergencyContact</code>|
|<strong>Scenario name</strong> | <code>msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateEmergencyContact</code>|
|<strong>Request Body</strong> |</p></li>

<li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li>

<li><code>relationship</code>: Relationship value of emergency contact</li>

<li><code>name</code>:Emergency contact name collected from employee</li>

<li><code>primaryFlag</code>: PrimaryFlag value from get call is automatically used here unless a new contact is added or else its false. If a first contact is being added, then it is automatically primary.</li>

<li><code>phone</code>: Emergency contact phone number collected from employee|<p></p>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">
	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeUpdateEmergencyContact&quot;,
    &quot;requestBody&quot;: &#39;{
        &quot;__metadata&quot;: {
            &quot;uri&quot;: &quot;PerEmergencyContacts&quot;
        },
        &quot;personIdExternal&quot;: &quot;personIdExternalVal&quot;,
        &quot;relationship&quot;: &quot;relationshipVal&quot;,
        &quot;name&quot;:&quot;nameVal&quot;,
        &quot;primaryFlag&quot;:&quot;primaryFlagVal&quot;,
        &quot;phone&quot;:&quot;phoneVal&quot;
    }&#39;,
    &quot;permissionsMetadata&quot;: [],
    &quot;rolePermissions&quot;: []
}
</code></pre>
<h5 id="delete-existing-emergency-contact">Delete existing emergency contact</h5>
<p>Update emergency contact flow has an extra configuration which deletes an existing emergency contact for the employee.  This configuration is used exclusively when an employee updates name of one of their current emergency contacts which must delete the current entry and add a new one with the change.</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMEmployeeDeleteEmergencyContact</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMEmployeeDeleteEmergencyContact</code></td>
</tr>
<tr>
<td><strong>Request Body</strong></td>
<td><li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li><li><code>relationship</code>: relationship value of emergency contact</li><li><code>name</code>: Emergency contact name collected from employee</li><li><code>primaryFlag</code>:<code>PrimaryFlag</code> value from get call is automatically used here unless a new contact is added or else its false. If a first contact is being added, then it is automatically primary</li><li><code>phone</code>:Emergency contact phone number collected from employee</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong>:</p>
<pre><code class="lang-json">
	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeUpdateEmergencyContact&quot;,
    &quot;requestBody&quot;: &#39;{
        &quot;__metadata&quot;: {
            &quot;uri&quot;: &quot;PerEmergencyContacts&quot;
        },
        &quot;operation&quot;: &quot;operationVal&quot;,
        &quot;personIdExternal&quot;: &quot;personIdExternalVal&quot;,
        &quot;relationship&quot;: &quot;relationshipVal&quot;,
        &quot;name&quot;:&quot;nameVal&quot;,
        &quot;primaryFlag&quot;:&quot;primaryFlagVal&quot;,
        &quot;phone&quot;:&quot;phoneVal&quot;
    }&#39;,
    &quot;permissionsMetadata&quot;: [],
    &quot;rolePermissions&quot;: []
}
</code></pre>
<h3 id="phone">Phone</h3>
<table>
<thead>
<tr>
<th>Phone</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Description</strong></td>
<td>Retrieves the employee&#39;s phone data, presents them to the employee, and asks if they would like to update or add a phone number. Depending on their answer they are presented with an adaptive card to either update a current contact or a blank card for them to add a phone number</td>
</tr>
<tr>
<td><strong>Prompts</strong></td>
<td><li>Update my current/existing emergency contact</li><li>My emergency contact has changed; can I update it in the system?</li><li>How/where can I update my emergency contact?</li><li>I want to add new emergency contact</li><li>Add my emergency contact</li></td>
</tr>
<tr>
<td>Adaptive card</td>
<td>Two kinds of adaptive cards can be used to change an employee&#39;s phone information: <li>Update phone</li><li>Add phone<br> The following screenshot shows an example of an adaptive card to add a phone number. <br><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-add-phone.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/employee-add-phone.png" alt="Screenshot of an adaptive card adding a phone number." data-linktype="relative-path">
</a>
</span>
</li></td>
</tr>
</tbody>
</table>
<h4 id="get-configurations---existing-phone-numbers-and-pick-list-for-phone-number-type-option">Get configurations - existing phone numbers and pick list for phone number type option</h4>
<p>Retrieving the existing phone numbers along with phone number type is the first step in the flow.</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMEmployeeGetContactPhone</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMEmployeeGetContactPhone</code></td>
</tr>
<tr>
<td><strong>Filter</strong></td>
<td>Filters on <code>personIdExternal</code> using <code>ESS_UserContext_Employee_Id</code></td>
</tr>
<tr>
<td><strong>Values queried</strong></td>
<td><li><code>areaCode</code>: Area code section of phone number</li><li><code>phoneNumber</code>: All numbers after the area code in a phone number. Also defined as Prefix + line number</li><li><code>countryCode</code>: Country code designation of phone.Example: 1 for US</li><li><code>phoneType</code>: Phone type values come from <code>ecPhoneType</code> <code>picklist Id</code></li><li><code>isPrimary</code>: Boolean flag for whether the Phone is primary or not</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeGetContactPhone&quot;,
    &quot;rootEntity&quot;: &quot;PerPerson&quot;,
    &quot;filter&quot;: &quot;personIdExternal eq &#39;{personIdExternalVal}&#39;&quot;,
    &quot;requestEntities&quot;: [
        {
            &quot;key&quot;: &quot;areaCode&quot;,
            &quot;valuePath&quot;: &quot;phoneNav/areaCode&quot;,
            &quot;labelPath&quot;: &quot;PerPhone/areaCode&quot;
        },
        {
            &quot;key&quot;: &quot;phoneNumber&quot;,
            &quot;valuePath&quot;: &quot;phoneNav/phoneNumber&quot;,
            &quot;labelPath&quot;: &quot;PerPhone/phoneNumber&quot;
        },
        {
            &quot;key&quot;: &quot;countryCode&quot;,
            &quot;valuePath&quot;: &quot;phoneNav/countryCode&quot;,
            &quot;labelPath&quot;: &quot;PerPhone/countryCode&quot;
        },
        {
            &quot;key&quot;: &quot;phoneType&quot;,
            &quot;valuePath&quot;: &quot;phoneNav/phoneType&quot;,
            &quot;labelPath&quot;: &quot;PerPhone/phoneType&quot;
        },
        {
            &quot;key&quot;: &quot;isPrimary&quot;,
            &quot;valuePath&quot;: &quot;phoneNav/isPrimary&quot;,
            &quot;labelPath&quot;: &quot;PerPhone/isPrimary&quot;
        }
    ],
    &quot;permissionsMetadata&quot;: [],
        &quot;rolePermissions&quot;: []
}
</code></pre>
<h4 id="get-picklist-for-phone-types">Get picklist for phone types</h4>
<p>Getting the list of phone number type options like Cell, Work, etc.</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMGetPicklistPhoneType</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMGetPicklistPhoneType</code></td>
</tr>
<tr>
<td><strong>Filter</strong></td>
<td>Filters on <code>picklistId</code> in <code>ecPhoneType</code> and <code>locale</code> which is <code>ESS_UserContext_Locale</code></td>
</tr>
<tr>
<td><strong>Values queried</strong></td>
<td><li><code>optionId</code>: Value used for data corresponding to label name</li><li><code>Label</code>: Human readable name</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMGetPicklistPhoneType&quot;,
    &quot;rootEntity&quot;: &quot;PicklistLabel&quot;,
    &quot;filter&quot;: &quot;picklistOption/picklist/picklistId eq &#39;ecPhoneType&#39; and locale eq &#39;{localeValue}&#39; &quot;,
    &quot;requestEntities&quot;: [
                {
            &quot;key&quot;: &quot;optionId&quot;,
            &quot;valuePath&quot;: &quot;optionId&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        },
        {
            &quot;key&quot;: &quot;label&quot;,
            &quot;valuePath&quot;: &quot;label&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }
        ],
    &quot;permissionsMetadata&quot;: [],
        &quot;rolePermissions&quot;: []
}
</code></pre>
<h4 id="update-contact-phone">Update contact phone</h4>
<p>Update the contact phone number.</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMEmployeeUpdateContactPhone</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateContactPhone</code></td>
</tr>
<tr>
<td><strong>Request Body</strong></td>
<td><li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li><li><code>CountryCode</code>: Country code input from employee</li><li><code>areaCode</code>:Area code input from employee</li><li><code>phoneNumber</code>: Phone number input from employee</li><li><code>isPrimary</code>:<code>isPrimary</code> value from get call is automatically used here unless a new contact is added or else it is false. If a first contact is being added, then it is automatically primary.</li><li><code>phoneType</code>: Phone number type value input from employee</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeUpdateContactPhone&quot;,
    &quot;requestBody&quot;: &#39;{
      &quot;__metadata&quot;: {
        &quot;uri&quot;: &quot;PerPhone&quot;
        },
      &quot;personIdExternal&quot;: &quot;personIdExternalVal&quot;,
      &quot;countryCode&quot;: &quot;countryCodeVal&quot;,
      &quot;areaCode&quot;: &quot;areaCodeNav&quot;,
      &quot;phoneNumber&quot;: &quot;phoneNumberVal&quot;,
      &quot;isPrimary&quot;: isPrimaryVal,
      &quot;phoneType&quot;: &quot;phoneTypeVal&quot;
      }&#39;,
    &quot;permissionsMetadata&quot;: [],
    &quot;rolePermissions&quot;: []
}
</code></pre>
<h3 id="email">Email</h3>
<table>
<thead>
<tr>
<th>Email</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Description</strong></td>
<td>Retrieves the employee&#39;s current email address, displays it, and then prompts employee to submit a new email address</td>
</tr>
<tr>
<td><strong>Prompts</strong></td>
<td><li>I want to update my personal email</li><li>update my personal email to <code>[email_addressTobeUpdated]</code></li><li>Update my email</li><li>I&#39;d like to update my email</li></td>
</tr>
</tbody>
</table>
<h4 id="get-configurations---contact-email">Get configurations - contact email</h4>
<p>Retrieving the existing contact email is the first step in the flow</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMEmployeeGetContactEmail</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMEmployeeGetContactEmail</code></td>
</tr>
<tr>
<td><strong>Filter</strong></td>
<td>Filters on <code>personIdExternal</code> using <code>ESS_UserContext_Employee_Id</code> and email type using picklist <code>emailType</code> value for Personal</td>
</tr>
<tr>
<td><strong>Values queried</strong></td>
<td><li><code>emailAddress</code>: Employee&#39;s current email address</li><li><code>emailType</code>: Types of Email values from picklist id &#39;ecEmailType&#39;.</li><li><code>isPrimary</code>: Boolean flag for if Email is primary</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeGetContactEmail&quot;,
    &quot;rootEntity&quot;: &quot;PerEmail&quot;,
    &quot;filter&quot;: &quot;emailType eq &#39;{emailTypeVal}&#39; and personIdExternal eq &#39;{personIdExternalVal}&#39;&quot;,
    &quot;requestEntities&quot;: [
        {
            &quot;key&quot;: &quot;emailAddress&quot;,
            &quot;valuePath&quot;: &quot;emailAddress&quot;,
            &quot;labelPath&quot;: &quot;PerEmail/emailAddress&quot;
        },
        {
            &quot;key&quot;: &quot;isPrimary&quot;,
            &quot;valuePath&quot;: &quot;isPrimary&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        },
        {
            &quot;key&quot;: &quot;emailType&quot;,
            &quot;valuePath&quot;: &quot;emailType&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }
    ],
    &quot;permissionsMetadata&quot;: [],
        &quot;rolePermissions&quot;: []
}
</code></pre>
<h4 id="get-picklist-for-email-types">Get picklist for email types</h4>
<p>Getting the list of email type options</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMGetPicklistEmailType</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMGetPicklistEmailType</code></td>
</tr>
<tr>
<td><strong>Filter</strong></td>
<td>Filters on <code>picklistId</code> in <code>ecEmailType</code> and locale which is <code>ESS_UserContext_Locale</code> and picklistOption/externalCode eq &#39;P&#39;</td>
</tr>
<tr>
<td><strong>Values queried</strong></td>
<td><li><code>optionId</code>: Value used for data corresponding to label name</li><li><code>Label</code>: Human readable name</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMGetPicklistEmailType&quot;,
    &quot;rootEntity&quot;: &quot;PicklistLabel&quot;,
    &quot;filter&quot;: &quot;picklistOption/picklist/picklistId eq &#39;ecEmailType&#39; and locale eq &#39;{localeValue}&#39; and picklistOption/externalCode eq &#39;P&#39;&quot;,
    &quot;requestEntities&quot;: [ 
                {
            &quot;key&quot;: &quot;optionId&quot;,
            &quot;valuePath&quot;: &quot;optionId&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        },
        {
            &quot;key&quot;: &quot;externalCode&quot;,
            &quot;valuePath&quot;: &quot;picklistOption/externalCode&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }, 
        {
            &quot;key&quot;: &quot;label&quot;,
            &quot;valuePath&quot;: &quot;label&quot;,
            &quot;labelPath&quot;: &quot;&quot;
        }
        ],
    &quot;permissionsMetadata&quot;: [],
        &quot;rolePermissions&quot;: []
}
</code></pre>
<h4 id="update-contact-email">Update contact email</h4>
<p>Updating the contact email</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMEmployeeUpdateContactEmail</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMEmployeeUpdateContactEmail</code></td>
</tr>
<tr>
<td><strong>Request Body</strong></td>
<td><li><code>personIdExternal</code>:<code>ESS_UserContext_Employee_Id</code></li><li><code>emailAddress</code>: New email address input from employee</li><li>emailType: Always set to &#39;Personal&#39; from <code>emailType</code> picklist</li><li><code>isPrimary</code>: Always set to true value. No support for updating emails that are not primary</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeUpdateContactEmail&quot;,
    &quot;requestBody&quot;: &#39;{
        &quot;__metadata&quot;: {
            &quot;uri&quot;: &quot;PerEmail&quot;
        },
        &quot;personIdExternal&quot;: &quot;personIdExternalVal&quot;,
        &quot;emailAddress&quot;: &quot;emailAddressVal&quot;,
        &quot;emailType&quot;:&quot;emailTypeVal&quot;,
        &quot;isPrimary&quot;: isPrimaryVal
    }&#39;,
    &quot;validationRules&quot;: &quot;&quot;,
    &quot;permissionsMetadata&quot;: [],
    &quot;rolePermissions&quot;: []
}
</code></pre>
<h3 id="preferred-name">Preferred Name</h3>
<table>
<thead>
<tr>
<th>Preferred Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Description</strong></td>
<td>Retrieves the employees current preferred name, displays it, and then prompts employee to submit a new name. Employee can also include name in prompt.</td>
</tr>
<tr>
<td><strong>Prompts</strong></td>
<td><li>Update my preferred name</li><li>Change my preferred name</li><li>Change my preferred name to<code>[new_preferred_name]</code></li><li>I&#39;d like to update my preferred name to <code>[new_preferred_name]</code></li></td>
</tr>
</tbody>
</table>
<h4 id="get-configurations---preferred-name">Get configurations - preferred name</h4>
<p>Retrieving the existing preferred name is the first step in the flow</p>
<table>
<thead>
<tr>
<th>Configuration</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Template configuration</strong></td>
<td><code>HRSAPSuccessFactorsHCMEmployeeGetPreferredName</code></td>
</tr>
<tr>
<td><strong>Scenario name</strong></td>
<td><code>msdyn_HRSAPSuccessFactorsHCMEmployeeGetPreferredName</code></td>
</tr>
<tr>
<td><strong>Filter</strong></td>
<td>Filters on <code>personIdExternal</code> using <code>ESS_UserContext_Employee_Id</code></td>
</tr>
<tr>
<td><strong>Values queried</strong></td>
<td><li><code>preferredName</code>: Employee&#39;s current preferred name</li></td>
</tr>
</tbody>
</table>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">{
  &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeGetPreferredName&quot;,
  &quot;rootEntity&quot;: &quot;PerPerson&quot;,
  &quot;filter&quot;: &quot;personIdExternal eq &#39;{personIdExternalVal}&#39;&quot;,
  &quot;requestEntities&quot;: [
    {
      &quot;key&quot;: &quot;preferredName&quot;,
      &quot;valuePath&quot;: &quot;personalInfoNav/preferredName&quot;,
      &quot;labelPath&quot;: &quot;PerPersonal/preferredName&quot;
    }
  ],
  &quot;permissionsMetadata&quot;: [],
  &quot;rolePermissions&quot;: []
}
</code></pre>
<h4 id="update-preferred-name">Update preferred name</h4>
<p>Updating the preferred name
| Configuration | Description |
| --- | --- |
|<strong>Template configuration</strong>|<code>HRSAPSuccessFactorsHCMEmployeeUpdatePreferredName</code>|
|<strong>Scenario name</strong>|<code>msdyn_HRSAPSuccessFactorsHCMEmployeeUpdatePreferredName</code>|
|<strong>Request Body</strong>|</p></li>

<li><code>personIdExternal</code>: <code>ESS_UserContext_Employee_Id</code></li>

<li><code>preferredName</code>: New preferred name input from employee|<p></p>
<p><strong>Configuration</strong></p>
<pre><code class="lang-json">	{
    &quot;scenario&quot;: &quot;HRSAPSuccessFactorsHCMEmployeeUpdatePreferredName&quot;,
    &quot;requestBody&quot;: &#39;{
        &quot;__metadata&quot;: {
            &quot;uri&quot;: &quot;PerPersonal&quot;
        },
        &quot;personIdExternal&quot;: &quot;personIdExternalVal&quot;,
                &quot;startDate&quot;:&quot;/Date(startDateVal)/&quot;,
        &quot;preferredName&quot;: &quot;preferredNameVal&quot;
    }&#39;,
    &quot;validationRules&quot;: &quot;&quot;,
    &quot;permissionsMetadata&quot;: [],
    &quot;rolePermissions&quot;: []
}
</code></pre>
</li>
