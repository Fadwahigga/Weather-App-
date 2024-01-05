<template>
  <div
    class="absolute w-full bg-black bg-opacity-30 h-screen top-0 left-0 flex justify-center px-8" v-if="isOpen"
  >
    <div class="p-4 bg-white self-start mt-32 max-w-screen-md rounded-lg">
      <slot />
      <button class="text-white bg-weather-primary py-2 px-6 rounded-md mt-4" @click="closeHandler">
        Close
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Props {
  closeHandler: any;
  isOpen: boolean;
}

const props = defineProps<Props>();
</script>

<style scoped></style>
