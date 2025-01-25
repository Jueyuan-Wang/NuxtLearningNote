# Get Started

## Pages and Components

* pages/
    all files in `pages` folder will be routed automatically
* components/
    shares the same structure with pages
* `v-for`
    be used for iterating collections
    ```html
    <Post v-for="post in posts" :key="post.id"/>
    ```
## Props & Emitting Events

> Question: How to share datas between pgaes/components

### Props
* static: `<Post title="post 1" />`
* dynamic: `<Post :title="post.title" />`
* props are only ever passed down to child components 
    Parent:
    ```vue
    <Section :message="message" />
    ```
    Child:
    ```vue
    {{message}}
    ```
* when the props data changes in the parent, the child components are updated too.
* Prop validation layer
    ```vue
    defineProps({
        message: String, 
    });
    ```
    P.S. `setup` combines the logic of the setup() function directly into the `<script>` block

### Emitting events

* basic (all of belows are wrapped in `<script>`)

    1. Listen in child
        ```js
        <button @click="$emit('increaseScore', 10)">&hearts;</button>
        ```
    2. Define in child
        ```js
        // takes in an array of one or more event names
        defineEmits(['increaseScore'])
        ```
    3. Handle in parent
        ```js
        <Child @increase-score="value => score += value" />
        function handleIncreaseScore(value) {...}
        ```
## Layouts

Defines structure of pages.
Nuxt.js can recognize `layouts` directory automatically by default.

* `<slot/>` is used for specifying the part that be displayed inside the layout.

* `<NuxtPage/ >` :the placeholder where page components (e.g. pages/login.vue) will be injected.

* `definePageMeta`can  be used for specifying layout for a page.

* Code should be added to the app.vue if we only need one layout.

## Auto import & Modules

* Default exports
    ***a file/module can only have one default export.***
    export:
    ```js
    export default {
    name: "HelloWorld",
    props: {
        msg: String
    }
    };
    ```
    import:
    ```js
    import HelloWorld from "./components/HelloWorld.vue";
    ```
* Named exports
    import as many or as few values as we need
    ```js
    import { ref, computed } from "vue";
    ```
* Nuxt auto-import
    Nuxt auto-imports components, helper functions, composable files, and Vue.js APIs. 
    * disable:set `autoImport: false` in `nuxt.config.ts`

