<script setup lang="ts">
import { ref } from 'vue';

const timeElapsed = ref(0);

function start() {
  const interval = setInterval(() => {
    timeElapsed.value++;
  }, 1000);
}

</script>

<template>
  <div>
    <div>{{ timeElapsed }}</div>
    <button @click="start">start</button>
    <button>Pause</button>
    <button>Restart</button>
  </div>
</template>

<style scoped>
</style>
