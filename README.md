# vuex-light

[![npm](https://img.shields.io/npm/v/vuex-light)](https://www.npmjs.com/package/vuex-light)
[![npm bundle size](https://img.shields.io/bundlephobia/min/vuex-light)](https://bundlephobia.com/result?p=vuex-light@latest)
[![GitHub Workflow Status (branch)](https://img.shields.io/github/workflow/status/js-cosmos/vuex-light/CI/main)](https://github.com/js-cosmos/vuex-light/actions?query=workflow%3ACI+branch%3Amain+)
![npm downloads](https://img.shields.io/npm/dm/vuex-light)
![last commit](https://img.shields.io/github/last-commit/js-cosmos/vuex-light/main)

# Features

- Light weight (10x smaller then [vuex](https://bundlephobia.com/result?p=vuex@next))
- Full typescript support
- Implement with vue 3 reactivity system only

# Installation

via npm

```
yarn add vuex-light
```

via cdn

```html
<script src="https://unpkg.com/vuex-light@latest"></script>
```

# Getting Started

```ts
import { createApp } from 'vue'
import { createStore, install } from 'vuex-light'

// Create a new store instance.
const store = createStore({
  state: {
    count: 0,
  },
  mutations: {
    increment({ state }) {
      state.count++
    },
  },
})

const app = createApp({})

// Install the store instance as a plugin
app.use(install, { store })
```

# Examples

- [Hello world](https://codesandbox.io/s/github/js-cosmos/vuex-light/tree/main/examples/hello-world)
- [Counter](https://codesandbox.io/s/github/js-cosmos/vuex-light/tree/main/examples/counter)
- [Todo MVC](https://codesandbox.io/s/github/js-cosmos/vuex-light/tree/main/examples/todomvc)

# Core API

```ts
const store = new Vuex.Store({
  state: {
    count: 0,
  },
  getters: {
    isOdd({ state, getters }) {
      // ...
    },
  },
  mutations: {
    increment({ state, getters }, ...payloads) {
      // ...
    },
  },
  actions: {
    incrementIfOdd({ state, getters, mutations }, ...payloads) {
      // ...
    },
  },
})

store.state.count
store.getters.isOdd
store.mutations.increment()
store.actions.incrementIfOdd()
```

# TypeScript Support

## Typing `useStore` Composition Function

Just create a function and return it!

```ts
import { useStore } from 'vuex-light'

const store = createStore({
  state: {
    count: 0,
  },
})

function useStore() {
  return store
}
```

```ts
import { defineComponent } from 'vue'
import { useStore } from './store'

defineComponent({
  setup() {
    const store = useStore()
    store.state.count // typed as number
    return {}
  },
})
```

## Typing `$store` Property in Vue Component

```ts
import { createApp } from 'vue'
import { useStore, install } from 'vuex-light'

const store = createStore({
  state: {
    count: 0,
  },
})

const app = createApp({})

app.use(install, { store })
```

```ts
import { defineComponent } from 'vue'

defineComponent({
  created() {
    this.$store.state.count // typed as number
  },
})
```

# Contributing

Please read [CONTRIBUTING.md](/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull
requests to us.

# Versioning

We use [SemVer](https://semver.org/) for versioning. For the versions available, see the tags on this repository.

# License

This project is licensed under the MIT License - see the [LICENSE](/LICENSE) file for details
