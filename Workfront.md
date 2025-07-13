
# Integration of Adobe Workfront Fusion with AEM Forms Submission

**Last updated:** July 13, 2025

* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** Workfront Fusion Integration, AEM Forms, Adaptive Forms, Integration
* **Audience:** Admin, Developer, Business User

## Overview

This enhanced documentation provides comprehensive guidance for implementing Adobe Experience Manager Forms integration with Workfront Fusion, combining insights from both the original documentation and video analysis to deliver actionable, step-by-step instructions.

## Prerequisites

Before you begin, ensure you have:

**Last updated:** Sun Jul 13 2025 16:10:17 GMT+0000 (Coordinated Universal Time)
*   **Licenses:** A valid Workfront and Workfront Fusion license is required.
*   **AEM Access:** An AEM user account with the necessary permissions to access the Developer Console and retrieve service credentials.
*   **Technical Account Membership:** The Technical Account used for the integration *must* be a member of the `forms-users` group within Workfront. Failure to do so will prevent webhook creation.
*   **Network Connectivity:** Stable network connectivity between the AEM Forms instance and the Workfront Fusion service.
*   **Administrative Privileges:** Administrative access to both AEM Forms and Workfront Fusion is highly recommended for configuration and troubleshooting.
*   **Understanding of Concepts:** A solid understanding of AEM Forms and Workfront Fusion concepts, including Adaptive Forms, scenarios, webhooks, and data models.
*   **SSL Certificates:** Valid SSL certificates for secure communication between AEM Forms and Workfront Fusion.
*   **API Keys & Authentication:** API keys and authentication credentials (Client ID, Client Secret, Technical Account ID, Org ID, Meta Scopes, Private Key) obtained from the Adobe Developer Console.  These are essential for establishing a secure connection.
*   **Adobe Developer Console Access:** Access to the Adobe Developer Console ([[https://developer.adobe.com/console](https://developer.adobe.com/console](https://developer.adobe.com/console](https://developer.adobe.com/console))) to retrieve the necessary service credentials.
*   **JSON Data Format Knowledge:** Familiarity with JSON data formats and webhook configurations, as data is typically exchanged in this format.
*   **Network Access:** Network access to required Adobe services and endpoints.
*   **Firewall and Security Configuration:** Proper firewall and security configurations to allow communication between AEM Forms and Workfront Fusion.
*   **AEM Forms Version:** AEM Forms as a Cloud Service version 6.5 or later.
*   **Workfront Fusion Version:** Workfront Fusion version 2023.1 or later.
*   **Compatible Browser:** A compatible browser such as Chrome, Firefox, or Edge is recommended.
*   **AEM Forms Administrator Role:** The AEM user needs the AEM Forms Administrator role or equivalent permissions to edit and publish Adaptive Forms.
*   **Workfront Fusion Integration Specialist Role:** The Workfront Fusion user needs the Workfront Fusion Integration Specialist role or equivalent permissions to create and configure scenarios.

## Implementation Steps

```markdown

# Integration of Adobe Workfront Fusion with AEM Forms Submission
**Last updated:** Sun Jul 13 2025 16:10:17 GMT+0000 (Coordinated Universal Time)


This document details how to integrate Adobe Workfront Fusion with AEM Forms to automate form submission processing. This integration allows for seamless transfer of form submissions data to Workfront Fusion workflows, enabling automation of tasks such as initiating projects, assigning tasks, sending notifications, and updating project statuses.


## Prerequisites

Before proceeding, ensure 
*   **Licenses:** A valid Workfront and Workfront Fusion license is required.
*   **AEM Access:** An AEM user account with the necessary permissions to access the Developer Console and retrieve service credentials.
*   **Technical Account Membership:** The Technical Account used for the integration *must* be a member of the `forms-users` group within Workfront. Failure to do so will prevent webhook creation.
*   **Network Connectivity:** Stable network connectivity between the AEM Forms instance and the Workfront Fusion service.
*   **Administrative Privileges:** Administrative access to both AEM Forms and Workfront Fusion is highly recommended for configuration and troubleshooting.
*   **Understanding of Concepts:** A solid understanding of AEM Forms and Workfront Fusion concepts, including Adaptive Forms, scenarios, webhooks, and data models.
*   **SSL Certificates:** Valid SSL certificates for secure communication between AEM Forms and Workfront Fusion.
*   **API Keys & Authentication:** API keys and authentication credentials (Client ID, Client Secret, Technical Account ID, Org ID, Meta Scopes, Private Key) obtained from the Adobe Developer Console.  These are essential for establishing a secure connection.
*   **Adobe Developer Console Access:** Access to the Adobe Developer Console ([[https://developer.adobe.com/console](https://developer.adobe.com/console](https://developer.adobe.com/console](https://developer.adobe.com/console))) to retrieve the necessary service credentials.
*   **JSON Data Format Knowledge:** Familiarity with JSON data formats and webhook configurations, as data is typically exchanged in this format.
*   **Network Access:** Network access to required Adobe services and endpoints.
*   **Firewall and Security Configuration:** Proper firewall and security configurations to allow communication between AEM Forms and Workfront Fusion.
*   **AEM Forms Version:** AEM Forms as a Cloud Service version 6.5 or later.
*   **Workfront Fusion Version:** Workfront Fusion version 2023.1 or later.
*   **Compatible Browser:** A compatible browser such as Chrome, Firefox, or Edge is recommended.
*   **AEM Forms Administrator Role:** The AEM user needs the AEM Forms Administrator role or equivalent permissions to edit and publish Adaptive Forms.
*   **Workfront Fusion Integration Specialist Role:** The Workfront Fusion user needs the Workfront Fusion Integration Specialist role or equivalent permissions to create and configure scenarios.


## Step-by-Step Instructions


### 1. **Creating a Workfront Fusion Scenario

**Objective**** To create a Workfront Fusion scenario to automate form submission processing.

**Actions:**

1. **Sign into your [Workfront Fusion account](https**//).
2. **Click `Scenarios` in the left panel.
3.  Click `Create a new scenario` in the upper-right corner of the page.
4.  Select `New scenario` in the upper-left corner and type a proper name for the scenario (e.g., "[Scenario Name]").
5.  Click the question mark icon and ensure you add the first module as `AEM Forms`.
6.  Select the `Watch for Form Events` dialog box.


### 2. Adding a Webhook

**Objective**** To add a webhook to the Workfront Fusion scenario.

**Actions:**

1. **Click `Add` in the `Watch for Form Events` dialog box. A dialog box to add a webhook appears.
2.  Specify a webhook name (e.g., "[Webhook Name]").  *Note** Choose your webhook name carefully, as it will appear in the AEM Forms submit action drop-down list. Changing it later will not reflect in AEM.*
3. **Click `Add` to add a new connection. The `Create a Connection` dialog box appears.


### 3. Adding a Connection to a Webhook

**Objective**** To configure the connection details for the webhook.

**Actions:**

1. **Specify a `Connection Name` in the `Create a Connection` dialog box.
2.  Select `Environment` and `Type` from the drop-down list.
3.  Enter the `Instance URL`.
4.  Replace `ims-na1.adobelogin.com` in the `IMS endpoint` with the value of `imsEndpoint` from the service credentials in the Developer console.
5.  Retain the `[https**//`](https://`) in the `IMS endpoint` textbox while adding the `imsEndpoint` URL.
6. **Specify     *   `Client ID` with the value of `clientId` from the service credentials in the Developer console.
    *   `Client Secret` with the value of `clientSecret` from the service credentials in the Developer console.
    *   `Technical Account ID` with the value of `id` from the service credentials in the Developer console.
    *   `Org ID` with the value of `org` from the service credentials in the Developer console.
    *   `Meta Scopes` with the value of `metascopes` from the service credentials in the Developer console.
    *   `Private Keys` with the value of `privateKey` from the service credentials in the Developer console.
7.  For `Private Key`, remove `\r\n` from its value. For example, if the private key value is `\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`, then after removing the `\r\n` from the private key, the key would look like 8.  You also have the option to retrieve a private key or certificate from the file by selecting the `Extract` button.
9.  Click `Continue`.
10. Select the created connection from the drop-down list in the `Add a webhook` dialog box.
11. Click `Save`.
12. Click `OK` and save the changes for the scenario.
13. To activate the scenario, click the ON/OFF toggle button in the scenario editor.


### 4. Configuring Submit Action of an Adaptive Form for Workfront Fusion

**Objective**** To configure the submit action of an Adaptive Form to invoke the created Workfront Fusion scenario.

**Actions (New Adaptive Form):**

1. **Log in to your AEM instance.
2.  Go to `Forms > Forms and Documents > Create > Adaptive Form`. The `Create Form` wizard appears.
3.  Select an Adaptive Form template from the `Source` tab.
4.  Select a theme from the `Style` tab.
5.  Select `Invoke a WorkFront Fusion Scenario` from the `Submission` tab.
6.  Select the created webhook from the `Options` tab in the `Properties` window.
7.  Click `Create`.
8.  Specify the name for your new Adaptive Form and click `Create`.

**Actions (Existing Adaptive Form)****

1. **Log in to your AEM instance.
2.  Go to `Forms > Forms and Documents`.
3.  Select an Adaptive Form and open the form in an edit mode.
4.  Open the Content browser, and select the `Guide Container` component of your Adaptive Form.
5.  Click the Guide Container properties icon. The Adaptive Form Container dialog box opens.
6.  Open the `Submission` tab.
7.  Select the `Submit action` as `Invoke a WorkFront Fusion Scenario`.
8.  Select `Workfront Fusion scenario` from the drop-down list.
9.  Click `Done`.


### 5. Testing the Integration

**Objective**** Verify that the Adaptive Form submission triggers the Workfront Fusion scenario and that the actions are executed correctly.

**Actions:**

1. **Submit a test form through the Adaptive Form.
2.  In Workfront Fusion, monitor the scenario execution logs to confirm that the trigger fired and the actions were executed successfully.
3.  Verify that the expected outcome (e.g., Workfront task creation) occurred.


## Next Steps

*   Review the [video tutorial](https**//video.tv.adobe.com/v/3427145/adaptive-forms-adobe-workfront-af-workfront-workfront-aem-forms/?quality=12&learn=on) for a visual demonstration.
*   Consult the provided support and resources for further assistance:
    *   [Send email](https://)
    *   [Submit to SharePoint Document Library](https://)
    *   [Submit to SharePoint List](https://)
    *   [Submit using Form Data Model](https://)
    *   [Submit to Azure Blob Storage](https://)
    *   [Submit to REST endpoint](https://)
    *   [Submit to OneDrive](https://)
    *   [Invoke an AEM Workflow](https://)
    *   [Submit to Power Automate](https://)
    *   [Submit to Workfront Fusion](https://)
    *   [Connect Adaptive Form to Salesforce application](https://)
    *   [Connect an Adaptive Form to Microsoft® Dynamics](https://)
    *   [Connect an Adaptive Form to Adobe Marketo Engage](https://)
    *   [Create custom submit action](https://)
*   Refer to [[https://experienceleague.adobe.com/docs/aem-forms/latest/integrations/workfront-fusion.html](https://experienceleague.adobe.com/docs/aem-forms/latest/integrations/workfront-fusion.html](https://experienceleague.adobe.com/docs/aem-forms/latest/integrations/workfront-fusion.html](https://experienceleague.adobe.com/docs/aem-forms/latest/integrations/workfront-fusion.html)) for detailed documentation.
```

## Related Links

* **Original Documentation:** https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/submit-adaptive-form-to-workfront-fusion
* **Adobe Experience League:** https://experienceleague.adobe.com
* **Adobe Developer Console:** https://developer.adobe.com/console
* **Adobe Support:** https://helpx.adobe.com

## Additional Resources

* **Adobe Documentation:** https://docs.adobe.com
* **Community Forums:** https://experienceleaguecommunities.adobe.com
* **Training Resources:** https://learning.adobe.com

---
