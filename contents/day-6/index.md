---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 6: Authentication, protecting routes, and the user feed

## Setting up

We'll begin developing on the Day 6 branch of the geekbook repository. If
you were able to follow along through the last class, you can continue along
with your own repo.

Or, you can clone my repo and checkout the branch:

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-6
```

If you have already cloned my repo, just fetch all the changes and then
checkout the branch:

```bash
$ cd geekbook
$ git fetch origin
$ git checkout -t origin/day-6
```

## Refactoring the user creation

Last time, we just hastily threw together the user creation in an attempt to
get it done. But now we're going to refactor it, clean it up, and do
everything the right way. The first thing we'll do is create some middleware
for Redux to handle API calls. And for this, we'll use some code from Jason.

```js
export default function promiseMiddleware() {
  return (next) => (action) => {
    const { promise, type, ...rest } = action;
    if (!promise) {
      return next(action);
    }

    next({ ...rest, type: type+'_REQUEST' });
    return promise.then(
      (result) => next({ ...rest, result, type: type }),
      (error) => {
        next({ ...rest, error, type: type+'_FAILURE' })
        return Promise.reject(error);
      }
    );
  };
}
```

Let's add this to a file called `promise_middleware.js` in a new folder called
`app/flux`. Next we need to apply this middleware, so let's do that.

```js
import { applyMiddleware, createStore } from 'redux'
import promiseMiddleware from '~/app/flux/promise_middleware'

const createStoreWithMiddleware = applyMiddleware(promiseMiddleware)(createStore)
const store = createStoreWithMiddleware(reducer)
```

## Action Creators

Up until now we've been calling our actions by just passing in a JavaScript,
but we should be using action creators. Let's create our action creator
for our current action, and move the user creation API call into that action.

*Exercise:* Add action creator and refactor registration component

## React Router Redux

Now that we've moved our API call into the actions, we need to be able to
change our page location on a successfull registration. We'll do this by
using React Router Redux to keep our router and redux state in sync, which
will give us access to all of the `React Router` objects that we need.

*Exercise:* Add React Router Redux and move logic into reducer from `Registration` component

## Finishing user login

We left user login in a state where we were ready to handle a form submission.
Let's go ahead and handle that now.

*Discuss:* What do we need to do in order to login?

*Exercise:* Wire up the login logic.

## Creating the user feed

Next we'll be starting on the creation of the user's feed.

*Discuss:*
  * How do we protect this route and make sure the user is logged in?

*Exercise:* Protect the feed route

*Discuss:*
  * What models do we need?
  * What fields should be on those models?
  * What relationships should there be?
  * What should the 'Post' component look like?

*Exercise:* Begin creating the Post component
