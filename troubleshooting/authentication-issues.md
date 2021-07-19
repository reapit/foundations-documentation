# Authentication Issues

## **Client Credentials Flow -** Authentication Issues

### **Error: "invalid\_client"**

* Check you have provided the correct ‘Client ID’ in your request payload using the header ‘client\_id’. Your Client ID is available on your app listing in the [Developer Portal](https://developers.reapit.cloud/apps)
* It’s possible that the ‘Authorization’ base64 secret you have provided maybe invalid.
* Ensure you have provided the encoded version as the value for the Authorization header set to ‘Basic’ \(Basic XBASE64SECRETX\)

For more information on Authentication \(using the Client Credentials Flow\), please click [here](https://foundations-documentation.reapit.cloud/api/api-documentation#client-credentials-flow)

Screenshot showing how to find your ‘Client ID’ and ‘Secret’ on your App listing:



![](../.gitbook/assets/image%20%28104%29.png)

### **Error:** "invalid\_request"

* Check you have provided the following values and headings:  grant\_type=client\_credentials client\_id=XCLIENTIDX Authorization: Basic XBASE64SECRETX content-type: application/x-www-form-urlencoded

### **Example POST Request \(**only applies to client\_credentials flow\)

You can use the example `POST` request to obtain an access token, simply replace XCLIENTIDX with your client ID and XBASE64SECRETX with your encoded Client ID and Secret:

```text
curl --request POST \
  --url 'https://connect.reapit.cloud/token?grant_type=client_credentials&client_id=XCLIENTIDX' \
  --header 'Authorization: Basic XBASE64SECRETX' \
  --header 'content-type: application/x-www-form-urlencoded' \

```

 

