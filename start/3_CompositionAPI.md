* Options API
    * data
    * method
    * computed
    * watch

* Composition API
    write code more like traditional JavaScript
    * `export default` wrapper
    * `setup()` 
    * `return` any value that want to be made available to use in template.
* `<script setup>`
    * make the `setup()` wrapper `export default` default.
* Reactivity(from regular js library)
    In `<script setup>` we do this to `state` in template follows `state` in `<script setup>`.
    ```js
    let state = reactive({  //one of the reactive wrappers(auto-imported in nuxt)
        user: null,
        darkMode: false,
    });
    <template>
        <p>{{ state.user }}</p>
    </template>
    ```
    * `isReactive`  property
        Check if an object is reactive.
        `const reactivitySet = isReactive(state)`