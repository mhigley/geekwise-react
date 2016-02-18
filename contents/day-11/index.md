---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 11: Getting Started With Relay

## Setting up

We'll begin developing on the Day 11 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-11
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-11
```

## Relay

Relay is a javascript framework for building data-driven React applications.
It aims to replace solutions like Alt and Redux for maintaining application
state. Relay emphasizes colocation of data requirements and components. That is
to say that our components define the data they need via a GraphQL fragment,
and Relay intelligently combines all of your data requirements into one query
that is sent to your GraphQL server.

This reduces server round trips, makes payloads smaller because you are only
fetching the data you need, and ultimately makes your application run faster
and smoother.

Relay also intelligently handles caching your data and updating the application
store when data is fetched or mutated, making it much easier to create snappy
applications.

## Update the feed and feed post components

This first thing we'll need to do is update the `Feed` and `FeedPost` components
to use Relay.

*Exercise:* Pair code to update these components to use Relay.

