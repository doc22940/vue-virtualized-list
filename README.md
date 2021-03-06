# vue-virtualized-list

A virtual list. Useful when you need to show lange amount of data.
It only render the DOM elements it needs.
It has less functionality compared to other virtual list libraries but it's **under 5kb** before gzip

[![Netlify Status](https://api.netlify.com/api/v1/badges/2e0807f3-0bda-4804-94ec-b63aef0e4834/deploy-status)](https://app.netlify.com/sites/vue-virtualized-list/deploys)

[Demo and Documetantion](https://vue-virtualized-list.netlify.com)


## Getting started

To install the package in your application just type
```
npm install vue-virtualized-list
```

Then, to install as a global component
``` javascript
import Vue from "vue";
import VirtualizedList from "vue-virtualized-list";

Vue.component("virtualized-list", VirtualizedList)
```

Or you can register locally in one of your components as follows
``` javascript
import VirtualizedList from "vue-virtualized-list";

export default {
    name: "AmazingComponent",
    props: [myprop],
    components: {
        "virtualized-list": VirtualizedList
    }
}
```

Using it
``` html
<virtualized-list :items="list" :item-height="itemH">
    <template v-slot="provided">
        <div class="my-item-class">
            {{provided.id}}: {{ provided.content }}
        </div>
    </template>
</virtualized-list>
```
``` javascript
export default {
  data() {
    // create an long array
    const fillArrayWithNumbers = n => Array.apply(null, Array(n)).map((x, i) => i);

    return {
      list: fillArrayWithNumbers(15000).map(i => ({id: i, content: "content-" + i})),
      itemH: 25
    }
  }
}
```


## Parameters and events

#### Props

| Name                | Type   | Mandatory | Example           | Default value                  | Description                     |
|---------------------|--------|-----------|-------------------|--------------------------------|--------------------------------|
| items               | Array  | true      |    -              |       -                        | The list of items               |
| itemHeight          | Number | true      | 100               |       -                        | The height of each item (in px) |
| outerContainerEl    | String | false     | "div"             |     "div"                      | The type of the outer element (no matter the element, some css properties are necessary, e.g. `display: block`)  |
| outerContainerClass | String | false     | "my-class"        | "vue-virtualized-list"         | Class of the outer element      |
| innerContainerEl    | String | false     | "div"             |     "div"                      | The type of the inner element, the scrollable one (no matter the element, some css properties are necessary, e.g. `display: block` and `position: relative`) |
| innerContainerClass | String | false     | "my-class__inner" | "vue-virtualized-list__scroll" | Class of the inner element      |
|                     |        |           |                   |                                |                                 |

#### Events

It does not emit any event


## Contributing

##### Project setup
```bash
npm install
```
##### Compiles and hot-reloads for development
```bash
npm run dev
```
##### Compiles and minifies for production
```bash
npm run build
```
Documentation is done using vuepress.
##### Compiles and watch docs
```bash
npm run docs:dev
```
##### Compiles and bundle documentation
```bash
npm run docs:build
```
##### Run all the tests
```bash
npm run test
```
###### Run unit tests
```bash
npm run test:unit
```
Or you can run them in watch mode
```bash
npm run test:unit:w
```
###### Run end-to-end tests
```bash
npm run test:e2e
```
Or you can run them in watch mode with amazing cypress experience
```bash
npm run test:e2e:w
```
##### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

## Author and License

[Alberto De Agostini](https://twitter.com/albertodeago88)

Licensed under MIT 
