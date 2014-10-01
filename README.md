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



