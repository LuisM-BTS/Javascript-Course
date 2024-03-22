

# JavaScript Project README

This project covers various concepts and features in JavaScript, including ES6 modules, top-level `await` (ES2022), the module pattern, CommonJS modules, and introduction to NPM.

## ES6 Modules

The project demonstrates how to import and export functionalities using ES6 modules. It covers different import methods, such as named imports, default imports, and importing everything as an object.

```javascript
// Example code for ES6 Modules
import { addToCart, totalPrice as price, tq } from './shoppingCart.js';
addToCart('bread', 5);
console.log(price, tq);
```

## Top-Level Await (ES2022)

This part showcases the usage of top-level `await` introduced in ES2022. It includes an example of fetching data asynchronously and using `await` outside of an async function.

```javascript
// Example code for Top-Level Await
const getLastPost = async function () {
  const res = await fetch('https://jsonplaceholder.typicode.com/posts');
  const data = await res.json();

  return { title: data.at(-1).title, text: data.at(-1).body };
};

const lastPost2 = await getLastPost();
console.log(lastPost2);
```

## The Module Pattern

This section demonstrates the module pattern in JavaScript, a way to encapsulate private and public methods and variables within a module.

```javascript
// Example code for The Module Pattern
const ShoppingCart2 = (function () {
  const cart = [];
  const shippingCost = 10;
  const totalPrice = 237;
  const totalQuantity = 23;

  const addToCart = function (product, quantity) {
    cart.push({ product, quantity });
    console.log(
      `${quantity} ${product} added to cart (sipping cost is ${shippingCost})`
    );
  };

  return {
    addToCart,
    cart,
    totalPrice,
    totalQuantity,
  };
})();

ShoppingCart2.addToCart('apple', 4);
console.log(ShoppingCart2);
```

## CommonJS Modules

This section introduces CommonJS modules, a module system for JavaScript used in Node.js environments.

```javascript
// Example code for CommonJS Modules
const { addToCart } = require('./shoppingCart.js');
```

## Introduction to NPM

This part covers the basics of NPM (Node Package Manager), including installing and using packages, such as lodash-es for deep cloning objects.

```javascript
// Example code for Introduction to NPM
import cloneDeep from 'lodash-es';
```



# JavaScript Parcel Bundler Configuration

This project provides a basic understanding of how to configure and use Parcel Bundler for JavaScript projects. It includes the setup for handling modules and dependencies using Parcel Bundler.(path : /dist/index.js)

## Parcel Bundler Configuration

The provided code snippet defines the Parcel Bundler configuration for handling modules and dependencies in a JavaScript project. It includes a function for loading modules and resolving dependencies.

```javascript
// modules are defined as an array
// [ module function, map of requires ]
//
// map of requires is short require name -> numeric require
//
// anything defined in a previous bundle is accessed via the
// orig method which is the require for previous bundles
parcelRequire = (function (modules, cache, entry, globalName) {
  // Save the require from previous bundle to this closure if any
  var previousRequire = typeof parcelRequire === 'function' && parcelRequire;
  var nodeRequire = typeof require === 'function' && require;

  // Define newRequire function to load modules and resolve dependencies
  function newRequire(name, jumped) {
    if (!cache[name]) {
      if (!modules[name]) {
        // If module not found in the internal map or cache, attempt to load from previous bundle or node require
        var currentRequire = typeof parcelRequire === 'function' && parcelRequire;
        if (!jumped && currentRequire) {
          return currentRequire(name, true);
        }
        if (previousRequire) {
          return previousRequire(name, true);
        }
        if (nodeRequire && typeof name === 'string') {
          return nodeRequire(name);
        }
        // Throw error if module not found
        var err = new Error('Cannot find module \'' + name + '\'');
        err.code = 'MODULE_NOT_FOUND';
        throw err;
      }

      // Define localRequire function to resolve and load modules
      localRequire.resolve = resolve;
      localRequire.cache = {};

      var module = cache[name] = new newRequire.Module(name);

      modules[name][0].call(module.exports, localRequire, module, module.exports, this);
    }

    return cache[name].exports;

    function localRequire(x){
      return newRequire(localRequire.resolve(x));
    }

    function resolve(x){
      return modules[name][1][x] || x;
    }
  }

  // Define Module constructor to encapsulate module information
  function Module(moduleName) {
    this.id = moduleName;
    this.bundle = newRequire;
    this.exports = {};
  }

  // Set newRequire properties and methods
  newRequire.isParcelRequire = true;
  newRequire.Module = Module;
  newRequire.modules = modules;
  newRequire.cache = cache;
  newRequire.parent = previousRequire;
  newRequire.register = function (id, exports) {
    modules[id] = [function (require, module) {
      module.exports = exports;
    }, {}];
  };

  var error;
  for (var i = 0; i < entry.length; i++) {
    try {
      newRequire(entry[i]);
    } catch (e) {
      // Save first error but execute all entries
      if (!error) {
        error = e;
      }
    }
  }

  if (entry.length) {
    // Expose entry point to Node, AMD or browser globals
    var mainExports = newRequire(entry[entry.length - 1]);

    if (typeof exports === "object" && typeof module !== "undefined") {
      module.exports = mainExports;
    } else if (typeof define === "function" && define.amd) {
      define(function () {
        return mainExports;
      });
    } else if (globalName) {
      this[globalName] = mainExports;
    }
  }

  // Override the current require with this new one
  parcelRequire = newRequire;

  if (error) {
    // throw error from earlier
    throw error;
  }

  return newRequire;
})({});

```

## Parcel Bundler Built-ins

Additionally, the project includes built-ins for handling CSS loading and Hot Module Replacement (HMR) runtime.

```javascript
// CSS Loader
var reloadCSS = require('./css-loader');

// HMR Runtime
var global = arguments[3];
var OldModule = module.bundle.Module;

// Function for creating and managing modules
function Module(moduleName) {
  OldModule.call(this, moduleName);
  this.hot = {
    data: module.bundle.hotData,
    _acceptCallbacks: [],
    _disposeCallbacks: [],
    accept: function (fn) {
      this._acceptCallbacks.push(fn || function () {});
    },
    dispose: function (fn) {
      this._disposeCallbacks.push(fn);
    }
  };
  module.bundle.hotData = null;
}

module.bundle.Module = Module;
```

---
