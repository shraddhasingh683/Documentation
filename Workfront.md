
# Integration of Adobe Workfront Fusion with AEM Forms Submission

**Last updated:** July 13, 2025

* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** Workfront Fusion Integration, AEM Forms, Adaptive Forms, Integration
* **Audience:** Admin, Developer, Business User

## Overview

This enhanced documentation provides comprehensive guidance for implementing Adobe Experience Manager Forms integration with Workfront Fusion, combining insights from both the original documentation and video analysis to deliver actionable, step-by-step instructions.

## Prerequisites

Before you begin, ensure you have:

**Last updated:** Sun Jul 13 2025 21:34:49 GMT+0000 (Coordinated Universal Time)
* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** AEM Forms Integration, Workfront Fusion Integration
* **CREATED FOR:** Admin, Developer, Business User
* A valid Workfront and Workfront Fusion license
* An AEM user with right to access Dev Console to retrieve the service credentials
* Network connectivity to both AEM and Workfront Fusion services
* Required user roles and access credentials (administrator access recommended)
* Administrative access to configure integrations and webhooks
* Understanding of AEM Forms and Workfront Fusion concepts
* Valid SSL certificates for secure communication
* API keys and authentication credentials for both systems
* Access to Adobe Developer Console for service credentials
* Understanding of JSON data formats and webhook configurations
* Network access to required Adobe services and endpoints
* Proper firewall and security configurations

## Implementation Steps

# Integration of Adobe Workfront Fusion with AEM Forms Submission
**Last updated:** Sun Jul 13 2025 21:34:49 GMT+0000 (Coordinated Universal Time)


* **Applies to:** Adobe Experience Manager Forms as a Cloud Service
* **Topics:** AEM Forms Integration, Workfront Fusion Integration
* **CREATED FOR:** Admin, Developer, Business User


## Overview

Adobe Workfront Fusion automates repetitive tasks and workflows, allowing seamless integration with AEM Forms for automated form processing. This integration enables organizations to create end-to-end workflows that capture form data and automatically trigger business processes.


## Prerequisites

To complete this task successfully, ensure you have:

* A valid Workfront and Workfront Fusion license
* An AEM user with right to access Dev Console to retrieve the service credentials
* Network connectivity to both AEM and Workfront Fusion services
* Required user roles and access credentials (administrator access recommended)
* Administrative access to configure integrations and webhooks
* Understanding of AEM Forms and Workfront Fusion concepts
* Valid SSL certificates for secure communication
* API keys and authentication credentials for both systems
* Access to Adobe Developer Console for service credentials
* Understanding of JSON data formats and webhook configurations
* Network access to required Adobe services and endpoints
* Proper firewall and security configurations


## Architecture Overview

The integration between AEM Forms and Workfront Fusion follows a webhook-based architecture:

1. **AEM Forms**: Captures form submissions and sends data to Workfront Fusion
2. **Webhook**: Acts as the communication bridge between the two systems
3. **Workfront Fusion**: Processes the form data and executes automated workflows
4. **Data Flow**: JSON-based data exchange with proper authentication and error handling


## Implementation Steps


### Step 1: Configure AEM Forms Environment

**Objective:** Set up the AEM Forms environment for Workfront Fusion integration

**Detailed Steps:**

1. **Access AEM Forms Author Instance**
   - Navigate to your AEM Forms author instance: 
   - Log in with administrator credentials
   - Ensure you have the necessary permissions for form configuration
   - Verify you're in the correct environment (author vs publish)

2. **Create or Configure Adaptive Form**
   - Go to **Forms & Documents** in the AEM navigation menu
   - Click **Create** → **Adaptive Form** or select an existing form
   - Configure form fields according to your business requirements
   - Set up form validation rules and submission handling
   - Configure form properties and metadata

3. **Configure Form Submission Settings**
   - Open the form properties by right-clicking the form
   - Navigate to the **Submission** tab
   - Configure the submission action to point to Workfront Fusion
   - Set up proper authentication and endpoint configuration
   - Configure data mapping and transformation rules


### Step 2: Set Up Workfront Fusion Integration

**Objective:** Configure Workfront Fusion to receive form submissions from AEM

**Detailed Steps:**

1. **Access Workfront Fusion**
   - Log in to your Workfront Fusion account: 
   - Navigate to the **Scenarios** section
   - Create a new scenario for AEM Forms integration
   - Set up proper organization and team access

2. **Configure Webhook Trigger**
   - Add a **Webhook** trigger to your scenario
   - Copy the webhook URL for use in AEM configuration
   - Configure the webhook to accept JSON data from AEM
   - Set up webhook security and authentication
   - Configure webhook response handling

3. **Set Up Data Processing**
   - Add modules to process the incoming form data
   - Map form fields to Workfront Fusion data structures
   - Configure any required data transformations
   - Set up error handling and retry logic
   - Configure data validation and filtering


### Step 3: Establish Connection Between Systems

**Objective:** Connect AEM Forms with Workfront Fusion for seamless data flow

**Detailed Steps:**

1. **Configure AEM Form Submission Action**
   - In your Adaptive Form configuration
   - Set the submission URL to your Workfront Fusion webhook
   - Configure authentication headers if required
   - Test the connection to ensure proper communication
   - Set up SSL/TLS certificate validation

2. **Set Up Error Handling**
   - Configure retry mechanisms for failed submissions
   - Set up proper error logging and monitoring
   - Implement user feedback for submission status
   - Configure timeout settings and connection limits
   - Set up alerting for critical failures

3. **Test the Integration**
   - Submit test forms to verify data flow
   - Check Workfront Fusion for received data
   - Validate data mapping and processing
   - Test error scenarios and recovery
   - Verify end-to-end functionality


### Step 4: Advanced Configuration

**Objective:** Implement advanced features for production use

**Detailed Steps:**

1. **Set Up Authentication**
   - Configure secure authentication between systems
   - Implement API key or OAuth authentication
   - Ensure proper credential management
   - Set up certificate-based authentication
   - Configure multi-factor authentication if required

2. **Configure Monitoring and Logging**
   - Set up comprehensive logging for all form submissions
   - Implement monitoring for integration health
   - Configure alerts for failures or issues
   - Set up performance monitoring and metrics
   - Configure audit logging for compliance

3. **Optimize Performance**
   - Configure appropriate timeouts and retry settings
   - Implement caching where appropriate
   - Monitor and optimize data transfer efficiency
   - Set up load balancing if required
   - Configure connection pooling


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
  "retryAttempts": 3
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
    "Authorization": "Bearer your-api-key"
  },
  "body": {
    "formData": "{{trigger.body}}",
    "timestamp": "{{trigger.timestamp}}",
    "source": "aem_forms"
  }
}
```


## Testing and Validation


### Unit Testing
- Test individual form components and validation rules
- Verify data transformation and mapping logic
- Test error handling and recovery mechanisms


### Integration Testing
- Test end-to-end form submission workflow
- Verify data flow between AEM and Workfront Fusion
- Test error scenarios and recovery procedures


### Performance Testing
- Test form submission performance under load
- Verify timeout and retry mechanisms
- Test system behavior under various network conditions


### Security Testing
- Test authentication and authorization mechanisms
- Verify data encryption and security measures
- Test input validation and sanitization


## Deployment and Production


## Related Resources

- **[Adobe Experience League Documentation](https://experienceleague.adobe.com/en/docs)**
- **[Adobe Experience League Support](https://experienceleague.adobe.com/home?support-tab=home#support)**
- **[Adobe Experience League Community](https://experienceleaguecommunities.adobe.com/?profile.language=en)**
- **[AEM Forms Documentation](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html)**
- **[Workfront Fusion Documentation](https://experienceleague.adobe.com/docs/workfront-fusion/using/workfront-fusion-2.html)**
- **[AEM Forms Best Practices](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/adaptive-form-best-practices.html)**
- **[Workfront Fusion Scenarios](https://experienceleague.adobe.com/docs/workfront-fusion/using/scenarios/scenarios.html)**
- **[AEM Forms Integration Guide](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate/configure-submit-adaptive-form.html)**
- **[Adobe Experience Manager Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/home.html)**
- **[Adobe Workfront Fusion Scenarios](https://experienceleague.adobe.com/docs/workfront-fusion/using/scenarios/scenarios.html)**
- **[AEM Forms Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/overview.html)**
- **[Adobe Experience League Training](https://experienceleague.adobe.com/?lang=en#training)**

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
