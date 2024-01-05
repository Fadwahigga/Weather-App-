<template>
    <header class="bg-weather-primary shadow-lg sticky top-0">
        <nav class="container flex flex-col sm:flex-row items-center text-white py-6 gap-4">
            <RouterLink :to="{ name: 'home' }">
                <div class="flex items-center gap-3">
                    <i class="fa-solid fa-sun text-2xl"></i>
                    <p class="text-2xl">The Weather</p>
                </div>
            </RouterLink>
            <div class="flex gap-3 justify-end flex-1"><i
                    class="fa-solid fa-circle-info text-xl hover:text-weather-secondary duration-150 cursor-pointer"></i>
                <i class="fa-solid fa-plus text-xl hover:text-weather-secondary duration-150 cursor-pointer"></i>
            </div>
        </nav>
    </header>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router';
</script>

<style scoped></style>