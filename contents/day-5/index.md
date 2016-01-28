---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 5: Creating a user and authentication

## Setting up

We'll begin developing on the Day 5 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-5
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-5
```

## Finishing form validation

Our form has most of the validation logic in place, and the next thing we
need to do is display an error message if the emails don't match, and then
wire up the form submission logic.

*Exercise:* Add logic to display an error message below the input when the emails don't match.

*Discuss:*
  * What do we need to do in order to submit our form
  * What do we need to do after the form has submitted?
  * What do we do on success? On failure?

*Exercise:* Wire up the form submission (pair coding)



