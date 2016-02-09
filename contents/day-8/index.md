---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 8: Persisting Likes

## Setting up

We'll begin developing on the Day 8 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-8
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-8
```

## Persisting the like state

In the last class we added the ability to `like` and `unlike` a post. Unfortunately
this isn't persisted to the database so our likes aren't remembered. Let's
fix that.

## GraphQL Mutations

So far, we've used a GraphQL query to fetch data, but now we're going to need
to take that a step further and be able to mutate data. In the CRUD world
this is known as an `update`, and would normally be acheived by sending
a `put` request. But with our GraphQL server everything is a `post` request.

We'll be sending a query that looks like this:

```js
mutation {
  likePostMutation(id: 1234, user_id: "1234") {
    id,
    likes
  }
}
```

We can do the same thing for unlikes.....

*Discuss:* What do we need to do in order to implement this?

*Exercise:* Implement the mutations so our like state is persisted


## Immutable.JS

We're going to need to implement Immutable JS in order to properly update our
state when we interact with the server.


