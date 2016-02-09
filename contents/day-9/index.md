---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 9: Persisting Unlikes

## Setting up

We'll begin developing on the Day 9 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-9
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-9
```

## Server fix

Last week we had an issue with the server not responding properly when we
clicked the like button. It was a data type issue, and has since been resolved,
and now the app works perfectly. Yai!


## Persisting the unlikes

After going through last week and implementing likes, we now need to be able
to persist unlikes. This should be a very similar process as last week.

*Discuss:* What do we need to do to make this happen?

*Exercise:* Implement the unlike action


## Optimistic Updates

Let's discuss optimistic updating, and how to implement it in our app.

*Discuss:* What is optimistic updating?

*Exercise:* Implement an optimistic update for our mutations

## Begin work on the friending user functionality

*Discuss:* What should this look like?

*Exercise:* Begin implementing this

