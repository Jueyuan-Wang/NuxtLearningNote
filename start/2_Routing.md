# Routing

## File-Based Navigation & Dynamic Routers

* Vue automatically creates routes for pages under `pages/`

* Manual configuration in Vue.js

* Dynamic routes
    `path: "/account/:id"`
    * combine with file system
    ```
    pages/index.vue => /
    something/index.vue => pages/something/index.vue
    [para].vue => pages/something/[para].vue
    ```
    * use in file
    ```js
    <script setup>
    const route = useRoute(); //get current route
    const userId = route.params.id; // the id is matching `[id]` in file name.
    </script>
    <template>
        <p>{{ userId }}</p>
        <a href="/">home</a>
    </template>
    ```
## NuxtLink & prefecthing

* traditional way: use `<a>` tag

* `NuxtLink` component
    ```js
    <li><NuxtLink to="/account/245662">account page with params</NuxtLink></li>
    ```
* prefecthing (powered by `NuxtLink`)
    * The problem: Traditional `SPA` bundles every single page into one large file.
    * Solution : `NuxtLink` enables code splitting and prefetching.
      * Code splitting: Only the JavaScript for the current page is downloaded initially.
      * Prefetching : Prefetching the JavaScript code for pages linked to the current page. 

* custom links
    * custom link is created as a component in the components directory
    * formart:
    `./components/CustomLink.ts`
    ```js
    export default defineNuxtLink({
        componentName: 'CustomLink',
        externalRelAttribute: '',
        activeClass: 'custom-active',
        exactActiveClass: 'custom-exact-active',
        prefetchedClass: 'prefetch-class'
    })
    ```
* 