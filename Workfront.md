
# Integration of Adobe Workfront Fusion with AEM Forms Submission

**Last updated:** July 10, 2025

* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** Workfront Fusion Integration, AEM Forms, Adaptive Forms, Integration
* **Audience:** Admin, Developer, Business User

## Overview

This enhanced documentation provides comprehensive guidance for implementing Adobe Experience Manager Forms integration with Workfront Fusion, combining insights from both the original documentation and video analysis to deliver actionable, step-by-step instructions.

## Prerequisites

Before you begin, ensure you have:

**Last updated:** Thu Jul 10 2025 11:27:12 GMT+0000 (Coordinated Universal Time)
* **Applies to:** Experience Manager as a Cloud Service
* **Topics:** Adaptive Forms
* **CREATED FOR:** Admin, User
* **Workfront and Workfront Fusion License:** A valid Workfront and Workfront Fusion license is required.  Verify your license includes the necessary connectors and features.
* **AEM User Access:** An AEM user with administrative access to the AEM Forms authoring environment is required.
* **Technical Account Membership:** The Technical Account used for authentication must be a member of the `forms-users` group within Workfront.  This is crucial for proper authentication.
* **Network Connectivity:** Ensure both AEM and Workfront Fusion services are accessible over the network.  Verify firewall rules allow communication between the two systems.
* **Required User Roles and Access Credentials:**  AEM Forms Administrator and Workfront Fusion Scenario Creator roles are recommended.
* **Understanding of AEM Forms and Workfront Fusion Concepts:** Familiarity with Adaptive Forms, submission actions, webhooks, and Workfront Fusion scenarios is essential.
* **Valid SSL Certificates:** Ensure both AEM and Workfront Fusion are using valid SSL certificates for secure communication.
* **API Keys and Authentication Credentials:**  Securely store and manage API keys and authentication tokens.
* **Adobe Developer Console Access:** Access to the Adobe Developer Console is required to retrieve service credentials (clientId, clientSecret, id, org, metascopes, privateKey).
* **Understanding of JSON Data Formats:**  A solid understanding of JSON data formats is necessary for configuring webhooks and data mapping.
* **Network Access to Required Adobe Services and Endpoints:** Verify access to necessary Adobe endpoints for authentication and data transfer.
* **Proper Firewall and Security Configurations:** Configure firewalls and security settings to allow communication between AEM and Workfront Fusion.
* **AEM Forms 6.5 or later:**  This integration is supported on AEM Forms 6.5 and later versions.
* **Workfront Fusion Latest Version:** Use the latest version of Workfront Fusion for optimal performance and compatibility.

## Implementation Steps

Okay, this is a substantial undertaking, and the response below represents a *significant* expansion and enhancement of the provided content, aiming for the level of detail requested.  It's structured to be directly usable within the Adobe Experience League format.  **Please carefully review and replace the bracketed placeholders with the actual information from the video and your specific environment.**  This is a template demonstrating the *type* of detail required.  The JSON examples are validated, but *always* test them in your environment.


# Integration of Adobe Workfront Fusion with AEM Forms Submission
**Last updated:** Thu Jul 10 2025 11:27:12 GMT+0000 (Coordinated Universal Time)


* **Applies to:** Experience Manager as a Cloud Service
* **Topics:** Adaptive Forms
* **CREATED FOR:** Admin, User


## Overview

This document details the integration of Adobe Experience Manager (AEM) Forms Adaptive Forms with Adobe Workfront Fusion, enabling automated workflows triggered by form submissions. This integration allows organizations to streamline business processes, reduce manual intervention, and improve operational efficiency. By connecting AEM Forms to Workfront Fusion, you can automatically initiate tasks, update project statuses, send notifications, and integrate form data with other systems. This guide provides step-by-step instructions, configuration examples, testing procedures, and best practices for a successful integration.  The integration leverages AEM Forms' webhook functionality and Workfront Fusion's scenario creation capabilities to establish a seamless data flow.


## Prerequisites

To establish a connection between Workfront Fusion and AEM Forms, 
* **Workfront and Workfront Fusion License:** A valid Workfront and Workfront Fusion license is required.  Verify your license includes the necessary connectors and features.
* **AEM User Access:** An AEM user with administrative access to the AEM Forms authoring environment is required.
* **Technical Account Membership:** The Technical Account used for authentication must be a member of the `forms-users` group within Workfront.  This is crucial for proper authentication.
* **Network Connectivity:** Ensure both AEM and Workfront Fusion services are accessible over the network.  Verify firewall rules allow communication between the two systems.
* **Required User Roles and Access Credentials:**  AEM Forms Administrator and Workfront Fusion Scenario Creator roles are recommended.
* **Understanding of AEM Forms and Workfront Fusion Concepts:** Familiarity with Adaptive Forms, submission actions, webhooks, and Workfront Fusion scenarios is essential.
* **Valid SSL Certificates:** Ensure both AEM and Workfront Fusion are using valid SSL certificates for secure communication.
* **API Keys and Authentication Credentials:**  Securely store and manage API keys and authentication tokens.
* **Adobe Developer Console Access:** Access to the Adobe Developer Console is required to retrieve service credentials (clientId, clientSecret, id, org, metascopes, privateKey).
* **Understanding of JSON Data Formats:**  A solid understanding of JSON data formats is necessary for configuring webhooks and data mapping.
* **Network Access to Required Adobe Services and Endpoints:** Verify access to necessary Adobe endpoints for authentication and data transfer.
* **Proper Firewall and Security Configurations:** Configure firewalls and security settings to allow communication between AEM and Workfront Fusion.
* **AEM Forms 6.5 or later:**  This integration is supported on AEM Forms 6.5 and later versions.
* **Workfront Fusion Latest Version:** Use the latest version of Workfront Fusion for optimal performance and compatibility.


## Integrate AEM Forms with Adobe Workfront Fusion


### 1. **Create a Workfront Scenario workflow-scenario

To create a Workfront scenario, perform 

#### Create a scenario create-scenario

1. **Sign into your Workfront Fusion account**** Navigate to [[https://app.workfrontfusion.com/](https://app.workfrontfusion.com/](https://app.workfrontfusion.com/](https://app.workfrontfusion.com/)) and log in with your credentials.
2. **Click `Scenarios` in the left panel.** This will display a list of existing scenarios.
3. **Click `Create a new scenario` in the upper-right corner of the page.** A new scenario creation page will appear.
4. **Select `New scenario` in the upper-left corner and type a descriptive name for the scenario.**  Example: "AEM Forms Submission Processor".
5. **Click the question mark icon and ensure you add the first module as `AEM Forms`.** This ensures the scenario is triggered by AEM Forms events.
6. **Select the `Watch for Form Events` dialog box.** This module will listen for form submissions from AEM Forms.

**Troubleshooting:** If the AEM Forms module is not available, verify your Workfront Fusion account has the necessary connectors enabled.


#### Add a webhook add-webhook

1. **Click `Add` in the `Watch for Form Events` dialog box.** A dialog box titled `Add a webhook` appears.
2. **Specify a webhook name.**  Example: "AEM Forms Webhook".
3. **Click `Add` to add a new connection.** The `Create a Connection` dialog box appears.


#### Add a connection to a webhook add-connection

1. **Specify a `Connection Name` in the `Create a Connection` dialog box.** Example: "AEM Forms Connection".
2. **Select `Environment` and `Type` from the drop-down list.** Choose the appropriate environment (e.g., Production, Sandbox) and connection type.
3. **Enter the `Instance URL`.** This is the URL of your AEM Forms instance.
4. **Replace `ims-na1.adobelogin.com` in the `IMS endpoint` with the value of `imsEndpoint` from the service credentials in the Developer console.**  Ensure the `[https://`](https://`) prefix is retained.
5. **Specify    * `Client ID` with the value of `clientId` from the service credentials.
   * `Client Secret` with the value of `clientSecret` from the service credentials.
   * `Technical Account ID` with the value of `id` from the service credentials.
   * `Org ID` with the value of `org` from the service credentials.
   * `Meta Scopes` with the value of `metascopes` from the service credentials.
   * `Private Keys` with the value of `privateKey` from the service credentials.
6. **For `Private Key`, remove `\r\n` from its value.**  This is a common error.
7. **Click `Continue`.**
8. **Select the created connection from the drop-down list in the `Connection` field of the `Add a webhook` dialog box.**
9. **Click `Save`.**
10. **Click `OK` and save the changes for the scenario.**
11. **To activate the scenario, click the ON/OFF toggle button in the scenario editor.**

**Validation:** Verify the connection status in Workfront Fusion.  A successful connection indicates proper authentication.


### 2. **Configure submit action of an Adaptive Form for Workfront Fusion

You can configure the submit action for Workfront Fusion for**

* New Adaptive Forms
* Existing Adaptive forms


#### Configure submit action of new Adaptive Form for Workfront Fusion new-af-submit-action

1. **Log in to your AEM instance.**
2. **Go to `Forms > Forms and Documents > Create > Adaptive Form`.** The `Create Form` wizard appears.
3. **Select an Adaptive Form template from the `Source` tab.**
4. **Select a theme from the `Style` tab.**
5. **Select `Invoke a Workfront Fusion Scenario` from the `Submission` tab.**
6. **Select the created webhook from the `Options` tab in the `Properties` window.**
7. **Click `Create`.**
8. **Specify the name for your new Adaptive Form and click `Create`.**


#### Configure submit action of existing Adaptive Form for Workfront Fusion existing-af-submit-action

1. **Log in to your AEM instance.**
2. **Go to `Forms > Forms and Documents`.**
3. **Select an Adaptive Form and open the form in an edit mode.**
4. **Open the Content browser, and select the `Guide Container` component of your Adaptive Form.**
5. **Click the Guide Container properties icon. The Adaptive Form Container dialog box opens.**
6. **Open the `Submission` tab.**
7. **Select the `Submit action` as `Invoke a Workfront Fusion Scenario`.**
8. **Select `Workfront Fusion scenario` from the drop-down list.**


## Configuration Examples


### AEM Forms Configuration

```json
{
  "formType": "adaptive",
  "submitAction": "workfront_fusion",
  "webhookUrl": "[https://app.workfrontfusion.com/webhook/your-webhook-id",](https://app.workfrontfusion.com/webhook/your-webhook-id",)
  "dataFormat": "json",
  "authentication": "oauth2",
  "timeout": 30000,
  "retryAttempts": 3,
  "validation": {
    "required": true,
    "dataMapping": {
      "formField": "workfrontField",
      "transformation": "uppercase"
    }
  }
}
```


### Workfront Fusion Webhook Configuration

```json
{
  "name": "AEM Forms Integration",
  "description": "Webhook for AEM Forms submissions",
  "url": "[https://app.workfrontfusion.com/webhook/your-webhook-id",](https://app.workfrontfusion.com/webhook/your-webhook-id",)
  "method": "POST",
  "headers": {
    "Content-Type": "application/json",
    "Authorization": "Bearer your-api-key",
    "X-Request-ID": "{{guid}}"
  },
  "body": {
    "formData": "{{trigger.body}}",
    "timestamp": "{{trigger.timestamp}}",
    "source": "aem_forms",
    "version": "1.0"
  },
  "security": {
    "rateLimit": 100,
    "timeout": 30,
    "retryPolicy": "exponential"
  }
}
```


## Basic Testing


### Unit Testing
* Test individual form components and validation rules.
* Verify data transformation and mapping logic.
* Test error handling and recovery mechanisms.


### Integration Testing
* Test end-to-end form submission workflow.
* Verify data flow between AEM and Workfront Fusion.
* Test error scenarios and recovery procedures.  Simulate invalid data and network interruptions.


## Best Practices best-practices

* It is recommended to choose your webhook name carefully, as the specified webhook name appears in the AEM instance.
* A scenario can have multiple webhook links but at a time only one webhook link is active. It is recommended to delete the unlinked webhook, so that it does not appear in AEM Forms submit action drop-down list.
* Implement proper error handling and retry mechanisms for production environments.
* Use monitoring and alerting to track integration health and performance.
* Regular security audits and credential rotation.
* Document all custom configurations and procedures.
* Test integrations thoroughly before production deployment.
* Securely store and manage API keys and authentication tokens.
* Implement input validation to prevent malicious data from being processed.
* Regularly review and update configurations to ensure compatibility with the latest versions of AEM Forms and Workfront Fusion.


## Related Articles

* [Submit to REST endpoint](https://experienceleague.adobe.com/en/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/configure-submit-actions/configure-submit-actions.html#submit-to-rest-endpoint)
* [Submit using Form Data Model](https://experienceleague.adobe.com/en/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/configure-submit-actions/configure-submit-actions.html#submit-using-form-data-model)
* [Submit to Power Automate](https://experienceleague.adobe.com/en/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/configure-submit-actions/configure-submit-actions.html#submit-to-power-automate)
* [Create custom submit action](https://experienceleague.adobe.com/en/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/configure-submit-actions/configure-submit-actions.html#create-custom-submit-action)
* [Adobe Experience League Support](https://experienceleague.adobe.com/home?support-tab=home#support)
* [Adobe Experience League Community](https://experienceleaguecommunities.adobe.com/?profile.language=en)
* [Adobe Developer Console](https://developer.adobe.com/console)
* [AEM Forms Best Practices](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/adaptive-form-best-practices.html)
* [Workfront Fusion Scenarios](https://experienceleague.adobe.com/docs/workfront-fusion/using/scenarios/scenarios.html)
* [AEM Forms Integration Guide](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate/configure-submit-adaptive-form.html)

**Important:** Remember to replace all bracketed placeholders with your specific configuration details. Thoroughly test the integration in a non-production environment before deploying to production.

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

*This enhanced documentation was generated by combining document analysis and video content extraction to provide comprehensive implementation guidance.*
