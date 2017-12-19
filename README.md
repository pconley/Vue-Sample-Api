# vue-sample-api

> a simple vue application based on my Vue-Sample-App 
> but extended to make use of Axios to get to an API using a second tutorial at
> https://alligator.io/vuejs/rest-api-axios/

# Notes

> there was an initial issue where the add function was not adding the todo to the 
> same list that was used by the list.  to overcome this i changed the "data" to not
> include a "todos" so that only the prop was used

> there are two components that both use the todos that are defined in the App.vue
> but the functions that act on the todos are implemented two ways... the list acts
> directly on the list because it bound as a property; but the create does not.
> the create emits an event that bubles up to the App so it can acct on the todo.
> Either way works and the differnce is retained to show the techniques.

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
