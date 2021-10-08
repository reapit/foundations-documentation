---
description: Lightweight Components to enhance your existing site
---

# Web Components

In addition to the Elements React component toolkit, Reapit will soon be offering a number of other distributed web components.

These may be modular blocks of functionality that can be embedded within your site, toolsets or even CMS friendly bundles of scripts available elsewhere. The guiding principles of the project is that the components should be standalone, highly customisable and lightweight. They are written in Svelte which compiles to Vanilla JS, CSS and HTML so are framework agnostic and can be used with any other front end tech of your choosing.

All web components are served both as NPM packages and as downloadable scripts from our CDN. These are under active development by our team with an Alpha release in the coming months. You can check on progress [here.](https://github.com/reapit/foundations/milestone/6)

### Sign In With Reapit

The first component we have shipped is a small but powerful "Sign In With Reapit" button. The button leverages the Connect Session to handle the OAuth flow and returns a session object in a callback you provide.

![Sign in With Reapit button](../.gitbook/assets/screenshot-2021-10-08-at-14.19.11.png)

The Component is a single script served from our CDN or NPM package, you instantiate with a target div, your client credentials as per the browser API and pass in a callback to receive your session object. As per the NPM module, all caching, redirection and refreshing is taken care of by the package. When you have a session, the button will change function to be a logout which will clear your cache and end your session in Reapit Connect.

#### Agreeing to Permissions

When clicking the Sign In With Reapit button, a dialog window will appear with the following details

![Agree to terms and permissions dialog](../.gitbook/assets/screenshot-2021-10-08-at-14.19.03.png)



#### CDN

Use the script tag below in your code base to use the ReapitConnectComponent.

```markup
<script src="https://web-components.prod.paas.reapit.cloud/reapit-connect-component.js"></script>
```

#### NPM

Install the `login-with-reapit` package using npm.

```bash
npm i --save @reapit/login-with-reapit
```

Below is an example of how to use the `ReapitConnectComponent` using the CDN. The below example shows how to embed on any static or dynamic page with a single script. In the connectHasSessionCallback function we fetch a list of appointments from the Platform API to demonstrate the full flow. The  production `connectUserPoolId` is `eu-west-2_eQ7dreNzJ`.

```markup
<div id="reapit-connect-component"></div>
<script src="https://web-components.prod.paas.reapit.cloud/reapit-connect-component.js"></script>
<script>
  const connectHasSessionCallback = (reapitConnectBrowserSession) => {
    reapitConnectBrowserSession.connectSession().then(session => {
      console.log('Session is', session)
      fetch('https://platform.reapit.cloud/appointments', {
        headers: {
          'Content-Type': 'application/json',
          'Authorization': `Bearer ${session.accessToken}`,
          'api-version': '2020-01-31'
        }
      })
      .then(res => res.json())
      .then(appointments => console.log('Appointments are', appointments))
    })
  }

  ReapitConnectComponent && new ReapitConnectComponent({
    connectClientId: '<<clientId here>>>',
    connectUserPoolId: '<<userpool id here>>'
    connectOAuthUrl: 'https://connect.reapit.cloud',
    connectLoginRedirectPath: '',
    connectLogoutRedirectPath: '/login',
    rootElement: '#reapit-connect-component',
    connectHasSessionCallback,
    companyName: 'My Company',
  })
</script>
```

### Search Component

Coming soon...

### Book a Valuation Component

Coming soon...

### Book a Viewing Component

Coming soon...

