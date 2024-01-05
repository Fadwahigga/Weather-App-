<template>
  <main class="container text-white">
    <div class="relative pt-4 mb-8">
      <input
        type="text"
        v-model="searchQuery"
        @input="getSearchResults"
        placeholder="Search for a city or state"
        class="py-2 px-1 border-b w-full bg-transparent focus:outline-none focus:border-weather-secondary"
      />
    </div>
    <ul
      class="bg-weather-secondary text-white w-full shadow-md py-1 px-1 top-0"
      v-if="mapboxSearchResults"
    >
      <p class="py-1" v-if="searchError">
        Sorry, something went wrong, please try again.
      </p>
      <p class="py-1" v-if="!searchError && mapboxSearchResults.length === 0">
        No results match your query, try a different term.
      </p>
      <template v-else>
        <li
          v-for="searchResult in mapboxSearchResults"
          :key="searchResult.id"
          class="py-1 cursor-pointer"
        >
          {{ searchResult.place_name }}
        </li>
      </template>
    </ul>
  </main>
</template>
<script setup lang="ts">
import { ref } from "vue";
import axios from "axios";
const mapboxAPIKey =
  "pk.eyJ1Ijoiam9obmtvbWFybmlja2kiLCJhIjoiY2t5NjFzODZvMHJkaDJ1bWx6OGVieGxreSJ9.IpojdT3U3NENknF6_WhR2Q";
const searchQuery = ref("");
const queryTimeout = ref();
const mapboxSearchResults = ref();
const searchError = ref();

const getSearchResults = () => {
  clearTimeout(queryTimeout.value);
  queryTimeout.value = setTimeout(async () => {
    if (searchQuery.value !== "") {
      try {
        const result = await axios.get(
          `https://api.mapbox.com/geocoding/v5/mapbox.places/${searchQuery.value}.json?access_token=${mapboxAPIKey}&types=place`
        );
        mapboxSearchResults.value = result.data.features;
        console.log(mapboxSearchResults.value);
      } catch {
        searchError.value = true;
      }

      return;
    }
    mapboxSearchResults.value = null;
  }, 300);
};
</script>
