## Setup

```
nvm use 15.8.0
npm install
npm run dev
```

## Interview questions

The app gets a list of dogs from the passed in URL when it is first mounted.

### AppRework.vue

This app has two working filters (breed and gender). How would you improve this code?

We're looking for
* Remove the watch
* Use a v-model on the inputs instead
* Set the value of the "don't filter this" inputs to something falsy instead of the strings "any" or "all"
* Use the v-model to return a computed array of dogs based on what filters are enabled

### AppFavorite.vue
```
 -- Make the following change in Wrapper.vue -- 

<script>
import App from "./AppRework.vue"
// import App from "./AppFavorite.vue"
...
```

A new feature request! When you click the "favorite" icon, it 

1. Changes to a filled in versions.
2. The favorite dogs will NEVER be filtered out based on breed or gender.
3. (New feature request) We ALSO want your favorite dogs to be at the TOP of the list.
