---
description: A singular component to enable auth with reapit
---

# Login With Reapit

The login With Reapit button is a singular stand alone component which can be utilised in any project on it's own. The component is written with Svelte which compiles Vanilla JS, CSS and HTML so are framework agnostic and be used with any other front end tech of your choosing.

### The Sign In With Reapit Button

The button leverages the Connect Session to handle the OAuth flow and returns a session object in a callback you provide.

<div align="center">

<img src="../.gitbook/assets/screenshot-2021-10-08-at-14.19.11.png" alt="Sign in With Reapit button">

</div>

The Component is a single script provided by NPM package, you instantiate with a target div, your client credentials as per the browser API and pass in a callback to receive your session object. As per the NPM module, all caching, redirection and refreshing is taken care of by the package. When you have a session, the button will change function to be a logout which will clear your cache and end your session in Reapit Connect.

### Agreeing to Permissions

When clicking the Sign In With Reapit button, a dialog window will appear with the following details

<div align="center">

<img src="../.gitbook/assets/screenshot-2021-10-08-at-14.19.03.png" alt="Agree to terms and permissions dialog">

</div>



#### Yarn

Use the script tag below in your code base to use the ReapitConnectComponent.

```markup
yarn add @reapit/login-with-reapit
```

#### NPM

Install the `login-with-reapit` package using npm.

```bash
npm i --save @reapit/login-with-reapit
```

Below is an example of how to use the `ReapitConnectComponent` . In the connectHasSessionCallback function we fetch a list of appointments from the Platform API to demonstrate the full flow. The  production `connectUserPoolId` is `eu-west-2_eQ7dreNzJ`.

### Single HTML page example

```javascript
<div id="reapit-connect-component"></div>

<script
  type="text/javascript"
  src="./node_modules/@reapit/login-with-reapit/public/dist/login-with-reapit.js"
></script>

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

  reapitConnectComponent && reapitConnectComponent({
    connectClientId: '<<clientId here>>>',
    connectUserPoolId: '<<userpool id here>>',
    connectOAuthUrl: 'https://connect.reapit.cloud',
    connectLoginRedirectPath: '',
    connectLogoutRedirectPath: '/login',
    rootElement: '#reapit-connect-component',
    connectHasSessionCallback,
    companyName: 'My Company',
  })
</script>
```

### ES6+ example

```javascript
import { reapitConnectComponent } from '@reapit/login-with-reapit'


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

reapitConnectComponent && reapitConnectComponent({
  connectClientId: '<<clientId here>>>',
  connectUserPoolId: '<<userpool id here>>',
  connectOAuthUrl: 'https://connect.reapit.cloud',
  connectLoginRedirectPath: '',
  connectLogoutRedirectPath: '/login',
  rootElement: '#reapit-connect-component',
  connectHasSessionCallback,
  companyName: 'My Company',
})
```

### rootElement

The `rootElement` property can be passed either query string, DOM element or shadow DOM element.

```javascript
reapitConnectComponent && reapitConnectComponent({
  connectClientId: '<<clientId here>>>',
  connectUserPoolId: '<<userpool id here>>',
  connectOAuthUrl: 'https://connect.reapit.cloud',
  connectLoginRedirectPath: '',
  connectLogoutRedirectPath: '/login',
  rootElement: document.getElementById('reapit-connect-component'),
  connectHasSessionCallback,
  companyName: 'My Company',
})
```

