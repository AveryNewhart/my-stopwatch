<script setup lang="ts">
import { ref } from 'vue';

// setting the state of which the time is
const state = ref<"stopped" | "running" | "paused">("stopped");

// for the start
const timeElapsed = ref(0);

//for the pause
const interval = ref<number | undefined>(undefined);

function start() {
  state.value = "running";
  interval.value = setInterval(() => {
    timeElapsed.value++;
  }, 1000);
}

function pause() {
  state.value = "paused";
  clearInterval(interval.value);
  interval.value = undefined;
}

function restart () {
  timeElapsed.value = 0;
  if (interval.value !== undefined) {
  clearInterval(interval.value);
  interval.value = undefined;
  }
  start();
}

function formatTime(elaspedTime: number) {
  const minutes = `0${Math.floor(elaspedTime / 60)}`.slice(-2);
  const seconds = `0${elaspedTime % 60}`.slice(-2);
  return `${minutes}:${seconds}`;
}
</script>

<template>
  <div>
    <div>{{ formatTime(timeElapsed) }}</div>
    <button v-if="state === 'stopped'" @click="start">start</button>
    <button v-if="state === 'running'" @click="pause">Pause</button>
    <button v-if="state === 'paused'" @click="start">resume</button>
    <button v-if="state === 'running' || state === 'paused'" @click="restart">restart</button>
  </div>
</template>

<style scoped>
</style>
