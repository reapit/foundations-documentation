# Reapit Connect

## **Reapit Connect**

### **Error: “Redirect Mismatch”**

* Check you have provided the correct Redirect URL(s) and Sign Out URL(s) on your app listing under the 'Authentication' section. \
  \
  When a user logs in, Reapit Connect will need to know where to direct the user. This is your Redirect URL(s). Reapit Connect will also need to know where to route your user if they logout. This is your Sign Out URL(s).

To test your application locally, you can provide the following (example):

**Redirect URI:** http://localhost:8080

**Signout URI:** http://localhost:8080/login

<figure><img src="../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

For more information on Reapit Connect, please [click here](https://foundations-documentation.reapit.cloud/api/reapit-connect).&#x20;
