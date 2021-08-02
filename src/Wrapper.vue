<template>
  <div>
    <app :url="fakeUrl" />
  </div>
</template>

<script>
// import App from "./AppRework.vue"
import App from "./AppFavorite.vue"
export default {
  components: {
    App
  },

  data() {
    return {
      fakeUrl: `https://l3pbkqtm4f.api.quickmocker.com/animals`
    }
  }
}
</script>