# Reapit Connect Updates

{% hint style="info" %}
The following documentation does not come into effect until 18th November 2024 at 20:00 GMT. No changes should be made to your applications prior to this date
{% endhint %}

### Overview

In November 2024 we migrated to a new identity provider. To make the migration process easier for developers, a compatibility layer was built so that there wasn't a requirement for all integrating partners to update the way they interact with Reapit Connect to sign users in and obtain short lived access tokens. After an appropriate time, the compatibility layer will be removed and it is expected that all applications will have been updated. There are various logging points that will allow us to engage with you directly if we detect that your application has not been updated well ahead of the compatibility layer being sunset.

The following changes should be planned in your next round of application updates taking place after the release of our new identity provider. Please ensure you refer to the relevant section(s) for your use case, in addition to the [General Changes](reapit-connect-updates.md#general-changes) section which includes information that applies to all applications.



### React Developers using connect-session

Applications using the [connect-session](https://www.npmjs.com/package/@reapit/connect-session) NPM package should update to a version >= 6.1.3. The updated package targets the new endpoints and also leverages [PKCE](https://oauth.net/2/pkce/) by default, enhancing the security of your application.&#x20;

Please ensure you update connect-session regularly as we will publish versions that slowly deprecate the legacy functionality that targets the compatibility layer.

The local development portion of the [Authorisation Code flow Applications (client side) section](reapit-connect-updates.md#authorisation-code-flow-applications-client-side) also applies to React developers using the connect-session library





### Authorisation Code flow Applications (client side)

#### Changes to URLs /Endpoints

Instead of calling \`GET /logout\` use \`GET /oidc/logout\` with your client\_id and desired post\_logout\_redirect\_uri. The post\_logout\_redirect\_uri must be  registered against your app in the DeveloperPortal as one of the logout urls. For example `GET /logout?client_id=12345&logout_uri=https://myapp.io` becomes `GET /oidc/logout?client_id=12345&post_logout_redirect_uri=https://myapp.io`.

Instead of calling /login call /oauth/authorize.

When calling /oauth/authorize you should explicitly specify the space-separated scopes that you want the token to contain. Product-specific scopes need to be added for use in your application via your app listing in the developer portal. To obtain a refresh token request the `offline_access` scope. To obtain an ID token request `openid profile email` in addition to any product specific scopes.

#### Changes to refresh tokens

Applications registered after 4th November 2024 will have refresh token rotation enabled. This means a single use fresh refresh token will be returned from the token endpoint, each time a fresh access token is requested. In addition, refresh tokens will be subject to an idle timeout of 15 days (half the overall lifetime of a refresh token). If a refresh token is not used within this period it will expire.

The connect-session library handles this as part of the `ReapitConnectBrowserSession` class. If your application manages it's own Reapit Connect session, ensure logic is in place to update the session's refresh token when using this endpoint. Using token rotation makes your applications more secure and keeps customer data safe.

#### Local Development

When developing client side applications locally that use the authorization code authentication flow, you may see a consent prompt appear if targeting a localhost address. This occurs because of additional security controls in place in the new identity provider. The easiest thing to do is to accept the prompt. Alternatively, we have update the DeveloperPortal to allow you to register redirect and signout URIs using http://dev.reapit. This can be configured as a local DNS entry added to your system's `hosts` file and will allow your app to be trusted so that the consent prompt is not displayed.

The hosts file can be found in the following locations depending on your operating system:

| Operating System | Hosts File Location                   |
| ---------------- | ------------------------------------- |
| Windows          | C:\Windows\System32\Drivers\etc\hosts |
| Linux            | /etc/hosts                            |
| MacOS            | /etc/hosts                            |

The format of the file is the same in each operating system. To add an entry for `dev.reapit`open the hosts file in an editor with Administrative permissions and add the following line (note: if you develop inside a container, for instance using Visual Studio Code with Ubuntu from a Windows machine, you should use the IP address of your container and NOT 127.0.0.1)

`127.0.0.1    dev.reapit`

Save the file and close the editor. Confirm your changes by running `ping dev.reapit`. You should see that domain resolve to `127.0.0.1`. Note that you may need to reboot to reload your hosts configuration, depending on your operating system.

If you are using our [Vite template](app-development/vite-template.md) you can update the server's configuration to open your browser automatically at`http://dev.reapit` by making the following changes to `vite.config.ts`

```typescript
server: {
    host: true,
    port: 8080
  },
```

to

```typescript
server: {
    host: true,
    port: 8080,
    open: 'http://dev.reapit:8080'
  },
```

Finally, update your app's configuration in the DeveloperPortal to use`http://dev.reapit` instead of `http://localhost`  for the redirect and signout urls.

### Machine to Machine flow Applications (server side)

#### Token caching

In response to developers not caching tokens locally, particularly where machine to machine applications are concerned, a server side caching layer has now been introduced. Repeated calls to `POST /oauth/token` will now return cached tokens where appropriate. The expiry of tokens is indicated by the `expires_in` property in the response payload. A five minute overlap is used in the server side caching layer to prevent any issues with imminently expiring tokens being returned back to your application. Only cached tokens with >= 5 minutes lifetime remaining will be returned, else a new access token will be issued. It is good practice to cache tokens locally to reduce round trips to the server.

#### Client secrets

Machine to machine applications will have a new secret generated as part of the migration. Old secrets will continue to work, however you are encouraged update your app to use the new secret and rotate your secrets regularly to keep your application secure.





### General Changes

#### Changes to URLs/Endpoints

When calling `POST /oauth/token` parameters should be sent in the request body and not as query string parameters.

There are some subtle changes to the endpoints used for signing users in/out and generating tokens. The compatibility layer takes care of redirecting these requests to the new identity provider in the background, but you are encouraged to make the following changes to your application code if required:

| Old URL/Path                           | New URL/Path                                 |
| -------------------------------------- | -------------------------------------------- |
| https://connect.reapit.cloud/oauth2/\* | https://connect.reapit.cloud/oauth/\*        |
| https://connect.reapit.cloud/token     | https://connect.reapit.cloud/oauth/token     |
| https://connect.reapit.cloud/login     | https://connect.reapit.cloud/oauth/authorize |
| https://connect.reapit.cloud/authorize | https://connect.reapit.cloud/oauth/authorize |
| https://connect.reapit.cloud/logout    | https://connect.reapit.cloud/oidc/logout     |



