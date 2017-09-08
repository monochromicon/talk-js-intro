# JavaScript Introduction
> It'll only sting for a moment.

```js
0 >= null
0 == null
0 > null
```

JavaScript's flexibility will hurt to adapt to, but it is not a bad thing.

> I also have grown to like the prototypical nature of JavaScript and other prototypical languages like Lua.  I’ve always been a big fan of statically typed languages, and I still am, but I can also now appreciate some of the patterns that only a prototypical language allows which can really allow you to do quite a bit with just a little code.
>
> [John Sonmez, "I Was Wrong About JavaScript and Responsive Design"](https://simpleprogrammer.com/2013/12/09/wrong-javascript-responsive-design/) in Dec 2013

And even better said:

> > “Whilst not conclusive, the lack of evidence in the charts that more advanced type languages are going to save us from writing bugs is very disturbing.” 
> >
> > Daniel Lebrero, “The Broken Promise of Static Typing”
>
> [Eric Elliott, "The Shocking Secret About Static Types"](https://medium.com/javascript-scene/the-shocking-secret-about-static-types-514d39bf30a3) in Jun 2016

## Topics

Important topics for the future.

- [ ] project directory structure
- [ ] bundling JS
- [ ] ecmascript 2015/2016/2017
- [ ] web apps and react/vdom
- [ ] typescript

This intro will only discuss language quirks.

- [x] addition operator
- [x] truthiness
- [x] triple equals
- [x] template strings
- [x] this
- [x] not using classes

---
## Addition Operator
> Do not thy non-numbers add.

```js
{} + []
[] + {}
[] + []
[] + [] + {}
'i am a ' + {}
```

The addition operator either performs string concatenation or numeric addition.

Take away: don't add non-numbers.

---
## Truthiness
> Existence is truth.

Truthiness is the process of simplifying any value to `true` or `false`, like during `if` statements.

```js
Boolean(false)
Boolean(0)
Boolean(-0)
Boolean('')
Boolean(null)
Boolean(undefined)
Boolean(NaN)
```

Everything else is truthy. This makes for some useful shortcuts, like when using the ternary operator to define a default value.

```js
const foo = ''
const bar = 'bar'
// if foo is truthy then return foo else return 'baz'
foo ? foo : 'baz'
// if bar is truthy then return bar else return 'baz'
bar ? bar : 'baz'
```

The Boolean operators work fine for `if` conditions, but also function as null-coalescing operators too.

```js
true || 'baz'
false || 'baz'
```

```js
true && 'baz'
false && 'baz'
```

In functions with optional parameters, a developer should prefer to test truthiness instead of type unless types need to be distinguished.

```js
function print (msg) {
  if (typeof msg !== 'undefined') {
    console.info(msg)
  }
}
```

```js
function print (msg) {
  if (msg) console.info(msg)
}
```

---
## Triple Equals
> Strict equivalence does not strictly equal loose equivalence.

`==` in JS is not the same as `==` in any other language.

Using `==` in JS is a loose comparison. `===` is the strict comparison similar to other languages.

All you should know about `==` is that it will go out of its way to make the left and right hand sides the same type. `==` should only be used for code golf.

![](6BYGcfx.jpg)

---
## Template Strings
> Just use them please.

If you shouldn't use the addition operator to build strings, how should you?

```js
const thing = 'message'
`this is my ${thing}`
```

---
## Functions
> What is this?

```js
function fn () {
  console.info('called')
}
```

Normal stuff going on here. Ready for the not-normal stuff?

```js
function another () {
  return this
}

another() // global scope returns

const obj = {another}
obj.another() // obj returns

const fn1 = obj.another
a1() // global scope returns

const fn2 = obj.another.bind(obj)
a2() // obj returns
```

---
## Classes
> Just because it is familiar does not mean it is better.

```js
class Foo {
  constructor () {
    this.val = 0
  }
  inc () {
    this.val++
  }
  dec () {
    this.val--
  }
}

const f = new Foo()
f.val
f.inc()
f.val
```

Classes tend to cause anti-patterns in JS, though.

- The lack of strict typing lends to functional code, not object-oriented.
- Most all frameworks for JS save state and you don't need to.
- The performance benefit isn't worth the technical debt and bloat.
- Most of the time, the dev+user of your class will not get IntelliSense.
- Tend to lead to articles titled "How to Use Classes and Sleep at Night"

It is often better to simply have functions that accept all of the state they need as parameters. This will also make unit testing easier and better compartmentalize the codebase.

```js
const inc = val => val + 1
const dec = val => val - 1

const initVal = 0;
const nextVal = inc(initVal);
const lastVal = dec(nextVal);
```

---
This is where I want to fill you my opinions.

- Use a debugger.
- Prefer `const` everywhere.
- Don't use classes.
- Don't use globals or namespaces.
- Write functional code (accept a state, return a new state).
- Use promises, streams, events, and callbacks, in that order.
- Observables are good but I haven't used them.
- https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript

Never stop learning and write code in peace.

|[![](https://github.com/maccelerated.png?size=100)](https://github.com/maccelerated)|
|---|
|[@maccelerated](https://github.com/maccelerated)|
