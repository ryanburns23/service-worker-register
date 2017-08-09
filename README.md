# service-worker-register

A [class expression mixin](https://www.polymer-project.org/2.0/docs/devguide/custom-elements#mixins) to register and manage a service worker

## Usage 

Install `ServiceWorkerRegister`
`bower i ryanburns23/service-worker-register -S`

Import the `ServiceWorkerRegister` class expression mixin
```html
<link rel="import" href="../bower_components/service-worker-register/service-worker-register.html">
```

Add ServiceWorkerRegister to your element like this:
```javascript
class MyElement extends ServiceWorkerRegister(Polymer.Element) {
  static get is() { return 'my-element' }
}
```

This creates a new class defined by the `ServiceWorkerRegister` factory, so the inheritance hierarchy is:
```javascript
MyElement <= ServiceWorkerRegister(Polymer.Element) <= Polymer.Element
```

### Handle Events
`ServiceWorkerRegister` distpatches the following events: 

TODO: Write event docs


## Credits
- [GoogleChrome/sw-precache/demo/app/js/service-worker-registration.js](https://github.com/GoogleChrome/sw-precache/blob/master/demo/app/js/service-worker-registration.js)