<template>
  <div class="flex flex-col min-h-screen font-Roboto bg-weather-primary">
    <NavBar />
    <RouterView />
  </div>
</template>

<script setup lang="ts">
import { RouterView } from "vue-router";
import NavBar from "./components/NavBar.vue";
</script>

<style scoped></style>
