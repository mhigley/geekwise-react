---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 3: User registration and authentication

## Setting up

We'll begin developing on the Day 3 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-3
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-3
```

## Creating the home page

Last week we created a `login` and `index` page just as exercises. But we are
making a Facebook clone, and these pages are one and the same on Facebook, so
let's go ahead and remove the `login` route and component.

*Discuss:*
  * What elements do we need on this page?
  * What components do we need to create?
  * Will these components be reusable in any way?

*Exercise:* Create the components needed for the home page.

## Unit testing your components

Last week we discussed unit testing briefly, and now we're going to actually
start writing some tests!

We've already got `legit-tests` installed, so we're good to go there. The next
thing we'll need to do is create a `test` directory in the root of our app.

*Discuss:* What should a unit test for a component look like?

*Exercise:* Pair code the unit tests for the components we just created

