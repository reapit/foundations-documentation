# REST API

### **Error: “Precondition failed: The ETag provided does not match the current version of this resource. Re-fetch the latest version of this resource before attempting to update it."**

* The most common reason is that the resource has been updated since it was fetched
* The Etag should be provided in a quotation marks Example "If-Match": "\"3B1D7563C34EE44E5D5B4E2AB99E288F\""

For more information on Etags, please click [here](https://foundations-documentation.reapit.cloud/api/api-documentation#optimistic-concurrency).

