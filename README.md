# vue-starter

> A Vue.js project

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
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

``` Avoid minified version of vue in development mode in order to include all warnings

v-if vs v-show : a v-show el will remain in the DOM and just toggles the display property of an element, v-if removes it from the dom. 

The v-show directive does not support the <template> tag. v-show does not work with with v-else in vue 2.0

v-else must inmeediately follow v-if to be recognized

when using the 'el' property to target the element with vue, if targeting a class, vue will only target the first class.

when iterating an object, index is in range of 0...n - 1 where n is the number of object properties

the @ symbol replaces the v-on allowing for cleaner code in HTML

VueJS provides four envet modifiers for v-on to prevent the event default behavior:
    1 .prevent
    2 .stop
    3 .capture
    4 .self

Vue Provides aliases for the keys: enter, esc, tab, delete, space, up, down, left, right. So we could use <input @keyup.enter="calculate();"> 

Computed properties work life functions that you can use as properties.

As of Vue 2.0, Vue filters cannot be used within v-for. Filters can now inly be used inside text 
interpolation ({{ }}). Vue's team suggests to move filters' logic into Javascript, so that it can be reused throughout your component

A computed property can also be used to filter an array. Using a computed property to perform array filtering gives you in-depth control and more flexibility, since it's full Javascript, and allows you to access the filtered result elsewhere. 

When we need to sort/filter/index data in more advanced ways, consider JavaScript utility library. Great utility Libraries: Lodash, Underscore, Sugar

Warning: HTML attributes are case-insensitive. When using camelCased prop names as attributes, use kebab-case.

//FOR BOOTSTRAP NPM : 
npm install bootstrap -> in main.js : import 'bootstrap/dist/css/bootstrap.css'

//FOR LODASH NPM
npm i --save lodash -> in main.js  : import * as _ from 'lodash'

The shorthand for v-bind is :, used to passed a js object a component or prop to an epression

Tip: Whenever you find yourself repeating a piece of functionality, the most efficient way to deal with it is to create a dedicated Component.

Global Event Bus
great way of getting unrelated sectins of the app to communicate.
Ex: import Vue form 'vue';
    export const bus = new Vue();

Then import bus in other components: bus.emit(channel:'string', payload1:any,...);
Note: The second argument is the item to be passed.

bus.$on(channelToListenTo, clickHandler);
bus.$off.(channelToListenTo, clickHandler)

Note: by using bus.$off.() I remove tevery single listener of bus, regardless of channel

```
