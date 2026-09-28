<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/scenarios/deploy-sap-netweaver -->
<!-- Sitemap-Last-Modified: 2025-04-09 -->

# Deploy SAP NetWeaver AS ABAP 7.51

This document guides you in setting up a lab environment with SAP ECC for testing.

## Deploying SAP NetWeaver AS ABAP 7.51 on ASE test environment from the SAP Cloud Appliance Library

1. Navigate to the SAP Cloud Appliance Library: [https://cal.sap.com/](https://cal.sap.com/).
2. Create an account for yourself in the SAP CAL and log in to the SAP Cloud Appliance Library. [https://calstatic.hana.ondemand.com/res/docEN/042bb15ad2324c3c9b7974dbde389640.html](https://calstatic.hana.ondemand.com/res/docEN/042bb15ad2324c3c9b7974dbde389640.html)
3. Navigate to the [Appliance Templates - SAP Cloud Appliance Library](https://cal.sap.com/console/tenant_QMOV0I8VZP4H#/applianceTemplates) page
4. Search for the **7.51** appliance template and click the Create Appliance button to create a **SAP NetWeaver AS ABAP 7.51 SP02 on ASE** appliance.

[![Screenshot of SAP Appliance Templates.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-1.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-1.png#lightbox)

5. Choose Create a new account. Using the **Standard Authorization for Authorization** Type requires the following permissions: The standard authorization includes permissions to create and manage appliances. The roles required by the Microsoft Azure user who grants permissions to SAP Cloud Appliance Library are:

- Option 1: An administrator of the subscription, that is, your user has the role Owner and has access to scope /subscriptions/.
- Option 2: Your Microsoft Azure user has the roles Contributor and User Access Administrator and has access to scope /subscriptions/. You must also have the role of Global Administrator for the Azure Active Directory. Using the **Authorization with Application** for Authorization Type requires you to manually register an application in your Azure AD tenant and grant it the Contributor role to your subscription. You must create an application registration and assign the role Contributor to the corresponding application for your subscription. In this guide, we'll use **Authorization with Application**.

6. Click the Test Connection button. Enter the name of your appliance and choose a master password to access your SAP instance. Click Create to provision resources into Azure AD tenant
7. Download and store the private key needed to access the appliance.

[![Screenshot of private key generation.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-5.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-5.png#lightbox)

8. SAP CAL will start provisioning and activating resources into your subscription. It may take up to several hours to complete.
9. The next step is to log on into the SAP GUI, get a developer license, and install it to be able to save packages and update the SAP instance, e.g., publish a web service. Once you create the appliance in the SAP Cloud Appliance Library, the SAP system generates a temporary license key that is sufficient to log on to the system. As a first step, before using the system, you need to install a Minisap license as described in the Community Wiki page: How to request and install Minisap license keys.

Installing the Minisap license changes the installation number from INITIAL to DEMOSYSTEM. The developer access key for user DEVELOPER and installation number DEMOSYSTEM is already in the system, and you can start developing in the customer's name range \(Z\*, Y\*\).

## Exposing a Web Service for the SAP ECC 7.51 Connector

The Web Service Configuration Tool discovers the Web service through WSDL \(Web Services Description Language\) and retrieves its services, endpoints, and operations \(BAPIs\) it provides. Services, endpoints, and operations \(BAPIs\) are used by the Web Service Connector to access the SAP server and manipulate identities with Microsoft Identity Manager \(MIM\) 2016.

For a web service to be discovered, it must be exposed in SAP ECC 7.51. This article describes the process of exposing the web service from SAP ECC 7.51 workbench.

Log in to SAP ECC 7 and enter the ABAP workbench using Transaction Code SE80. This opens the Object Navigator screen, where you maintain different SAP application components like packages, viewing function groups, BSP programs, etc.

To create a web service utilized by Web Service Configuration Tool, you must first create a package so that all the objects can easily navigate through different systems.

1. From the dropdown, select Package, give the new package a name and press enter. The following screen appears if the object is not available in the system. Click Yes to proceed with the package creation.

[![Screenshot of create pack.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-7.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-7.png#lightbox)

2. Provide the required details with the **Create Package** screen and click the Create button. You can choose to specify the Application Component. This action restricts the scope of object created only to the application \(SAP module, for ex: ABAP, MM, PS, LW, etc.\) specified. Note: It's recommended that you don't specify the application component that makes the object global.

[![Screenshot of package creation.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-8.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-8.png#lightbox)

3. The system prompts for a transport request. Click the button next to Request to generate a new transport request.

[![Screenshot of request prompt.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-9.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-9.png#lightbox)

4. Create a new local request.

[![Screenshot of Workbench request.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-10.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-10.png#lightbox)

5. Double click on request name \(NPL\*\) to select it.

[![Screenshot of NPL.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-11.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-11.png#lightbox)

6. After workbench request is selected, click the Create button to create a package.

[![Screenshot of request creation.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-12.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-12.png#lightbox)

7. Once the package is created, under Object Name, to start creating the web service, right-click on the Package name, and select Create -> Enterprise Service

[![Screenshot of object navigator.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-13.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-13.png#lightbox)

8. The screen to select Object Type is displayed. Select Service Provider as object type and click Continue.

[![Screenshot of object type creation.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-14.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-14.png#lightbox)

9. On the Kind of Service Provider screen, select Existing ABAP Objects \(Inside Out\) and press Continue. With inside out you start at the backend with an existing application and enable the service for a particular functionality. It means that you start with the implementation and move out towards the interface.

[![Screenshot of Kind of Service Provider.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-15.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-15.png#lightbox)

10. Provide the Service Definition name and description for the selected Object Type. Click Continue.

[![Screenshot of service definition.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-16.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-16.png#lightbox)

11. On the Endpoint Type screen, select Function Group and press Continue. You must choose Function Group since the Web Service configuration tool for MIM requires a single URL for all the selected BAPIs.

[![Screenshot of endpoint type.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-17.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-17.png#lightbox)

12. On the Endpoint Function Group screen, select the required Function Group name, and press Continue. The function group chosen in the example is already defined and encapsulates the BAPIs related to users.

[![Screenshot of endpoint function group.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-18.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-18.png#lightbox)

13. On the Function Group screen, select all the required BAPIs and add the BAPIs that aren't included in the function group. Click Continue. In this example, all BAPIs from SU\_USER function groups are selected. Consult your SAP administrator regarding the BAPIs to be used in your project.

[![Screenshot of function group.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-19.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-19.png#lightbox)

To implement basic user management scenarios, you may want to limit a list of BAPIs published to:

- BAPI\_USER\_GETLIST
- BAPI\_USER\_GETDETAILS
- BAPI\_USER\_CREATE1
- BAPI\_USER\_DELETE
- BAPI\_USER\_CHANGE

14. On the **Configure Service** screen, choose a profile for Security Settings. There are four profiles defined by SAP for selection. Select one profile as per requirement.

- Authentication with Certificates and Transport Guarantee
- Authentication with User and Password, No Transport Guarantee
- Authentication with User and Password and Transport Guarantee
- No Authentication and No Transport Guarantee

15. In this example, we use Authentication with User and Password and no Transport Guarantee \(no HTTPs\) option. Click Continue.

[![Screenshot of configure service.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-20.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-20.png#lightbox)

16. On the Transport screen, click on the icon next to Request/Task name, and select your Local Workbench request. Click Continue.

[![Screenshot of transport.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-21.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-21.png#lightbox)

17. On the **Finish** screen, click Complete button.

[![Screenshot of the finish screen.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-22.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-22.png#lightbox)

18. After the Web Service is created, you must change the Profile settings of the Service definition. Under Configuration Tab, select Stateful communication properties, and activate Stateful profile. Click the Save button \(diskette icon\) in the toolbar.

[![Screenshot of profile change.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-23.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-23.png#lightbox)

19. In the Repository Browser expand the ZSAPCONNECTORWS package, right click on the ZSAPCONNECTORWEBSERVICE service definition, and select Activate.

[![Screenshot of ZSAPCONNECTORWEBSERVICE service definition.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-24.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-24.png#lightbox)

## Configuring Web Service using SOA Manager

Follow the steps below to configure the Web Service.

1. Open the Transaction SOAMANAGER. Navigate to the Technical Administration tab and click SAP Client Settings.

[![Screenshot of technical administration.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-25.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-25.png#lightbox)

2. Expand the Web Service Navigator tray and enter a hostname of your SAP server and port number. Click Save.

[![Screenshot of host and port.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-26.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-26.png#lightbox)

3. Click Back and Navigate to Service Administration tab. Select Web Service Configuration link.

[![Screenshot of web service configuration.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-27.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-27.png#lightbox)

4. In the Object Name input field, type ZSAPCONNECTORWEBSERVICE and click Search.

[![Screenshot of search results.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-28.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-28.png#lightbox)

5. Click to select ZSAPCONNECTORWEBSERVICE Service Definition.
6. On the Configurations tab, click Create Service button.

[![Screenshot of configuration create service.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-29.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-29.png#lightbox)

7. On Configuration of New Binding for Service Definition page, enter the Service Name, the New Binding Name and click Next.

[![Screenshot of binding for service definition.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-30.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-30.png#lightbox)

8. On the Provider Security page, select the User ID/Password under Transport Channel Authentication, and click Next.

[![Screenshot of binding for service definition configuration.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-31.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-31.png#lightbox)

9. On the SOAP Protocol page, leave all settings by default, and click Next.

[![Screenshot of SOAP protocol page.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-32.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-32.png#lightbox)

10. On the Operation Settings page, click Finish.

[![Screenshot of operation settings finish screen.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-33.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-33.png#lightbox)

11. Once the Service is created click on web page icon to open WSDL generation parameters.

[![Screenshot of WSDL parameters.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-34.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-34.png#lightbox)

Configure WSDL Flavors as:

- WSP Version: No Policy
- SOAP Version: SOAP 1.1
- SOAP Style: Document
- WSDL Section: AllInOne

12. Click to save WSDL Flavor as: SOAP 1.1. Only

[![Screenshot of save.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-35.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-35.png#lightbox)

13. Find a WSDL URL for Service under WSDL Generation section and copy that link. Example: `http://vhcalnplci.dummy.nodomain:8000/sap/bc/srt/wsdl/flv\_10002A1011D1/bndg\_url/sap/bc/srt/rfc/sap/zsapconnectorwebservice/001/zsapconnectorws/zsapconnectorws?sapclient\=001`

[![Screenshot of WSDL URL.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-36.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-36.png#lightbox)

## Activating Web Service for SAP ECC 7.51 Connector

1. Log in to SAP ECC 7 and enter the ABAP workbench using Transaction Code SICF. Mention Hierarchy Type as Service and click Execute button.

[![Screenshot of hierarchy type.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-37.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-37.png#lightbox)

2. On the **Define Services** page, type ZSAPCONNECTORWS Service Name, and click Apply.
3. Select the ZSAPCONNECTORWS service and choose Activate Service.

[![Screenshot of activate service.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-38.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-38.png#lightbox)

4. Confirm Activation of ICF Service. Click Yes.

[![Screenshot of confirm activation.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-39.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-39.png#lightbox)

5. On the **Define Services** page, type WSDL Service Name, and click Apply. Choose to Activate Service for both WSDL services.

[![Screenshot of active services.](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-40.png)](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/media/deploy-sap-netweaver/sap-40.png#lightbox)

6. Test the web service deployed using your favorite SOAP client tool to ensure that it does return proper data before configuring the Web Services Connector Template

## Connecting to Web Service from MIM or the ECMA2Host machine

1. To avoid publishing your SAP Web Service endpoint to the Internet, set up peering between your SAP demo lab network and your MIM or ECMA2Host machine. This setup allows you to reach your Web Service by its internal IP address.
2. Add the SAP host name and IP address into the hosts file on MIM or ECMA2Host machine.
3. Test opening the WSDL URL on the MIM or ECMA2Host machine from a browser to check connectivity to SAP Web Service.

The next step is to create a [webservice connector template](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/sap-template) to manage SAP ECC users using this SOAP endpoint and BAPIs published.

## Next steps

- [Migrate identity management scenarios from SAP IDM to Microsoft Entra](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/migrate-from-sap-idm)
- [Author SAP ECC 7 Template for ECMA2Host](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/sap-template)
- [Configuring Microsoft Entra ID to provision users into SAP ECC with NetWeaver AS ABAP 7.0 or later](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/on-premises-sap-connector-configure)
