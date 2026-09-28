<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/sap-manager-read-write-scenarios -->
<!-- Sitemap-Last-Modified: 2025-12-17 -->

# SAP SuccessFactors manager read & write scenarios with Employee Self-Service

The following article describes the different manager read and write scenarios for Employee Self-Service agent connected to SAP SuccessFactors:

- [SAP SuccessFactors manager read scenarios](#sap-successfactors-manager-read-scenarios)
- [SAP SuccessFactors manager write scenarios](#sap-successfactor-manager-write-scenarios)

## SAP SuccessFactors manager read scenarios

Manager read Topics check if the user is a manager using `ESS_UserContext_Is_Manager` variable. Afterwards most of the Topics follow the same format, which is simply redirecting the Topic to `SuccessFactors System Get Common Execution`, which calls the `Get Common Orchestrator` flow and then having the Large Language Model interpret responses from the flow and generate a response for the Manager. The `SuccessFactors System Get Common Execution` expects the following inputs:

**Filter Parameters:**  
Generally passing `Employee ID` and `User ID` for filter query for `Employee Read` Topics:

Example format used in a Topic:

```json
"{""personIdExternalVal"": """ & Global.ESS_UserContext_Employee_Id & """,""userIdVal"": """ & Global.ESS_UserContext_User_Id & """}" 
```

Example Template configuration:

```json
{ 
  ... 
  "filter": "personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'", 
  ... 
} 
```

The keys present in the filterParam must match what is expected in the Template configuration. In the previous examples, `personIdExternalVal` would be used as a key to insert `Global.ESS_UserContext_Employee_Id` into the filter expression.

**ScenarioName:** Configuration name, which is used by Dataverse call to get scenario configuration. **userIdentifier:** User ID

- Common Orchestrator then returns a `ModelResponse` and `LabelResponse`, which is then parsed using a large language model using the following instructions and generates answer for a Manager:
- Extract the input from the below response \(map the Label response *value* as key in model response attribute then provide model value\)
- Provide response to the user in a human readable form
- Format it properly so it looks clean and readable
- Use **only** data values from variable named as `successfactorsModelResponse` and use variable named as `successfactorsLabelResponse` for labelling the data. Response Example:

```json
Label Response : key":"company","value":"company" 

Model Response : 
"company":"11111" 

Example Output : 
Your company is 11111
```

The only exception to this general format is `Get Employee Id` and `Get Service Anniversary`, which are further explained in the following sections.

### Company Code

| Company Code | Details |
| --- | --- |
| **Description** | Retrieves the manager direct reports current company code and displays it. Manager can also include direct and job title in prompt. |
| **Prompts** | <li>Update cost center for <code>[EmployeeName]</code> </li><br><br><li>I want to update <code>[EmployeeName]</code>&#39;s cost center </li><br><br><li>I&#39;d like to update a team member&#39;s cost center to <code>[id_costCenter]</code> </li><br><br><li>Update <code>[EmployeeName]</code>&#39;s cost center to <code>[id_costCenter]</code> </li><br><br><li> Update cost center for my team</li> |
| **Response** | Here are the company codes for your direct reports:<br><br><li>Manuela	Torres: 2000 (Contoso UK)<br> </li><br><br><li> Gerardo Palacios: 2000 (Contoso UK)</li><br><br><li>Xiang	Tao: 2000 (Contoso UK)<br> If you need any further assistance, feel free to ask!</li> |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerCompanyCode` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerCompanyCode` |
| **Filter** | Filters on personIdExternal using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to false. `isContingentWorker` is to ensure only employees data is retrieved |
| **Values queried** | <li> <code>DisplayName</code>:  Directs current preferred name</li><br><br><li> <code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li> <code>CompanyCode</code>: Directs company code as an ID value </li><br><br><li> <code>CompanyName</code>: Directs company code as a name linked to ID value</li> |

**Configuration**:

```json
{ 
  "scenario": "ManagerReadCompanyCode", 
  "rootEntity": "EmpEmployment", 
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}'", 
  "requestEntities": [ 
    { 
      "key": "UserId", 
      "valuePath": "userNav/userId", 
      "labelPath": "User/userId" 
    }, 
    { 
      "key": "DisplayName", 
      "valuePath": "userNav/displayName", 
      "labelPath": "User/displayName" 
    }, 
    { 
      "key": "CompanyName", 
      "valuePath": "jobInfoNav/companyNav/name", 
      "labelPath": "" 
    }, 
    { 
      "key": "CompanyCode", 
      "valuePath": "jobInfoNav/company", 
      "labelPath": "EmpJob/company" 
    } 
  ], 
  "permissionsMetadata": [], 
  "rolePermissions": [ 
    { 
      "roleId": "115", 
      "permissions": [{ "permStringValue": "$_jobInfo_company_read" }] 
    } 
  ] 
} 
```

#### Get specific employee/direct report company code

This configuration is used when a directs name is filled with the manager's prompt. It includes a filter expression that filters on the different name fields trying to match it to what the manager included in the prompt:

| Get specific company code | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerEmpNameCompanyCode ` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerEmpNameCompanyCode ` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to false. `isContingentWorker` is used to ensure only employees data is retrieved. Additionally, the expression filters on `firstName`, `lastName`, and `displayName` using the slot filled name from manager's query |
| **Values queried** | <li> <code>DisplayName</code>: Directs current preferred name </li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li><code>CompanyCode</code>: Directs company code as an ID value</li> |
| **CompanyName** | Directs company code as a name linked to ID value. |

**Configuration**:

```json
{ 
    "scenario": "ManagerReadEmpNameCompanyCode", 
    "rootEntity": "EmpEmployment", 
    "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}' and (substringof(tolower('{name}'), tolower(userNav/firstName)) or substringof(tolower('{name}'), tolower(userNav/lastName)) or substringof(tolower('{name}'), tolower(userNav/displayName)))", 
    "requestEntities": [{ 
            "key": "UserId", 
            "valuePath": "userNav/userId", 
            "labelPath": "User/userId" 
        }, { 
            "key": "DisplayName", 
            "valuePath": "userNav/displayName", 
            "labelPath": "User/displayName" 
        }, { 
            "key": "CompanyName", 
            "valuePath": "jobInfoNav/companyNav/name", 
            "labelPath": "" 
        }, { 
            "key": "CompanyCode", 
            "valuePath": "jobInfoNav/company", 
            "labelPath": "EmpJob/company" 
        } 
    ], 
    "permissionsMetadata": [], 
    "rolePermissions": [{ 
            "roleId": "115", 
            "permissions": [{ 
                    "permStringValue": "$_jobInfo_company_read" 
                } 
            ] 
        } 
    ] 
}
```

### Cost Center

| Cost Center | Details |
| --- | --- |
| **Description** | Retrieves the manager's directs current company code and displays it. A Manager can also include direct and job title in the prompt. |
| **Prompts** | <li>Show cost center of all my direct reports</li><br><br><li>Show me my team&#39;s Cost center data</li><br><br><li>What cost centers are assigned to my reports?</li><br><br><li>What are my team&#39;s cost centers?</li><br><br><li>Show cost center of <code>[EmployeeName]</code> </li><br><br><li>What cost center is assigned to <code>[EmployeeName]</code></li> |
| **Response** | Here are the cost centers for your direct reports:<br><br><li>Manuela Torres: 2000-4200 (Contoso UK Production) </li><br><br><li> Gerardo Palacios: 2000-4200 (Contoso UK Production)</li><br><br><li>Xiang	Tao: 2000-2200 (Contoso UK HR)<br> If you need any further assistance, feel free to ask!</li> |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerCostCenter` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerCostCenter` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to `false`. `isContingentWorker` is to ensure only employees data are retrieved. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name</li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li> <code>CostCenterCode</code>: Directs cost center code as an ID value </li><br><br><li><code>CostCenterName</code>: Directs cost center as a name linked to ID value.</li> |

**Configuration**:

```json
{ 
 "scenario": "ManagerReadCostCenter", 
 "rootEntity": "EmpEmployment", 
 "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}'", 
 "requestEntities": [ 
   { 
     "key": "UserId", 
     "valuePath": "userNav/userId", 
     "labelPath": "User/userId" 
   }, 
   { 
     "key": "DisplayName", 
     "valuePath": "userNav/displayName", 
     "labelPath": "User/displayName" 
   }, 
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
 "permissionsMetadata": [], 
 "rolePermissions": [ 
   { 
     "roleId": "115", 
     "permissions": [{ "permStringValue": "$_jobInfo_cost-center_read" }] 
   } 
 ] 
} 
```

#### Get specific employee/directs cost center

This configuration is used when a directs name is filled with the manager's prompt. It includes a filter expression that filters on the different name fields trying to match it to what the manager included in the prompt.

| Get specific cost center | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerEmpNameCostCenter` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerEmpNameCostCenter` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to false. `isContingentWorker` is used to ensure only employees data are retrieved. Additionally, the expression filters on `firstName`, `lastName`, and `displayName` using the slot filled name from manager's query. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name </li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li><code>CostCenterCode</code>: Directs cost center code as an ID value </li><br><br><li><code>CostCenterName</code>: Directs cost center as a name linked to ID value</li> |

**Configuration**:

```json
{ 
  "scenario": "ManagerReadEmpNameCostCenter", 
  "rootEntity": "EmpEmployment", 
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}' and (substringof(tolower('{name}'), tolower(userNav/firstName)) or substringof(tolower('{name}'), tolower(userNav/lastName)) or substringof(tolower('{name}'), tolower(userNav/displayName)))", 
  "requestEntities": [ 
    { 
      "key": "UserId", 
      "valuePath": "userNav/userId", 
      "labelPath": "User/userId" 
    }, 
    { 
      "key": "DisplayName", 
      "valuePath": "userNav/displayName", 
      "labelPath": "User/displayName" 
    }, 
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
  "permissionsMetadata": [], 
  "rolePermissions": [ 
    { 
      "roleId": "115", 
      "permissions": [{ "permStringValue": "$_jobInfo_cost-center_read" }] 
    } 
  ] 
} 
```

### Job Information

| Job Information | Details |
| --- | --- |
| **Description** | Retrieves and displays the manager's directs job title, job code, job function, and job function type. A manager can also include a direct and job title in the prompt. |
| **Prompts** | <li>Show me job info for all my direct reports? </li><br><br><li>What is the job function type of my entire team? </li><br><br><li>Give me Job information for my direct reports? </li><br><br><li>What are the job titles of my direct reports? </li><br><br><li>What are my direct report job functions? </li><br><br><li>Get job data for <code>[EmployeeName]</code> </li><br><br><li>What is the job title of <code>[EmployeeName]</code>?</li> |
| **Response** | Here's the job information for your direct reports:  <br>**Manuela Torres**:<br><br><li><strong>Job Title</strong>: Software Engineer II</li><br><br><li> <strong>Job Code</strong>: 50071001</li><br><br><li> <strong>Job Function Type</strong>: DL</li><br><br><li> <strong>Job Function</strong>: 50070986 <br><br> <strong>Gerardo Palacios</strong>: </li><br><br><li><strong>Job Title</strong>: Software Engineer III </li><br><br><li><strong>Job Code</strong>: 50071001 </li><br><br><li><strong>Job Function Type</strong>: DL </li><br><br><li><strong>Job Function</strong>: 50070986<br><br><strong>Xiang	Tao</strong>: </li><br><br><li><strong>Job Title</strong>: CTO </li><br><br><li><strong>Job Code</strong>: 50070999 </li><br><br><li><strong>Job Function Type</strong>: MT </li><br><br><li><strong>Job Function</strong>: 50070905<br> If you need any further assistance, feel free to ask!</li> |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerJobInfo` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerJobInfo` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to `false`. `isContingentWorker` is to ensure only employees data are retrieved. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name</li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data</li><br><br><li><code>JobTitle</code>: Directs job title</li><br><br><li><code>JobCode</code>: Directs job code/positionNumber</li><br><br><li><code>JobFunctionType</code>: Directs job function type</li><br><br><li><code>JobFunction</code>: Directs job function</li> |

**Configuration**:

```json
{ 
  "scenario": "ManagerReadJobInfo", 
  "rootEntity": "EmpEmployment", 
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}'", 
  "requestEntities": [ 
    { 
      "key": "DisplayName", 
      "valuePath": "userNav/displayName", 
      "labelPath": "User/displayName" 
    }, 
    { 
      "key": "UserId", 
      "valuePath": "userNav/userId", 
      "labelPath": "User/userId" 
    }, 
    { 
      "key": "JobTitle", 
      "valuePath": "jobInfoNav/jobTitle", 
      "labelPath": "User/jobTitle" 
    }, 
    { 
      "key": "JobCode", 
      "valuePath": "jobInfoNav/jobCode", 
      "labelPath": "User/jobCode" 
    }, 
    { 
      "key": "JobFunctionType", 
      "valuePath": "jobInfoNav/jobCodeNav/jobFunctionNav/jobFunctionType", 
      "labelPath": "FOJobFunction/jobFunctionType" 
    }, 
    { 
      "key": "jobFunction", 
      "valuePath": "jobInfoNav/jobCodeNav/jobFunction", 
      "labelPath": "FOJobCode/jobFunction" 
    } 
  ], 
  "permissionsMetadata": [], 
  "rolePermissions": [ 
    { 
      "roleId": "115", 
      "permissions": [ 
        { 
          "permStringValue": "$_jobInfo_job-title_read" 
        }, 
        { 
          "permStringValue": "$_jobInfo_job-code_read" 
        } 
      ] 
    } 
  ] 
} 
```

##### Get specific employee/directs job information

This configuration is used when a directs name is filled with the manager's prompt. It includes a filter expression that filters on the different name fields trying to match it to what the manager included in the prompt

| Specific job Information | Details |
| --- | --- |
| **Template configuration** | `RSAPSuccessFactorsHCMGetManagerEmpNameJobInfo` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerEmpNameJobInfo` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to `false`. `isContingentWorker` is used to ensure only employees data are retrieved. Additionally, the expression filters on `firstName`, `lastName`, and `displayName` using the slot filled name from manager's query. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name </li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li><code>JobTitle</code>: Directs job title </li><br><br><li> <code>JobCode</code>: Directs job code/positionNumber </li><br><br><li><code>JobFunctionType</code>: Directs job function type </li><br><br><li><code>JobFunction</code>: Directs job function</li> |

**Configuration**:

```json
{ 
  "scenario": "ManagerReadEmpNameJobInfo", 
  "rootEntity": "EmpEmployment", 
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}' and (substringof(tolower('{name}'), tolower(userNav/firstName)) or substringof(tolower('{name}'), tolower(userNav/lastName)) or substringof(tolower('{name}'), tolower(userNav/displayName)))", 
  "requestEntities": [ 
    { 
      "key": "UserId", 
      "valuePath": "userNav/userId", 
      "labelPath": "User/userId" 
    }, 
    { 
      "key": "DisplayName", 
      "valuePath": "userNav/displayName", 
      "labelPath": "User/displayName" 
    }, 
    { 
      "key": "JobTitle", 
      "valuePath": "jobInfoNav/jobTitle", 
      "labelPath": "User/jobTitle" 
    }, 
    { 
      "key": "JobCode", 
      "valuePath": "jobInfoNav/jobCode", 
      "labelPath": "User/jobCode" 
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
  "permissionsMetadata": [], 
  "rolePermissions": [ 
    { 
      "roleId": "115", 
      "permissions": [ 
        { "permStringValue": "$_jobInfo_job-title_read" }, 
        { "permStringValue": "$_jobInfo_job-code_read" } 
      ] 
    } 
  ] 
} 
```

### Service Anniversary

| Service Anniversary | Details |
| --- | --- |
| **Description** | Retrieves the manager's directs hire date, calculates the service anniversary using the duration global variable and displays it. A manager can also include direct and job title in prompt. |
| **Prompts** | <li>When are the service anniversaries of all my direct reports? </li><br><br><li>What are the service anniversaries of my entire team? </li><br><br><li>Show me service anniversaries of my direct reports? </li><br><br><li>What is <code>[EmployeeName]</code>&#39;s next service anniversary assuming service anniversary duration is <code>[Duration]</code> years. </li><br><br><li>When is <code>[EmployeeName]</code>&#39;s <code>[Duration]</code> year service anniversary? </li><br><br><li>What is <code>[EmployeeName]</code>&#39;s Start/Hire Date? </li><br><br><li>When is <code>[EmployeeName]</code>&#39;s service anniversary? </li><br><br><li>Do any of my direct have a service anniversary next month?</li> |
| **Formula** | `If(DateDiff(Today(), DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)), TimeUnit.Years)) < 0, DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)) + Topic.Duration, TimeUnit.Years), DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)), TimeUnit.Years))`  <br>  <br>This PowerFX formula calculates the next service anniversary date for an employee based on their hire date and a specified duration. The formula follows these steps:  <br>  <br>1. `DateValue(userNav.hireDate)`  <br>Converts the employee's hire date to a date value  <br>  <br>2. `Year(Today()) - Year(DateValue(userNav.hireDate))`  <br>Calculates the number of years between the current year and the year of the employee's hire date  <br>  <br>3. `DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)), TimeUnit.Years)`  <br>Adds the calculated number of years to the hired date to determine the next anniversary date  <br>  <br>4. `DateDiff(Today(), DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)), TimeUnit.Years)) < 0`  <br>Checks if the calculated anniversary date is in the past  <br>  <br>5. `If(DateDiff(Today(), DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)), TimeUnit.Years)) < 0 `  <br>If the next anniversary date is in the past, it calculates the anniversary date for the next year by adding the specified duration `(Topic.Duration)` to the hire date.  <br>  <br>6. `DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)) + Topic.Duration, TimeUnit.Years)`Calculates the next anniversary date for the following year.  <br>  <br>7. `DateAdd(DateValue(userNav.hireDate), Year(Today()) - Year(DateValue(userNav.hireDate)), TimeUnit.Years)`  <br>If the anniversary date isn't in the past, it returns the calculated anniversary date for the current year |
| **Response** | Here are the service anniversaries for your direct reports:  <br>**Manuela Torres**:<br><br><li><strong>Hire date</strong>: 2014-01-01 </li><br><br><li><strong>Upcoming service anniversary date</strong>: 2025-12-31</li><br><br><li><strong>Upcoming milestone</strong>: 12 years  <br><br> <strong>Gerardo Palacios</strong>: </li><br><br><li><strong>Hire date</strong>: 2014-01-01 </li><br><br><li><strong>Upcoming service anniversary date</strong>: 2025-12-31</li><br><br><li><strong>Upcoming milestone</strong>: 12 years<br><br><strong>Xiang	Tao</strong>: </li><br><br><li><strong>Hire date</strong>: 2014-01-01 </li><br><br><li><strong>Upcoming service anniversary date</strong>: 2025-12-31</li><br><br><li><strong>Upcoming milestone</strong>: 12 years<br> If you need any further assistance, feel free to ask!</li> |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerServiceAnniversary` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerServiceAnniversary` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to false. `isContingentWorker` is to ensure only employees data are retrieved. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name </li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li><code>hireDate</code>: Directs hire date</li> |

**Configuration**:

```json
{ 
  "scenario": "ManagerReadServiceAnniversary", 
  "rootEntity": "EmpEmployment", 
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}'", 
  "requestEntities": [ 
    { 
      "key": "UserId", 
      "valuePath": "userNav/userId", 
      "labelPath": "User/userId" 
    }, 
    { 
      "key": "DisplayName", 
      "valuePath": "userNav/displayName", 
      "labelPath": "User/displayName" 
    }, 
    { 
      "key": "hireDate", 
      "valuePath": "userNav/hireDate", 
      "labelPath": "" 
    } 
  ], 
  "permissionsMetadata": [], 
  "rolePermissions": [ 
    { 
      "roleId": "115", 
      "permissions": [ 
        { "permStringValue": "$_employmentInfo_originalStartDate_read" } 
      ] 
    } 
  ] 
} 
```

#### Get specific employee/directs service anniversary

This configuration is used when a directs name is filled with the manager's prompt. It includes a filter expression that filters on the different name fields trying to match it to what the manager included in the prompt

| Specific service anniversary | Details |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerEmpNameServiceAnniversary` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerServiceAnniversary` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to `false`. `isContingentWorker` is used to ensure only employee data is retrieved. Additionally, the expression filters on `firstName`, `lastName`, and `displayName` using the slot filled name from manager's query |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name </li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data </li><br><br><li><code>hireDate</code>: Directs hire date</li> |

#### Configuration

```json
{ 
  "scenario": "ManagerReadEmpNameServiceAnniversary", 
  "rootEntity": "EmpEmployment", 
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}' and (substringof(tolower('{name}'), tolower(userNav/firstName)) or substringof(tolower('{name}'), tolower(userNav/lastName)) or substringof(tolower('{name}'), tolower(userNav/displayName)))", 
  "requestEntities": [ 
    { 
      "key": "UserId", 
      "valuePath": "userNav/userId", 
      "labelPath": "User/userId" 
    }, 
    { 
      "key": "DisplayName", 
      "valuePath": "userNav/displayName", 
      "labelPath": "User/displayName" 
    }, 
    { 
      "key": "hireDate", 
      "valuePath": "userNav/hireDate", 
      "labelPath": "" 
    } 
  ], 
  "permissionsMetadata": [], 
  "rolePermissions": [ 
    { 
      "roleId": "115", 
      "permissions": [ 
        { "permStringValue": "$_employmentInfo_originalStartDate_read" } 
      ] 
    } 
  ] 
} 
```

## SAP Successfactor manager write scenarios

Manager *write* topics are described as follows:

### 1. Get direct report data

Get manager's direct report data and picklist data if necessary, using `SuccessFactors System Get Common Execution`, which requires the following inputs:

**FilterParams**: The following example is for a user data request, but picklist data request follow the same rules for prepping the filterParams.

Example format used in Topic:

```json
"{""personIdExternalVal"": """ & Global.ESS_UserContext_Employee_Id & """,""userIdVal"": """ & Global.ESS_UserContext_User_Id & """}" 
```

Snippet of template configuration:

```json
{ 
  ... 
  "filter": "personIdExternal eq '{personIdExternalVal}' and userId eq '{userIdVal}'", 
  ... 
} 
```

The keys present in `filterParam` must match what is expected in the Template configuration. In the examples above, `personIdExternalVal` would be used as a key to insert `Global.ESS_UserContext_Employee_Id` into the filter expression.

**ScenarioName**: Configuration name, which is used by Dataverse call to get scenario configuration.

**userIdentifier**: User ID

`SuccessFactors System Get Common Execution` then returns a `ModelResponse` and `LabelResponse`, which are parsed for the user's data and stored in variables.

### 2. Confirm information

Present the manager directs current information asking for their confirmation to update or cancel to trigger the respective flow using either inline messaging or with an adaptive card.

### 3. Submit

If the manager submits their update, data is collected and used to call the `SuccessFactors System Update Common Execution`. This flow will `UPSERT` user data in `SuccessFactors` using the `OData` connector. `SuccessFactors System Update Common Execution` expects the following inputs:

**TargetUserId**: User ID **var\_requestParam**: An array of objects. Example format used in Topic:

```JSON
"[{""key"":""personIdExternalVal"", ""value"":"""&Global.ESS_UserContext_Employee_Id&"""},         {""key"":""countryVal"", ""value"":"""&First(Topic.var_parsedModel).country&"""},{""key"":""startDateVal"", ""value"":"""&DateDiff(Date(1970, 1, 1), First(Topic.var_parsedModel).startDate, TimeUnit.Seconds) * 1000&"""},{""key"":""genericString1Val"", ""value"":"""&Topic.id_raceAndEthnicity&"""}]" 
```

Snippet from Template configuration:

```JSON
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

The keys present in `var_requestParam` must match what is expected in the Template configuration. In the examples above, `personIdExternalVal` is used as a key to insert `Global.ESS_UserContext_Employee_Id` into the request body.

**var\_scenarioName**: Configuration name, which is used by Dataverse call to get scenario configuration.

If `SuccessFactors System Update Common Execution` succeeds, then copilot responds that the update was successful. If the update fails, the user gets a failure message.

#### Customizations

Customizations to the Template configuration generally require these changes:

**Adding fields to Get Config**:  
After adding field to template configuration, it must update the `modelResponse` parsing node schema.

[![Screenshot of the parse value field.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/parse-value.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/parse-value.png#lightbox)

[![Screenshot of the Edit schema definition window.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/edit-schema.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/edit-schema.png#lightbox)

[![A screenshot of a JSON with a highlighted LookUp function.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/adaptive-cards-fields.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/adaptive-cards-fields.png#lightbox)

The adaptive card "label" property is set by the value stored in the parsed label variable. The "value" property is set using the `var_veteranInfo` variable, which stores the parsed user data.

If another input type to be added to the adaptive card to collect data for another field, then use the following input control code:

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

After which, update the output binding schema with the string given in `id` property. In the previous example, `id` = `id_veteran` therefore the output binding schema must have a variable with the same name set with the correct data type, as shown:

```
kind: Record
properties:
  actionSubmitId: String
  id_challenged_veteran: String
  id_special_disabled_veteran: String
  id_veteran: String
```

[![Screenshot of the Edit the output binding schema.](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/output-binding-schema.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/output-binding-schema.png#lightbox)

##### Adding fields to update

After adding the new field to update configuration, it must be updated with the `var_requestParam` to include added field and the values to send to update with. Refer to the built-in `"write"` scenarios for further guidance to extend scenarios.

**Authorization**:

- Authorization is done using the `permissionsMetadata/rolePermission` that is part of the Template configuration. The `permissionsMetadata` and `User Id` are used to create the query string for `OData Connector in SuccessFactors Check User Permissions flow`. If `SuccessFactors Check User Permissions flow` doesn't find `permissionsMetadata` it runs `roleBased Permissions flow` using role permission and user roles variable.
- It's important to include `permissionMetadata` or `rolePermission` in template configuration file as there's no other authorization check if both of those fields are missing.

#### Cost Center

| Cost center | Details |
| --- | --- |
| **Description** | Retrieves the manager's directs current cost center, displays it, and then prompts manager to select a direct and input their new cost center with a start date. Manager can also include direct and job title in prompt. |
| **Prompts** | <li>Update cost center for <code>[EmployeeName]</code></li><br><br><li>I want to update <code>[EmployeeName]</code>&#39;s cost center?</li><br><br><li>I&#39;d like to update a team member&#39;s cost center to <code>[id_costCenter]</code></li><br><br><li>Update <code>[EmployeeName]</code>&#39;s cost center to <code>[id_costCenter]</code></li><br><br><li>Update cost center for my team</li> |

| Specific cost center | Details |
| --- | --- |
| **Description** | Retrieves the manager's directs current cost center, displays it, and then prompts manager to select a direct and input their new cost center with a start date. Manager can also include direct and job title in prompt, and it will be slot filled |
| **Prompts** | <li>Update cost center for <code>[EmployeeName]</code> </li><br><br><li>I want to update <code>[EmployeeName]</code>&#39;s cost center?</li><br><br><li>I&#39;d like to update a team member&#39;s cost center to <code>[id_costCenter]</code></li><br><br><li>Update <code>[EmployeeName]</code>&#39;s cost center to [id_costCenter]</li><br><br><li>Update cost center for my team.</li> |
| **Adaptive card** | <span class="mx-imgBorder"><br><a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/adaptive-card.png#lightbox" data-linktype="relative-path"><br><img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/adaptive-card.png" alt="A screenshot of an adaptive card in a chat experience." data-linktype="relative-path"><br></a><br></span> |

##### Get configurations - Cost center

Retrieve the existing cost center is the first step in the flow.

| Get configurations | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerCostCenter` |
| **Scenario name** | `sdyn_HRSAPSuccessFactorsHCMGetManagerCostCenter` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to `false`. `isContingentWorker` is used to ensure only employees data is retrieved. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name</li><br><br><li><code>UserId</code>: Directs userId, which is used in upsert to match data</li><br><br><li><code>CostCenterCode</code>: Directs cost center as an ID value</li><br><br><li><code>CostCenterName</code>: Directs Cost center as a name linked to ID value</li><br><br><li><code>Company</code>: Directs company code used to validate cost center submitted by manager.</li> |

**Configuration**:

```json
	
{
  "scenario": "ManagerReadCostCenter",
  "rootEntity": "EmpEmployment",
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}'",
  "requestEntities": [
    {
      "key": "UserId",
      "valuePath": "userNav/userId",
      "labelPath": "User/userId"
    },
    {
      "key": "DisplayName",
      "valuePath": "userNav/displayName",
      "labelPath": "User/displayName"
    },
    {
      "key": "CostCenterCode",
      "valuePath": "jobInfoNav/costCenter",
      "labelPath": "EmpJob/costCenter"
    },
    {
      "key": "CostCenterName",
      "valuePath": "jobInfoNav/costCenterNav/name",
      "labelPath": ""
    },
{
      "key": "Company",
      "valuePath": "jobInfoNav/company",
      "labelPath": "EmpJob/company"
    }
  ], 
  "permissionsMetadata": [],
  "rolePermissions": [
    {
      "roleId": "115",
      "permissions": [{ "permStringValue": "$_jobInfo_cost-center_read" }]
    }
  ]
}
```

#### Validate cost center

This configuration is used to validate the manager's entered cost center. After the manager submits the adaptive card, this configuration is used with the Get Common Orchestrator to query for the cost center and see if it exists under the company code the manager is in.

| Validate cost center | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMEmployeeValidateCostCenter` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeValidateCostCenter` |
| **Filter** | Filters on cost center code \(`externalCode`\) using `costCentervalue` and company code \(`cust_LegalEntity/externalCode`\) |
| **Values queried** | <li><code>CostCenterCode</code>: Cost center as an ID value </li><br><br><li> <code>CostCenterName</code>: Cost center as a name linked to ID value</li> |

**Configuration**:

```json


{
  "scenario": "ValidateCostCenter",
  "rootEntity": "FOCostCenter",
  "filter": "externalCode eq '{costCenterValue}' and cust_LegalEntity/externalCode eq '{companyCodeValue}'",
  "requestEntities": [
    {
      "key": "costCenterCode",
      "valuePath": "externalCode",
      "labelPath": ""
    },
    {
      "key": "costCenterName",
      "valuePath": "name",
      "labelPath": ""
    }
  ], 
  "permissionsMetadata": [],
  "rolePermissions": []
}
```

#### Update cost center

Updating the contact email

| Validate cost center | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMManagerUpdateCostCenter` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMManagerUpdateCostCenter` |
| **Request Body** | <li><code>userId</code>: User ID of the direct that&#39;s being updated</li><br><br><li><code>startDate</code>: Start date of when the change should take effect</li><br><br><li><code>costCenter</code>: New cost center ID input by manager.</li> |

**Configuration**

```json

{
        "scenario": "UpdateCostCenter",
        "requestBody": '{
            "__metadata": {
                "uri": "EmpJob"
            },
            "userId": "userIdVal",
            "startDate": "/Date(startDateVal)/",
            "costCenter": "costCenterVal"
        }',
        "permissionsMetadata": [{
                "permType": "DATA_MODEL",
                "permLongValue": -1,
                "permStringValue": "$_eventReason_DATACOST_write"
            }
        ],
        "rolePermissions": []
    }
```

#### Job Title

| Job Title | Description |
| --- | --- |
| **Description** | Retrieves the managers directs current job titles, displays it, and then prompts manager to select a direct and input their new title with a start date. Manager can also include direct and job title in prompt. |
| **Prompts** | <li>I want to change the job title for <code>[EmployeeName]</code></li><br><br><li>Update <code>[EmployeeName]</code>&#39;s job title to <code>[newJobTitle]</code></li><br><br><li>Can I change the job title of my team member?</li><br><br><li>I&#39;d like to change <code>[EmployeeName]</code>&#39;s job title</li><br><br><li>Update job title for my direct reports</li><br><br><li>Change job title of my team member to <code>[newJobTitle]</code>?</li> |
| **Adaptive Card** | <span class="mx-imgBorder"><br><a href="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/adaptive-card.png#lightbox" data-linktype="relative-path"><br><img src="https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/media/adaptive-card.png" alt="A screenshot of an adaptive card in a chat experience." data-linktype="relative-path"><br></a><br></span> |
|  |  |

#### Get configurations - Job information

Retrieving the existing job information is the first step in the flow

| Get configurations | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMGetManagerJobInfo` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMGetManagerJobInfo` |
| **Filter** | Filters on `personIdExternal` using `ESS_UserContext_Employee_Id`, `userId` using `ESS_UserContext_User_Id`, and `isContingentWorker` set to `false`. `isContingentWorker` is used to ensure only employees data is retrieved. |
| **Values queried** | <li><code>DisplayName</code>: Directs current preferred name</li><br><br><li><code>UserId</code>: Directs <code>userId</code> which is used in upsert to match data.</li><br><br><li><code>JobTitle</code>: Directs job title</li><br><br><li><code>JobCode</code>: Not used in this Topic but is queried because the template configuration Manager Read Job Info is reused here</li><br><br><li><code>JobFunctionType</code>: Not used in this topic but is queried because the template configuration Manager Read Job Info is reused here</li><br><br><li><code>JobFunction</code>: Not used in this topic but is queried because the template configuration Manager Read Job Info is reused here</li> |

**Configuration**:

```json

	{
  "scenario": "ManagerReadJobInfo",
  "rootEntity": "EmpEmployment",
  "filter": "isContingentWorker eq {isContingentWorkerValue} and userNav/manager/empInfo/personIdExternal eq '{personIdExternalVal}' and userNav/manager/empInfo/userId eq '{userIdVal}'",
  "requestEntities": [
    {
      "key": "DisplayName",
      "valuePath": "userNav/displayName",
      "labelPath": "User/displayName"
    },
    {
      "key": "UserId",
      "valuePath": "userNav/userId",
      "labelPath": "User/userId"
    },
    {
      "key": "JobTitle",
      "valuePath": "jobInfoNav/jobTitle",
      "labelPath": "User/jobTitle"
    },
    {
      "key": "JobCode",
      "valuePath": "jobInfoNav/jobCode",
      "labelPath": "User/jobCode"
    },
    {
      "key": "JobFunctionType",
      "valuePath": "jobInfoNav/jobCodeNav/jobFunctionNav/jobFunctionType",
      "labelPath": "FOJobFunction/jobFunctionType"
    },
    {
      "key": "jobFunction",
      "valuePath": "jobInfoNav/jobCodeNav/jobFunction",
      "labelPath": "FOJobCode/jobFunction"
    }
  ],
  "permissionsMetadata": [],
  "rolePermissions": [
    {
      "roleId": "115",
      "permissions": [
        {
          "permStringValue": "$_jobInfo_job-title_read"
        },
        {
          "permStringValue": "$_jobInfo_job-code_read"
        }
      ]
    }
  ]
}
```

#### Update job title

Updating the job title

| Job Title | Description |
| --- | --- |
| **Template configuration** | `HRSAPSuccessFactorsHCMManagerUpdateJobTitle` |
| **Scenario name** | `msdyn_HRSAPSuccessFactorsHCMEmployeeUpdatePreferredName` |
| **Request Body** | <li><code>userId</code>: User ID of direct that&#39;s being updated</li><br><br><li><code>startDate</code>: Start date of when the change should be effective gathered from manager</li><br><br><li><code>jobTitle</code>: New job title gathered from manager</li> |

##### Configuration

```
        "scenario": "UpdateJobTitle",
        "requestBody": '{
            "__metadata": {
                "uri": "EmpJob"
            },
            "userId": "userIdVal",
            "startDate": "/Date(startDateVal)/",
            "jobTitle": "jobTitleVal"
        }',
        "permissionsMetadata": [{
                "permType": "DATA_MODEL",
                "permLongValue": -1,
                "permStringValue": "$_eventReason_JOBTITLE_write"
            }
        ],
        "rolePermissions": []
}
```
