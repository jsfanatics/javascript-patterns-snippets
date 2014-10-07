JavaScript Patterns Snippets
============================
Useful JavaScript Patterns Snippets for Sublime Text

## Constructor pattern

**trigger**: constructor⇥

That constructor pattern enforces the use of `new`, even if you call the
constructor like a function. In JavaScript, if the `new` keyword is forgotten,
`this` will reference the global object inside the constructor, and that's never
a desirable situation.

That approach is like `$()` and `$.Deferred()` in jQuery, where you can call
it in the same way with `new $()` and `new $.Deferred`.

```javascript
var ConstructorName = (function() {
  'use strict';

  function ConstructorName(arg1, arg2) {
    // enforces new
    if (!(this instanceof ConstructorName)) {
        return new ConstructorName();
    }

    // constructor body
  }

  ConstructorName.prototype.someMethod = function(arg) {
    // method body
  }

  return ConstructorName;

}());
```

Reference:
- [Object Creation patterns](http://www.jspatterns.com/category/patterns/object-creation/)


## Singleton pattern

**trigger**: singleton⇥

With the Singleton pattern there will be only one instance of a constructor
function. If you try to instantiate another one, the first instance that was
created at first will be returned.

```javascript
var singletonName = (function() {
  'use strict';

  var instance;

  singletonName = function() {
    if (instance) {
      return instance;
    }

    instance = this;

    // your code goes here
  };

  return singletonName;

}());

```

Reference:
- [Singleton Pattern - Simples Ideias](http://simplesideias.com.br/design-patterns-no-javascript-singleton)

## Module

<<<<<<< HEAD
**trigger**: module⇥

A simple module pattern. Uses strict mode and suggest the use of a `init`
function for kickoff. Also possible to define some "private" methods and
variables. Only the variable with the module's name is returned and therefore
made public outside the closure.

```javascript
var moduleName = (function() {
  'use strict';

  var privateVar = '';

  var moduleName = {
    init: {
      // kickoff
    }
  }

  return moduleName;

}());
```

Reference:
- [JavaScript Module Pattern: In-Depth](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)


## Revealing module

**trigger**: rmodule⇥

Some might say it's a less verbose and more organized way to define a module.
It declares all the variables and functions in the private scope and returns
an object with references to what is going to be public.

```javascript
var revealingModule = (function(){
  'use strict';

  var privateVar = 'foo';
  var publicVar = 'bar';

  function privateFunction() {

  }

  function publicFunction() {

  }

  return {
    publicVar: publicVar,
    publicFunction: publicFunction
  };
}());
```
=======
## Module
>>>>>>> pr/3

**trigger**: module⇥

A simple module pattern. Uses strict mode and suggest the use of a `init`
function for kickoff. Also possible to define some "private" methods and
variables. Only the variable with the module's name is returned and therefore
made public outside the closure.

```javascript
var moduleName = (function() {
  'use strict';

  var privateVar = '';

  var moduleName = {
    init: {
      // kickoff
    }
  }

  return moduleName;

}());
```

Reference:
- [JavaScript Module Pattern: In-Depth](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)


## Revealing module

**trigger**: rmodule⇥

Some might say it's a less verbose and more organized way to define a module.
It declares all the variables and functions in the private scope and returns
an object with references to what is going to be public.

```javascript
var revealingModule = (function(){
  'use strict';

  var privateVar = 'foo';
  var publicVar = 'bar';

  function privateFunction() {

  }

  function publicFunction() {

  }

  return {
    publicVar: publicVar,
    publicFunction: publicFunction
  };
}());
```

## Memoization

Caches the return value of function. Useful for repetitive calls for a
computationally expensive function.

```javascript
var expensiveFunction = (function() {
  'use strict';

  var funcMemoized = function() {
    var cacheKey = JSON.stringify(Array.prototype.slice.call(arguments));
    var result;

    if (!funcMemoized.cache[cacheKey]) {
        // your expensive computation goes here

        funcMemoized.cache[cacheKey] = result;
    }

    return funcMemoized.cache[cacheKey];
  }

  funcMemoized.cache = {};

  return funcMemoized;
}());
```
