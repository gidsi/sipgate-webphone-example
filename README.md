# sipgate Webphone Example

The sipgate webphone is a fully fledged VoIP client running inside your browser. With the API you can use it so simply add telephony functionality to your own application.

## Demo

You find a demo at [sipgate.github.io/sipgate-webphone-example/](https://sipgate.github.io/sipgate-webphone-example/).


## Quick Start

```shell
npm install
npm start
open localhost:5000
```


## Slow Start

Include the Webphone from sipgate's CDN:
```html
<script src="https://phone.sipgate.com/static/js/webphone.js"></script>
```

Create a wrapping container:
```html
<div id='sipgate-webphone-container' style="height: 600px; width: 400px;"></div>
```

Get a *client ID* by [filling out the form](https://goo.gl/ePNNXz).

Initialize the webphone with your client ID:
```js
var webphone = new SipgateWebphone();
webphone.init({
  container: document.getElementById('sipgate-webphone-container'),
  clientId: 'CLIENT_ID'
});
```



You are now ready to start and receive calls. :tada:


## Start a call using JavaScript

You can use the `call(e164PhoneNumber)` method to start a call:
```js
webphone.call('+4915799912345'); // You have to provide a valid E164 phone number
```

## Call events

Once the webphone is initialized you can receive and handle events to e.g. augment the phone's UI with additional data.

### Ring incoming

When the phone is ringing to signalise an incoming call, you will receive a `ringIncoming` event. You can handle it like this:

```js
webphone.on('ringIncoming', function(meta){ console.log('ringing incoming from ' + meta.remote); });
```

### Dialing

When the phone is dialing to establish an external call, you will receive a `dial` event. You can handle it like this:

```js
webphone.on('dial', function(meta){ console.log('dialing to ' + meta.remote); });
```

### Ring outgoing

When the phone is ringing while trying to establish an external call, you will receive a `ringOutgoing` event. You can handle it like this:

```js
webphone.on('ringOutgoing', function(meta){ console.log('ringing outgoing to ' + meta.remote); });
```

### Speak

When a call is established, you will receive a `speak` event. You can handle it like this:

```js
webphone.on('speak', function(meta){ console.log('speaking to ' + meta.remote); });
```

### End

When a call or call attempt is ended, you will receive an `end` event. You can handle it like this:

```js
webphone.on('end', function(){ console.log('call ended'); });
```


## Content-Security-Policy

If you configured your webserver to use the [Content-Security-Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) header, the webphone will not work. You need to add the following directive to your existing CSP header configuration:

```
script-src *.sipgate.com; frame-src *.sipgate.com;
```
