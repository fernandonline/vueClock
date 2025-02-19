<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import CustomClock from './CustomClock.vue';

const customizationRef = ref();
const currentTime = ref(getFormattedTime());

function getFormattedTime() {
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
    <CustomClock ref="customizationRef"/>
    <span
      class="clock-text"
      :style="customizationRef?.styles"
    >

      {{ currentTime.hour }}

      <span class="time-space"> : </span>

      {{ currentTime.minute }}

    </span>
  </div>
</template>

<style scoped>
.clock-container {
  font-family: 'Arial', sans-serif;
}

.time-space {
  margin-left: var(--margin-space);
  margin-right: var(--margin-space);
}

.clock-text {
  font-size: 10rem;
}
</style>
