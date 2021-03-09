# Vuex Contributing Guide

> When there’s a clear benefit to separating state management from components (for example, due to state complexity) we recommend using Vuex over any other Flux pattern. Otherwise, feel free to manage state in the components.

## Separation of concern

Vuex is composed of State, Getters, Mutations, Actions, and Modules.

When a user clicks on an action, we need to dispatch it. This action commits a mutation that changes the state. The action itself does not update the state; only a mutation should update the state.


## FIle Structure

When using Vuex at Primedevs, separate these concerns into different files to improve readability:

```
└── store
  ├── index.js          # where we assemble modules and export the store
  ├── actions.js        # actions
  ├── mutations.js      # mutations
  ├── getters.js        # getters
  ├── state.js          # state
  └── modules
    ├── module_one.js   # modules
```

## <mark>index.js</mark>

This is the entry point for our store. You can use the following as a guide:

```js
import Vuex from 'vuex';
import * as actions from './actions';
import * as getters from './getters';
import mutations from './mutations';
import state from './state';
import module_one from './modules';

export const createStore = () =>
  new Vuex.Store({
    actions,
    getters,
    mutations,
    state,
    modules: {
      module_one
    },
  });
```
