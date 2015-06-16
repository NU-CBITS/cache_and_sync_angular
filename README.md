# Cache and Sync library

Provides simple local storage cache and synchronization functionality for
Angular 1.X applications.

## Usage

Cache resources in local storage

```javascript
(function() {
  'use strict';

  function PicnicBasketCache(cache) {
    this.KEY = 'picnicBaskets';

    cache.delegate(this, 'persist');
    cache.delegate(this, 'fetchAllDirty');
    cache.delegate(this, 'markClean');
  }

  function PicnicBasketCacheFactory(cache) {
    return new PicnicBasketCache(cache);
  }

  angular.module('myApp.services')
         .factory('picnicBasketCache',
                  ['resourceCache', PicnicBasketCacheFactory]);
})();
```

Start periodic synchronization of specific caches.

```javascript
synchronizer.registerCache(picnicBasketCache);
synchronizer.run();
```
