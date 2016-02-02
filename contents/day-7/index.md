---
title: Geekwise Academy ReactJS
template: index.ejs
---

# Day 7: The User feed

## Setting up

Everyone will need to clone by Day 7 branch today.

```bash
$ git clone git@github.com:dphaener/geekbook.git
$ cd geekbook
$ git checkout day-7
```

## Reviewing the changes

I made a bunch of changes to the code base over the weekend so that we can
continue on and start creating the user feed. Let's review those right now.

### Multiple reducers

If you look at the reducers directory, you will see that I separated the reducers out into two
files, and then combined them into one object that I exported.

```js
import registration from './registration'
import login from './login'

export default {
  registration,
  login
}
```

I then had to update the way we were combining reducers in `app.jsx`:

```js
const reducer = combineReducers(
  Object.assign({}, reducers, { routing: routeReducer})
)
```

### Protecting the user feed page

Up until now, if you knew a user's id, you could just put that in the URL,
and the app would work. I added a simple authentication function to help us
protect this page:

```js
function authenticate(nextState, replace) {
  if (!localStorage.getItem('geekbook_user')) {
    replace({ pathname: '/' })
  }
}
```

This function simply checks for the presence of our `geekbook_user` key and
if it cannot be found it redirects to the home page. Admittidely, this could
be more secure (like checking the URL token against the token in the `geekbook_user`
key), but for the purposes of moving forward, we'll go with this.

This function is invoked on the `onEnter` callback in the React Router route:

```js
<Route path="/:token" component={Feed} onEnter={authenticate} />
```

### First API data call

I also added a simple API call to load the users first ten posts. This isn't
how we want to implement this in the end, we ultimately want to move this
into an action creator. Here's the query:

```js
query {
  user(token: "${this.state.userId}") {
    posts(first: 10) {
      content
    }
  }
}
```

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
