<template>
  <button @click="toggleNightMode" class="focus:outline-none">
    <img :src="isNightMode ? '/night.png' : '/day.png'" alt="Night Mode Toggle" class="w-15 h-10 rounded-full" />
  </button>
</template>

<script setup>
import { ref } from 'vue';

const isNightMode = ref(false);

function toggleNightMode() {
  isNightMode.value = !isNightMode.value;
}
</script>

<style scoped>

</style>
