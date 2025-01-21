<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import ClockCustom from './ClockCustom.vue';
import type { iTimeTypes } from './TimeInterface.ts';

const customizationRef = ref();
const currentTime = ref<iTimeTypes>(getFormattedTime());

function getFormattedTime(): iTimeTypes {
  const now = new Date();
  return {
    hour: now.getHours().toString().padStart(2, '0'),
    minute: now.getMinutes().toString().padStart(2, '0')
  };
}

const updateTime = () => {
  currentTime.value = getFormattedTime();
}

let intervalId: number | undefined;

onMounted(() => {
  intervalId = setInterval(updateTime, 1000);
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId);
})
</script>

<template>
  <div class="clock-container">
    <ClockCustom ref="customizationRef" />
    <span
      class="clock-text"
      :class="{'image-bg': customizationRef?.backgroundChoice === 'image'}"
      :style="customizationRef?.styles"
    >
      {{ currentTime.hour }}:{{ currentTime.minute }}
    </span>
  </div>
</template>

<style scoped>
.clock-container {
  font-family: 'Arial', sans-serif;
}

.clock-text {
  font-size: 5em;
}
</style>
