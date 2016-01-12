---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 1: The Basics

## Who is everyone?

### About me

- I've been a web developer for about 2 1/2 years
- Started with Ruby/Rails, but have been full time (mostly) with React for the last 9 months
- I currently work for [Edit LLC](http://editllc.com/) doing a variety of things
- I have built an app called [FermentAble](https://www.getfermentable.com) that is using React on the front end
- Email: dphaener at gmail dot com
- Slack: https://geekwise-academy-frs.slack.com

### About Jason

- Web developer for 8 years
- Started with Django, now using React full time for the last year
- I work with Daren at [Edit LLC](http://editllc.com/)
- Email: zbyte64 at gmail dot com

### Student Intros

- What's your name?
- What's your career background?
- What technologies do you have experience with?
- What do you hope to get out of this class?

## Tools

### ES6

We will be developing all of our React components using the new
[ES6](https://babeljs.io/docs/learn-es2015/) specification for JavaScript.
ES6 provides us with lot's of nifty new features that we'll be exploring
during this class.

This flavor of JS has not yet been adopted fully by most browsers, so
we will have to use [Babel](https://babeljs.io) to transpile our ES6 down
to browser compatible ES5.

### NPM

NPM is one of the package managers for JavaScript. It has a ton of modules
and is very well supported, so we will be using it for this class.

### Text Editor

Any text editor will do:

- I prefer Vim these days
- [Sublime Text](http://www.sublimetext.com/)
- [Atom](https://atom.io)

### Version Control (Git)

- We will be using Git + GitHub exclusively for version control in this course
- You don't have to be a git expert right off the bat
- Learn commands as you go, eventually you will "commit" them to memory (pun intended)
- Resources:
    - [Pro Git](http://git-scm.com/book) (free online book)
    - [Code School + GitHub's Try Git](http://try.github.io/) (interactive tutorial)
- Have we all heard of [GitHub](https://github.com)?

## Development Environment

### Node

We will be using Node 5.4 in this class. For those of you that do not have
node installed, let's get that done right now.

#### Mac OSX/Linux
I highly recommend using [NVM](https://github.com/creationix/nvm) to manage
and install your Node versions. Using homebrew you'll get 0.12.7, which is
not what we want.

There are two ways to install NVM:
```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```
or
```bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```

The script clones the nvm repository to `~/.nvm` and adds the source line
to your profile (`~/.bash_profile`, `~/.zshrc` or `~/.profile`).

Once you have successfully installed NVM, all you need to do now is install
node:
```bash
nvm install 5.4
```

#### Windows
You're on your own. Just kidding.

Go to the [NodeJS](https://nodejs.org/en/) website and download the installer.
Then use the installer to install Node.

## Getting Started with ES6

Open up your terminal and fire up the Node REPL:
```bash
$ node $(node --v8-options | awk '/harmony/ && $1 ~ /^--/{print $1}')
```

That command will load all the harmony(ES6) options, which is needed for us to
be able to explore all of these things in the Node REPL.

If you're using Windows, this isn't going to work, so let's just grab the flags
that we need for today:

```bash
> node --harmony-destructuring --harmony-arrow-functions --harmony-default-parameters
```

### String Interpolation

ES6 now supports string interpolation, meaning we no longer need to do this:

```js
var s = 'Foo' + bar + 'Baz'
```

Interpolation works by surrounding your string with backticks instead of
quotes.

```js
var s = `Foo ${bar} Baz`
```

As you can see, we use the `${}` notation to interpolate. Anything inside
the brackets will be interpreted, so you can not only put variables inside,
but you can perform operations:

```js
console.log(`Four plus five equals ${4 + 5}`)
```

### Arrow Functions

Arrow functions are a shorthand for defining a function, plus as a bonus,
it automatically binds `this` to the function. So there's no more of this:

```js
this.number = 2
var self = this

var addNumbers = function(number) {
  return self.number + number
}
```

That now simply becomes:

```js
this.number = 2

var addNumbers = (number) => {
  return this.number + number
}
```

Pretty neat huh?

If the function is just one line, you can write it like this:
```js
var addNumbers = (x) => (
  x + 2
)
```

Notice how we replaced the curly braces with parens? That means two things:
1. That the function can only have *one* line of code.
2. That the function is going to implicitly return the result of that one line.

So there's no need for a return. Awesome!

Also, if it's just a one liner like above, you can write that function like this:

```js
var addNumbers = x => x + 2
addNumbers(2)
=> 4
```

We're going to see the first type of function used quite a bit in this class
in the form of `Function Components` which will look something like this:

```js
export default ({ name, message, sender }) => (
  <div>
    <span className='name'>Hello {name}</span>
    <span className='message'>{sender} wanted to tell you that {message}</span>
  </div>
)
```

That may look a bit weird right now, but by the end of this class you'll be
whipping out these stateless components like it's second nature.

### Destructuring

One of the weird things you may have noticed from the code sample above
is the function declaration:
```js
export default ({ name, message, sender }) => (
```

What we're doing there is called parameter destructuring. This function
expects an object to be passed in as a parameter that looks like:
```js
{
  name: 'Darin',
  message: 'You learned React',
  sender: 'Jason'
}
```

It will then assign the variables `name`, `message`, and `sender` to the
value of the keys in that object. If the keys don't exist, the variables
will be `undefined`.

Let's try it out in the REPL:
```js
let foo = { a: "1", b: "2" }
let { a, b } = foo
console.log(a, b)
```
