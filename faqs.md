# FAQ's

## **General**

### How do I find a ‘Customer ID’?

An agent can locate their Customer ID via the Marketplace inside of Agency Cloud.

* Within Agency Cloud, click on ‘Apps’ and select ‘Browse’
* Click on the ‘Settings’ icon in the bottom left-hand corner
* The Customer ID can be located on the right-hand side of the screen.

![](.gitbook/assets/image%20%2899%29.png)





### I just want to access my data, do I still need to create an app? 

Yes, the app registration process gives you the required authentication, either to use as a client side/server-side integration or as an app that launches inside of the Desktop CRM \(Agency Cloud\).

In order to access customer data, an installation will need to occur. This is done by creating and listing an app in the Marketplace. It can either be public or private to a specific agent. 

Please [click here](faqs.md#listing-your-app) for more information on Listing an App in Marketplace

### When will my requested feature  be available?

You can track the status of your issue [directly in GitHub](https://github.com/reapit/foundations/issues). 

Please [click here](app-development/dev-requests.md) for details on our development processes.

## Registration

### We have created multiple accounts but want to work on the same app, what can we do? 

You can invite members to collaboratively work within the same Developer Portal organisation from the '[Organisations](https://developers.reapit.cloud/settings/organisation)' page using the 'Invite Member' option.

## **Testing**

### **How can I test my App or Integration?**

The Developer Edition of Agency Cloud allows you to test your apps/integration within the desktop application using Sandbox data.

Please [click here](https://developers.reapit.cloud/desktop) for more information on testing your App or Integration.

### How can I test my Integration without a customer installation?

You can use **authorization code flow** by providing your developer portal credentials to our Reapit Connect service

You can use **client credentials flow** by providing `SBOX` as your `reapit-customer` request header

Please [click here](https://foundations-documentation.reapit.cloud/api/api-documentation#sandbox-mode) for more information on using Sandbox data

### How do I Test my App/Integration with a specific agent?

To test with a specific agent your app will need to be set to private and submitted for approval.

Using the ‘Private App’ section on your app listing, you will need to provide the Customer ID of the agent. However, it will first need to be approved and tested by our Admin department. 

Once the app has been approved it will be available to the selected agent\(s\) to ‘Install’ from the Marketplace.

Please [click here](faqs.md#how-do-i-find-a-customer-id) for information on finding the Customer ID  
Please [click here](faqs.md#listing-your-app) for more information on Listing your app  
Please [click here](faqs.md#app-approvals) for more information on App Approvals

## **Developer Edition of Agency Cloud**

### I need help with using Agency Cloud \(Desktop CRM\)

We do not provide online or telephone support for the Developer Edition of Agency Cloud.

Please [click here](https://developers.dev.paas.reapit.cloud/developer-edition-guide.pdf) to view the Developer Edition Guide

## **Listing your App in the Marketplace**

### I’m ready to list my app, what do I need to do?

When you are ready to list your app in the Marketplace, either publicly or as a private app, it will first need to be submitted for approval privately to our testing environment 'RES'.   
  
First, ensure your app is ready to be listed, please [click here](listing-your-app.md) to see a guide on what information is required. 

Once the content of your app has been added: 

* Enter Customer ID 'RES' in the 'Private Apps' section on your app listing
* Select the 'Submit for Approval' check box and Submit' 

Please [click here ](https://foundations-documentation.reapit.cloud/listing-your-app#apps-launchable-inside-of-agency-cloud)for more information on testing

## **App Approvals**

### I have submitted my App for approval. How long is the approval process?

Depending on your app listing or integration and its complexity, from start to finish can typically take between 2-7 weeks.  A member of the reviewal team will make direct contact with you within 24 – 48 hours.  

Please [click here](https://foundations-documentation.reapit.cloud/listing-your-app#2-submit-for-approval) for more information on the App Approval Process 

## **Authentication**

### How do I change the authentication method on my app?

Once your app has been created, you cannot change the authentication flow. You will need to register a new app using your preferred flow.

Please [click here](https://foundations-documentation.reapit.cloud/api/reapit-connect#authentication-flow) for more information on Authentication Flows

## **Webhooks**

### How can I setup an alert to know when a new action or information has occurred or been added?

Our Webhooks system allows your application to directly subscribe to events happening in our customers data. You can manage Webhook subscriptions [here](https://developers.reapit.cloud/webhooks).

Please [click here](https://foundations-documentation.reapit.cloud/api/webhooks) to see more information on Webhooks

## **Billing/Accounts**

### What is a Reapit Account Reference?

It is a reference that is assigned to your organisation/company and would have been setup with our Accounts Department. If you have an existing relationship with Reapit, you should be able to obtain your reference on previous correspondence. If you do not have an existing relationship, you will be required to complete a Direct Debit mandate.

Please [click here](https://foundations-documentation.reapit.cloud/developer-portal#10-billing) for more information on setting up your Billing Information.

### My billing information is with accounts - how long will this take to process?

Once you have submitted your billing information, it will be sent to our Accounts Department to verify/setup and your account status will be set to 'Pending'. 

This setup process is usually completed within 24-48 hours. Once the information has been verified you will receive an email confirmation and your account status will be set to 'Confirmed'

Please [click here](https://foundations-documentation.reapit.cloud/developer-portal#10-billing) for more information on setting up your billing information.

## Pricing/Costs

### Do you have information regarding pricing?

You can find information regarding pricing using either the documentation listed below or using our ‘API Cost Calculator’ on the [Analytics](https://developers.reapit.cloud/analytics/costexplorer) page.

Please [click here](pricing.md) for more information on pricing  
Please [click here](developer-terms-and-conditions.md#schedule-2-fees) to see pricing information on our Terms and Conditions

### I am an agency building a website for a Reapit Customer - will I be charged for using this service?

Please [click here](pricing.md#website-integration-private-to-a-single-customer-id) for more information regarding pricing for website integrations

### I have looked at your pricing information and I have a query - who do I speak to?

Should you have any questions or queries regarding the cost or pricing structure, please [click here](mailto:mgoddard@reapit.com?subject=Foundations%20Pricing%20Query) to contact a member of the team

