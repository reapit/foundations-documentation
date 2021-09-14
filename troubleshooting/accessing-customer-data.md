# Accessing Customer Data

### **Error:** “The request could not be fulfilled as the reapit customer specified by the provided credentials does not have the application installed”

### **Error:** “Unauthorized: 401 Unauthorized”

When making a request to our Platform API’s using the Client Credentials Flow and you receive the above error, it maybe related to the incorrect Client ID you have provided in your ‘reapit-customer’ header.

How to verify the Customer ID:

* Ask the agent to confirm their Customer ID – click [here ](../faqs.md#how-do-i-find-a-customer-id)for more information on how to obtain the Customer ID
* View the [email ](../faqs.md#installation)notification you received when the app was installed 
* View the [installations ](../faqs.md#installations-table)table on your app listing
* If you had setup a [webhook ](../faqs.md#webhooks)for application.install, the payload will have included the ‘customerId’

or 

The Reapit Customer ID you have provided in your ‘reapit-customer’ header has not yet installed your application from the AppMarket. The installation process is the step that grants you access to live data \(not Sandbox\).

If you are a Reapit Agent looking to interact with your own data, you will still need to list \(privately\) and install your own app.

For more information on how to list your app in the AppMarket, please click [here](https://foundations-documentation.reapit.cloud/listing-your-app)

