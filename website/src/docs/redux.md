---
title: "Redux"
type: docs
permalink: docs/redux/
order: 9
category: 'React'
---

Uppy supports the popular [Redux](https://redux.js.org/) state management library in two ways:

## Redux Store

You can tell Uppy to use your app’s Redux store for its files and UI state. Please check out [Custom Stores](/docs/stores/) for more information on that. Here’s an example to give you a sense of how this works:

```js
const { createStore } = require('redux')
const ReduxStore = require('@uppy/store-redux')

const reducer = combineReducers({
  ...reducers,
  uppy: ReduxStore.reducer
})

const uppy = Uppy({
  store: ReduxStore({
    store: createStore(reducer) // That’s a lot of stores!
  })
})
```

## Redux Dev Tools

This is a `ReduxDevTools` plugin that simply syncs with the [redux-devtools](https://github.com/gaearon/redux-devtools) browser or JS extensions, and allows for basic time travel:

```js
const Uppy = require('@uppy/core')
const ReduxDevTools = require('@uppy/redux-dev-tools')

const uppy = Uppy({
  debug: true,
  meta: {
    username: 'John',
    license: 'Creative Commons'
  }
})
  .use(XHRUpload, { endpoint: 'https://example.com' })
  .use(ReduxDevTools)
```

After you `.use(ReduxDevTools)`, you should be able to see Uppy’s state in Redux Dev Tools.

You will likely not need this if you are actually using Redux yourself, as well as Redux Store in Uppy like in the example above, since it will just work automatically in that case.
