<template>
  <div class="max-w-7xl mx-auto">
    <div
      class="
        w-full
        bg-blue-400
        border-b border-blue-600
        flex
        justify-between
        items-center
        px-12
      "
    >
      <img class="h-16 py-2" src="./assets/logo.png" />
      <p class="text-2xl cursor-pointer">
        <a href="#" class="hover:underline pr-4">Login</a>
        <a href="#" class="hover:underline">Sign Up</a>
      </p>
    </div>

    <div
      v-for="(dog, index) in dogs"
      :key="index"
      class="inline-block w-1/3 p-2 pb-4"
    >
      <div class="p-3 bg-gray-200 shadow-lg rounded-lg">
        <!-- Feature 1: Add a "favorite this dog" button -->
        <img class="mx-auto" :src="`/src/assets/${dog.image}`" />
        <p class="text-2xl text-center py-2">{{ dog.name }}</p>
        <p>Golden Retriever</p>
        <p>Available {{ dog.availability }}</p>
        <p>${{ dog.price }} donation fee</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  props: {
    /**
     * Callable URL to return all available dogs
     */
    url: {
      type: String,
      required: true,
    },
  },

  async mounted() {
    const response = await axios.get(this.url);
    this.dogs = response.data.dogs;
  },

  data() {
    return {
      dogs: [],
    };
  },
};
</script>
