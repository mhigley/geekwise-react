---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 2: Continuation of ES6

## Getting started

In order to be able to use all of the new features in the Node REPL we will
have to start up Node with the following wacky command:
```bash
$ node $(node --v8-options | awk '/harmony/ && $1 ~ /^--/{print $1}')
```

What this is going to do is start up the Node REPL with every possible
harmony flag. You can look at what these are by just typing:
```bash
$ node --v8-options
```

This is really only necessary for the purposes of us getting familiar with
all of these new features from within the Node REPL.

If you're using Windows, well, this isn't going to work. We will just have to
start your Node REPL with the flags that we need. :(

So for now just start up Node like this:
```bash
> node --harmony-spread-arrays --harmony-spreadcalls
```

### Default Parameters

Another great feature of ES6 is that you can define default parameters in
your function declarations. Take this code for example:

```js
var addNumbers = function(number, otherNumber) {
  if (otherNumber === undefined) otherNumber = 2
  return number + otherNumber
}
```

Using default parameters, we can now rewrite that like this:

```js
var addNumbers = function(number, otherNumber = 2) {
  return number + otherNumber
}
```

### Spread Operators

Spread operators are another thing that come in extremely handy when
creating React components. I'll go over these briefly right now just so
we have a basic understanging.

Imagine we have an object:
```js
var car = {
  make: 'Toyota',
  model: 'Corolla'
}
```

If we were to put this into a React component:
```js
<Car {...car} />
```

This would be the equivalent of saying:
```js
<Car make={car.make} model={car.model} />
```

It's just some nice, convenient shorthand that comes in quite handy in a lot
of cases. Especially in re-usable components.

### For..Of

This is another nice feature, that has actually made it's way into most
browsers already. It allows you to easily loop through an array:
```js
var a = [1, 2, 3]
for (var n of a) {
  console.log(n)
}
```

Just a bit of really nice shorthand that makes looping easier.

### forEach and map

These are also a few that are already in browsers but don't get a lot of
attention.

```js
var a = [1, 2, 3]
a.forEach((num, index) => console.log(num, index))
```

```js
var a = [1, 2, 3]
a.map((num) => num + 1)
console.log(a)
```

### Classes

New in ES6 is the ability to create your own classes. Classes support
inheritance, super calls, instance and static methods, and constructors.

Let's create a class that we can work with:

```js
class Car {
  constructor(make, model, year) {
    this.make = make
    this.model = model
    this.year = year
  }

  name() {
    return `${this.year} ${this.make} ${this.model}`
  }
}

let myCar = new Car("Toyota", "Highlander", "2003")
console.log(myCar.name())
```

You can also inherit from other classes. Let's make a new class called
`Vehicle` that will hold common information:

```js
class Vehicle {
  constructor(make, model, year) {
    this.make = make
    this.model = model
    this.year = year
  }

  get name() {
    return `${this.year} ${this.make} ${this.model}`
  }
}

class Car extends Vehicle {
  get type() {
    return 'Car'
  }
}

class Truck extends Vehicle {
  get type() {
    return 'Truck'
  }
}

let myCar = new Car("Toyota", "Highlander", "2003")
let myTruck = new Truck("Toyota", "Tacoma", "2005")

console.log(myCar.name)
console.log(myCar.type)
console.log(myTruck.name)
console.log(myTruck.type)
```


### Modules

In ES6, we can easily import modules using, you guessed it, the `import` syntax.
It looks something like this:

```js
import React from 'react'
```

So, the React module `exports` a `React` class, probably something like this:

```js
export default React
```

When we say `export default` in a module, we are saying that if you do not
specify which `export` to `import` (strange language, I know), then you'll
get the default. If we were to export things in this fashion:

```js
export default React

export Container
```

Then we could import like this:

```js
import React, { Container } from 'react'
```

Yup, you can use destructuring during an import too. Awesome!
