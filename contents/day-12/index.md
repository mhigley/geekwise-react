---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 12: Finishing up with Relay

## Setting up

We'll begin developing on the Day 12 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-12
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-12
```

## Add the like and unlike mutations

Similar to how we created the mutation to add a post, we will now need to
create mutations to like and unlike posts.

*Discuss:* What will these mutations look like

*Exercise:* Create the mutations!

## Update the user list to use Relay

We will have to now add back our user list to use Relay in the same fashion
that we did for the `Feed` `FeedPost` components.

*Discuss:* What do we need to do to get started with this?

*Exercise:* Implement the user list

