sipgate Webphone Example
========================

Demo
----

You find a demo at [sipgate.github.io/sipgate-webphone-example/](https://sipgate.github.io/sipgate-webphone-example/).

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
<script src="https://phone.sipgate.com/static/js/webphone.js"></script>
```

Create a wrapping container:
```html
<div id='sipgate-webphone-container' style="height: 600px; width: 400px;"></div>
```

Initialize the Webphone:
```js
var webphone = new SipgateWebphone();
webphone.init({
  container: document.getElementById('sipgate-webphone-container'),
  clientId: 'CLIENT_ID'
});
```

You are now ready to start and receive calls. :tada:


Start a call using JavaScript
-----------------------------

You can use the `call(e164PhoneNumber)` method to start a call:
```js
webphone.call('+4915799912345'); // You have to provide a valid E164 phone number
```

Content-Security-Policy
-----------------------

If you configured your webserver to use the [Content-Security-Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) header, the webphone will not work. You need to add the following directive to your existing CSP header configuration:

```
script-src *.sipgate.com; frame-src *.sipgate.com;
```
