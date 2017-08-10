# ServiceWorkerRegister

A [class expression mixin](https://www.polymer-project.org/2.0/docs/devguide/custom-elements#mixins) to register and manage a service worker

## Notes
- Your `service-worker.js` *must* be located at the top-level directory relative to your site.
- It won't be able to control pages unless it's located at the same level or higher than them.
- *Don't* register service worker file in, e.g., a scripts/ sub-directory!
- See https://github.com/slightlyoff/ServiceWorker/issues/468

## Usage 

### Install
`bower i ryanburns23/service-worker-register -S`

### Import the class expression mixin
```html
<link rel="import" href="../bower_components/service-worker-register/service-worker-register.html">
```

### Add ServiceWorkerRegister to your element
```javascript
class MyElement extends ServiceWorkerRegister(Polymer.Element) {
  static get is() { return 'my-element' }
}
```
This creates a new class defined by the `ServiceWorkerRegister` factory, so the inheritance hierarchy is
```javascript
MyElement <= ServiceWorkerRegister(Polymer.Element) <= Polymer.Element
```

### Listen & Respond to Events
ServiceWorkerRegister distpatches the following events: 
- `service-worker-update-available`: At this point, the old content will have been purged and the fresh content will have been added to the cache. It's the perfect time to display a "New content is available; please refresh." message in the page's interface.
- `service-worker-content-cached`: At this point, everything has been precached. It's the perfect time to display a "Content is cached for offline use." message.

### Example:
```javascript
window.addEventListener('service-worker-update-available', e => this._handleServiceWorkerUpdate(e));
window.addEventListener('service-worker-content-cached', e => this._handleServiceWorkerInstall(e));

_handleServiceWorkerUpdate(){
  // display update message
}
_handleServiceWorkerInstall(){
  // display install message
}
```

## Credits
- [GoogleChrome/sw-precache/demo/app/js/service-worker-registration.js](https://github.com/GoogleChrome/sw-precache/blob/master/demo/app/js/service-worker-registration.js)