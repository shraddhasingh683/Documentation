
# Integration of Adobe Workfront Fusion with AEM Forms Submission

**Last updated:** July 11, 2025

* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** Workfront Fusion Integration, AEM Forms, Adaptive Forms, Integration
* **Audience:** Admin, Developer, Business User

## Overview

This enhanced documentation provides comprehensive guidance for implementing Adobe Experience Manager Forms integration with Workfront Fusion, combining insights from both the original documentation and video analysis to deliver actionable, step-by-step instructions.

## Prerequisites

Before you begin, ensure you have:

**Last updated:** Fri Jul 11 2025 18:03:21 GMT+0000 (Coordinated Universal Time)
* **Applies to:** Experience Manager as a Cloud Service
* **Topics:** Adaptive Forms
* **CREATED FOR:** Admin, User
* **Workfront and Workfront Fusion License:** A valid Workfront and Workfront Fusion license is required.  Verify license coverage includes the necessary connectors and features for AEM Forms integration.
* **AEM User Access:** An AEM user with access to the Dev Console to retrieve the service credentials is necessary. This user should have appropriate permissions to manage Adaptive Forms and their submission actions.
* **Network Connectivity:** Stable network connectivity between the AEM Forms instance, the Workfront Fusion environment, and the Adobe IMS (Identity Management System) is essential.  Ensure firewalls and proxies allow communication on the required ports (typically 443 for HTTPS).
* **Technical Account Membership:** The Technical Account must be a member of the `forms-users` group within Workfront. This group grants the necessary permissions for AEM Forms integration. Verify membership through the Workfront administration console.
* **Administrative Access:**  Administrative privileges within both AEM Forms and Workfront Fusion are required to configure the integration, create webhooks, and manage connections.
* **Understanding of AEM Forms and Workfront Fusion Concepts:** Familiarity with Adaptive Forms, submission actions, webhooks, and Workfront Fusion scenarios is crucial for successful integration.
* **Valid SSL Certificates:** Ensure both AEM Forms and Workfront Fusion are configured with valid SSL certificates for secure communication.
* **API Keys and Authentication Credentials:** Securely store and manage API keys, client IDs, client secrets, and technical account IDs.  Implement proper access controls to prevent unauthorized access.
* **Access to Adobe Developer Console:** Access to the Adobe Developer Console is required to retrieve service credentials (clientId, clientSecret, id, org, metascopes, privateKey) for authenticating with AEM Forms.
* **Understanding of JSON Data Formats and Webhook Configurations:**  A solid understanding of JSON data structures and webhook configurations is essential for correctly formatting data and configuring the integration.
* **Network Access to Required Adobe Services and Endpoints:** Ensure network access to Adobe's IMS endpoints and other required services.
* **Proper Firewall and Security Configurations:** Configure firewalls and security settings to allow communication between AEM Forms, Workfront Fusion, and Adobe services.  Implement appropriate security measures to protect sensitive data.

## Implementation Steps

# Integration of Adobe Workfront Fusion with AEM Forms Submission
**Last updated:** Fri Jul 11 2025 18:03:21 GMT+0000 (Coordinated Universal Time)


* **Applies to:** Experience Manager as a Cloud Service
* **Topics:** Adaptive Forms
* **CREATED FOR:** Admin, User


## Prerequisites

To establish a connection between Workfront Fusion and AEM Forms, 
* **Workfront and Workfront Fusion License:** A valid Workfront and Workfront Fusion license is required.  Verify license coverage includes the necessary connectors and features for AEM Forms integration.
* **AEM User Access:** An AEM user with access to the Dev Console to retrieve the service credentials is necessary. This user should have appropriate permissions to manage Adaptive Forms and their submission actions.
* **Network Connectivity:** Stable network connectivity between the AEM Forms instance, the Workfront Fusion environment, and the Adobe IMS (Identity Management System) is essential.  Ensure firewalls and proxies allow communication on the required ports (typically 443 for HTTPS).
* **Technical Account Membership:** The Technical Account must be a member of the `forms-users` group within Workfront. This group grants the necessary permissions for AEM Forms integration. Verify membership through the Workfront administration console.
* **Administrative Access:**  Administrative privileges within both AEM Forms and Workfront Fusion are required to configure the integration, create webhooks, and manage connections.
* **Understanding of AEM Forms and Workfront Fusion Concepts:** Familiarity with Adaptive Forms, submission actions, webhooks, and Workfront Fusion scenarios is crucial for successful integration.
* **Valid SSL Certificates:** Ensure both AEM Forms and Workfront Fusion are configured with valid SSL certificates for secure communication.
* **API Keys and Authentication Credentials:** Securely store and manage API keys, client IDs, client secrets, and technical account IDs.  Implement proper access controls to prevent unauthorized access.
* **Access to Adobe Developer Console:** Access to the Adobe Developer Console is required to retrieve service credentials (clientId, clientSecret, id, org, metascopes, privateKey) for authenticating with AEM Forms.
* **Understanding of JSON Data Formats and Webhook Configurations:**  A solid understanding of JSON data structures and webhook configurations is essential for correctly formatting data and configuring the integration.
* **Network Access to Required Adobe Services and Endpoints:** Ensure network access to Adobe's IMS endpoints and other required services.
* **Proper Firewall and Security Configurations:** Configure firewalls and security settings to allow communication between AEM Forms, Workfront Fusion, and Adobe services.  Implement appropriate security measures to protect sensitive data.


## Integrate AEM Forms with Adobe Workfront Fusion


### 1. **Create a Workfront Scenario workflow-scenario

To create a Workfront scenario, perform 

#### Create a scenario create-scenario

1. **Sign into your [Workfront Fusion account](https**//).**  Verify you have the necessary permissions to create and manage scenarios.
2. **Click `Scenarios` in the left panel.** This will display a list of existing scenarios or an empty state if none exist.
3. **Click `Create a new scenario` in the upper-right corner of the page.** This initiates the scenario creation process.
4. **Select `New scenario` in the upper-left corner and type a proper name for the scenario.**  Use a descriptive name that clearly indicates the purpose of the scenario (e.g., "Adaptive Form Submission to Workfront").
5. **Click the question mark icon and ensure you add the first module as `AEM Forms`.** This ensures the scenario is configured to listen for AEM Forms events.
6. **Select the `Watch for Form Events` dialog box.** This module will monitor AEM Forms for new submissions.


#### Add a webhook add-webhook

1. **Click `Add` in the `Watch for Form Events` dialog box.** A dialog box titled `Add a webhook` appears.
2. **Specify a webhook name.**  Choose a descriptive name for the webhook (e.g., "AEM Forms Webhook").
3. **Click `Add` to add a new connection.** The `Create a Connection` dialog box appears.


#### Add a connection to a webhook add-connection

1. **Specify a `Connection Name` in the `Create a Connection` dialog box.**  Use a descriptive name for the connection (e.g., "AEM Forms Connection").
2. **Select `Environment` and `Type` from the drop-down list.** Choose the appropriate environment (e.g., Production, Sandbox) and connection type (e.g., AEM Forms).
3. **Enter the `Instance URL`.** This is the URL of your AEM Forms instance.
4. **Replace `ims-na1.adobelogin.com` in the `IMS endpoint` with the value of `imsEndpoint` from the service credentials in the Developer console.**  Ensure the URL is correctly formatted and accessible.
5. **Retain the `[https://`](https://`) in the `IMS endpoint` textbox while adding the `imsEndpoint` URL.** This is crucial for secure communication.
6. **Specify     * `Client ID` with the value of `clientId` from the service credentials in the Developer console.
    * `Client Secret` with the value of `clientSecret` from the service credentials in the Developer console.
    * `Technical Account ID` with the value of `id` from the service credentials in the Developer console.
    * `Org ID` with the value of `org` from the service credentials in the Developer console.
    * `Meta Scopes` with the value of `metascopes` from the service credentials in the Developer console.
    * `Private Keys` with the value of `privateKey` from the service credentials in the Developer console.
7. **For `Private Key`, remove `\r\n` from its value.**  This is a common formatting issue that can prevent the connection from being established.  For example, if the private key value is `\r\nIJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL\r\nMy1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`, then after removing the `\r\n` the key would look like:
    * `IJAVO8GDYAOZ9jMA0GCSqGSIb3DQEBCwUAMDAxL`
    * `My1lMTUxODMxLWNtc3RnLWludGVncmF0aW9uLTAw`
8. **You also have the option to retrieve a private key or certificate from the file by selecting the `Extract` button.** This simplifies the process of importing the key.
9. **Click `Continue`.**
10. **Select the created connection from the drop-down list in the `Connection` field of the `Add a webhook` dialog box.**
11. **Click `Save`.**
12. **Click `OK` and save the changes for the scenario.**
13. **To activate the scenario, click the ON/OFF toggle button in the scenario editor.**  The scenario must be active to receive form submissions.


### 2. **Configure submit action of an Adaptive Form for Workfront Fusion

You can configure the submit action for Workfront Fusion for**

* New Adaptive Forms
* Existing Adaptive forms


#### Configure submit action of new Adaptive Form for Workfront Fusion new-af-submit-action

1. **Log in to your AEM instance.**
2. **Go to `Forms > Forms and Documents > Create > Adaptive Form`.** The `Create Form` wizard appears.
3. **Select an Adaptive Form template from the `Source` tab.**
4. **Select a theme from the `Style` tab.**
5. **Select `Invoke a WorkFront Fusion Scenario` from the `Submission` tab.**
6. **Select the created webhook from the `Options` tab in the `Properties` window.**  The webhook name should appear in the drop-down list.
7. **Click `Create`.**
8. **Specify the name for your new Adaptive Form and click `Create`.**


#### Configure submit action of existing Adaptive Form for Workfront Fusion existing-af-submit-action

1. **Log in to your AEM instance.**
2. **Go to `Forms > Forms and Documents`.**
3. **Select an Adaptive Form and open the form in an edit mode.**
4. **Open the Content browser, and select the `Guide Container` component of your Adaptive Form.**
5. **Click the Guide Container properties icon. The Adaptive Form Container dialog box opens.**
6. **Open the `Submission` tab.**
7. **Select the `Submit action` as `Invoke a WorkFront Fusion Scenario`.**
8. **Select `Workfront Fusion scenario` from the drop-down list.**
9. **Click `Done`.**


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
* Test individual form components and validation rules within AEM Forms.
* Verify data transformation and mapping logic within the Adaptive Form.
* Test error handling and recovery mechanisms within the Adaptive Form.


### Integration Testing
* Test end-to-end form submission workflow from AEM Forms to Workfront Fusion.
* Verify data flow between AEM Forms and Workfront Fusion, ensuring all fields are correctly mapped.
* Test error scenarios and recovery procedures, including network outages and authentication failures.  Simulate invalid data and verify error handling.
* Use Workfront Fusion's scenario execution logs to monitor data flow and identify any issues.


## Best Practices best-practices

* It is recommended to choose your webhook name carefully, as the specified webhook name appears in the AEM instance. In case, you change the webhook name in future it is not reflected at the AEM Forms submit action drop-down list.
* A scenario can have multiple webhook links but at a time only one webhook link is active. It is recommended to delete the unlinked webhook, so that it does not appear in AEM Forms submit action drop-down list.
* Implement proper error handling and retry mechanisms for production environments.  Configure Workfront Fusion's retry policy to handle transient errors.
* Use monitoring and alerting to track integration health and performance.  Monitor scenario execution times, error rates, and data volume.
* Regular security audits and credential rotation.  Rotate API keys and credentials on a regular basis.
* Document all custom configurations and procedures.  Maintain detailed documentation of the integration architecture, configuration settings, and troubleshooting steps.
* Test integrations thoroughly before production deployment.  Perform comprehensive testing in a staging environment before deploying to production.
* Implement logging within the Workfront Fusion scenario to capture detailed information about each execution.
* Securely store and manage sensitive data, such as API keys and passwords.


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
