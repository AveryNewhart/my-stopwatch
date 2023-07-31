<script setup lang="ts">
import { ref } from 'vue';

// for the start
const timeElapsed = ref(0);

//for the pause
const interval = ref<number | undefined>(undefined);

function start() {
  interval.value = setInterval(() => {
    timeElapsed.value++;
  }, 1000);
}

function pause() {
  clearInterval(interval.value);
}

</script>

<template>
  <div>
    <div>{{ timeElapsed }}</div>
    <button @click="start">start</button>
    <button @click="pause">Pause</button>
    <button>Restart</button>
  </div>
</template>

<style scoped>
</style>
