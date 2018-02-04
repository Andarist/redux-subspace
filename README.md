# redux-subspace

[![npm version](https://img.shields.io/npm/v/redux-subspace.svg?style=flat-square)](https://www.npmjs.com/package/redux-subspace)
[![npm downloads](https://img.shields.io/npm/dm/redux-subspace.svg?style=flat-square)](https://www.npmjs.com/package/redux-subspace)
[![License: MIT](https://img.shields.io/npm/l/redux-subspace.svg?style=flat-square)](/LICENSE.md)

This is a library to help build decoupled, componentized [Redux](http://redux.js.org/) apps that share a single global store.

## Installation

```sh
npm install --save redux-subspace react-redux-subspace
```

## Quick Start

```javascript
import React from 'react'
import { createStore, combineReducers } from 'redux'
import { Provider } from 'react-redux'
import { namespaced } from 'redux-subspace'
import { SubspaceProvider } from 'react-redux-subspace'
import { TodoApp, todoReducer } from './todoApp'
import { CounterApp, counterReducer } from './counterApp'

const rootReducer = combineReducers({
  todo: todoReducer
  counter1: namespaced('counter1')(counterReducer),
  counter2: namespaced('counter2')(counterReducer)
})

const store = createStore(rootReducer)

const App = () => (
  <Provider store={store}>
    <SubspaceProvider mapState={(state) => state.todo}>
      <TodoApp />
    </SubspaceProvider>
    <SubspaceProvider mapState={(state) => state.counter1} namespace="counter1">
      <CounterApp />
    </SubspaceProvider>
    <SubspaceProvider mapState={(state) => state.counter2} namespace="counter2">
      <CounterApp />
    </SubspaceProvider>
  </Provider>
)
```

## [Documentation](https://ioof-holdings.github.io/redux-subspace/)

* [Introduction](https://ioof-holdings.github.io/redux-subspace/docs/Introduction.html)
* [Basics](https://ioof-holdings.github.io/redux-subspace/docs/basics/)
* [Advanced](https://ioof-holdings.github.io/redux-subspace/docs/advanced/)
* [Examples](https://ioof-holdings.github.io/redux-subspace/docs/Examples.html)

## Packages

* [`redux-subspace`](https://github.com/ioof-holdings/redux-subspace/tree/master/packages/redux-subspace): The core package for Redux Subspace
* [`react-redux-subspace`](https://github.com/ioof-holdings/redux-subspace/tree/master/packages/react-redux-subspace): React bindings compatible with `react-redux`
* [`redux-subspace-loop`](https://github.com/ioof-holdings/redux-subspace/tree/master/packages/redux-subspace-loop): Utilities for integrating with `redux-loop`
* [`redux-subspace-observable`](https://github.com/ioof-holdings/redux-subspace/tree/master/packages/redux-subspace-observable): Utilities for integrating with `redux-observable`
* [`redux-subspace-saga`](https://github.com/ioof-holdings/redux-subspace/tree/master/packages/redux-subspace-saga): Utilities for integrating with `redux-saga`
* [`redux-subspace-wormhole`](https://github.com/ioof-holdings/redux-subspace/tree/master/packages/redux-subspace-wormhole): Middleware for exposing additional state to subspaces

## Upgrading From Version 1 to Version 2

When upgrading to version 2 of Redux Subspace, refer to the [migration guide](/docs/Migrating.md) to work through all the breaking changes.

## Media

[MelbJS](http://melbjs.com/) presentation that launched this library - [Scaling React and Redux at IOOF](http://www.slideshare.net/VivianFarrell/scaling-react-and-redux-at-ioof).
[Web Developer 42˚](http://web.dev42.co/) presentation about Micro-Frontends - [From Monolith to Micro-Frontends](https://mpeyper.github.io/from-monolith-to-micro-frontends-wd42/)
