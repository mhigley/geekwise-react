---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 4: Finishing user registration

## Setting up

Everyone will need to clone my Day 4 branch from the geekbook repository.

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-4
```

Then you'll need to npm install again:

```bash
$ npm install
```

If all goes well, you should be able to start the server and see the fancy
new styles:

```bash
$ npm start
```

## Testing review

Last week we ran into a few problems while testing the login component. The
issue lied in that when we were simulating a click on the `submit` button
the React testing utils were not allowing the form to be submitted. I personally
think this is probably good behavior, as it allows us to really isolate our
test cases in a black box.

Let's open up the test file and discuss the changes I made to make this work
properly.

## The registration form

We've taken the login form about as far as we can at this point. There isn't a
good reason to implement any further functionality at this point, since there
isn't a user in the system to login with. So let's create the registration
functionality.

### Form Validation

We're going to need to validate this form, as all fields are required, and
one is required to be a confirmation field. This is going to add a bit of
complexity to our form. We're going to need to break this into pieces and do
some testing so that we can get our functionality dialed in.

*Discuss:*
  * What duplication do we have so far?
  * How can we reduce this duplication?

*Exercise:* Refactor the registration component to remove duplication.

Now we have some basic input components, but they need to be able to display
validation errors, and of course, perform validations. Let's implement that.

*Discuss:* What should validation errors look like, and how do we validate the components?

*Exercise:* Create the validations, and write tests for the input components

So now that we have some basic form components, let's implement some validation.
I think we should create a form component for this, so let's do that and test
it.

*Discuss:*
  * What does the form component need to do?
  * What tests do we need to write?

*Exercise:* Implement the form component with tests (pair programming)

### Controlled and uncontrolled components

React has the notion of `controlled` and `uncontrolled` components. When creating
input components it makes a big difference whether you use `value` or `defaultValue`
as the component attribute. When you use the `value` attribute to set an initial
value on a component, it becomes a `controlled` component. What this means is
that the value cannot be changed via user input. The value can *ONLY* be updated
programatically. An `uncontrolled` component however does not have these
restraints. You can still set an initial value for an input by using the
`defaultValue` attribute and the component will remain an `uncontrolled`
component.

## Introducing GraphQL

The backend server is a GraphQL server. We'll be writing our queries using the
[GraphQL](https://facebook.github.io/graphql/) query language. This is a very
powerful query language that will allow us, the consumer of an API, to be
able to request exactly the data we need from the API, and only the data we
need. All from a single API endpoint.

A simple GraphQL query that we might use could look like this:

```js
query {
  user(id: 1234) {
    email
  }
}
```

You'll notice that this looks a lot like a JavaScript object, but with only keys.
This is how you structure a GraphQL query. You tell the server what record
you are looking for, in this case a `User` with an id of `1234`. Then we tell
the server that we're only looking for the email of that user.

Let's jump into Postman and play with this a bit.
