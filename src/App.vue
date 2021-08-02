<template>
  <div class="max-w-7xl mx-auto">
    <div
      class="
        w-full
        bg-blue-200
        md:flex
        justify-between
        items-center
        px-12
        pb-4
        md:py-1
        md:rounded-b-3xl
        shadow
        z-20
        sticky
      "
    >
      <img class="h-16 py-2 mx-auto" src="./assets/logo.png" />
      <p class="w-full text-center md:text-right text-2xl cursor-pointer border-t pt-1 mt-1 md:pt-0 md:mt-0 md:border-t-0">
        <a href="#" class="hover:underline pr-4">Login</a>
        <a href="#" class="hover:underline">Sign Up</a>
      </p>
    </div>

    <div class="-mt-1 pt-8 md:pt-2 md:mt-6 flex bg-gray-100 rounded-lg">
      <div class="w-1/3 md:w-1/4 md:mr-8 p-2 md:p-6 rounded-lg">
        <!-- Breed selector -->
        <div class="w-full mb-6">
          <p class="text-xl border-b border-gray-400 mb-1 pb-0.5">Breed</p>
          <select
            class="text-center mt-2 py-1 md:px-4 md:text-lg"
            v-model="breedFilter"
          >
            <option :value="null">All</option>
            <option value="retriever">Retrievers</option>
            <option value="terrier">Terriers</option>
          </select>
        </div>

        <!-- Gender selector -->
        <div class="w-full mb-6">
          <p class="text-xl border-b border-gray-400 mb-1 pb-0.5">Gender</p>
          <label class="block text-lg">
            <input type="radio" :value="null" v-model="genderFilter" /> Any
          </label>

          <label class="block text-lg">
            <input type="radio" value="male" v-model="genderFilter" /> Male
          </label>

          <label class="block text-lg">
            <input type="radio" value="female" v-model="genderFilter" /> Female
          </label>
        </div>
      </div>
      <div class="w-2/3 md:w-3/4 border-l px-1 md:px-4">
        <!-- Dog loop -->
        <div
          v-for="(dog, index) in dogs"
          :key="index"
          class="inline-block w-full md:w-1/2 lg:w-1/3 p-4 pb-6"
        >
          <div class="p-2 bg-white shadow-lg rounded-lg relative">
            <div
              class="w-full bg-gray-200 h-48 bg-top bg-cover bg-no-repeat"
              :style="`background-image: url('/src/assets/${dog.image}');`"
            />
            <div
              @click="favorite(dog)"
              class="
                absolute
                right-0
                top-0
                p-2
                m-4
                z-20
                bg-white
                rounded-full
                cursor-pointer
                hover:bg-gray-100
                hover:text-green-500
              "
            >
              <heart class="h-6 w-6" />
              <!-- <heart-filled class="h-6 w-6" /> -->
            </div>
            <p class="text-2xl text-center py-2">{{ dog.name }}</p>
            <p>{{ startCase(dog.gender) }} {{ dog.breed }}</p>
            <p>Available {{ dog.availability }}</p>
            <p>${{ dog.price }} donation fee</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import heart from "./components/svgs/heart.vue";
import heartFilled from "./components/svgs/heartFilled.vue";
import { startCase } from "lodash";

export default {
  components: { heart, heartFilled },

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

  methods: {
    startCase,

    favorite(dog) {
      console.log(dog);
    },
  },

  data() {
    return {
      /**
       * Available dogs
       *
       * @type {Array} (check /fixtures/dogs.json)
       *        .id: Integer
       *        .image: String
       *        .base_breed: String ['terrier', 'retriever', 'other']
       *        .breed: String -- ['Golden retriever', 'English bull terrier', ...]
       *        .name: String
       *        .gender: String -- ['male', 'female']
       *        .availability: DateString -- 'dd/mm/yyyy
       *        .price: Integer
       */
      dogs: [],

      /**
       * Gender to filter on
       *
       * @type {?String}
       */
      genderFilter: null,

      /**
       * Breed to filter on
       *
       * @type {?String}
       */
      breedFilter: null,
    };
  },
};
</script>
