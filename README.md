sipgate Webphone Example
========================

Quick Start
-----------

```shell
npm install
npm start
open localhost:5000
```


Slow Start
----------

Include the Webphone from sipgate's CDN:
```html
<script src="https://static.sipgate.com/js/webphone/v1/webphone.js"></script>
```

Create a wrapping container:
```html
<div id='sipgate-webphone-container' style="height: 600px; width: 400px;"></div>
```

Initialize the Webphone:
```js
var webphone = new SipgateWebphone();
webphone.init({
  deprecatedUsername: 'sipgateUsername', // This will be replaced with OAuth2 in future releases
  deprecatedPassword: 'sipgatePassword', // This will be replaced with OAuth2 in future releases
  container: document.getElementById('sipgate-webphone-container'),
});
```

You are now ready to start and receive calls. :tada:


Start a call using JavaScript
-----------------------------

You can use the `call(e164PhoneNumber)` method to start a call:
```js
webphone.call('+4915799912345'); // You have to provide a valid E164 phone number
```
