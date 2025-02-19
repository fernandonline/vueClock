<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';

const {customStyles} = defineProps<{
  customStyles: Record<string, string>;
}>();

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
};

let intervalId: number | undefined;
onMounted(() => {
  intervalId = setInterval(updateTime, 1000);
});
onUnmounted(() => {
  if (intervalId) clearInterval(intervalId);
});
</script>

<template>
  <div class="clock-container">
    <span
      class="clock-text"
      :style="customStyles"
    >

      {{ currentTime.hour }}

      <span class="time-space"> : </span>

      {{ currentTime.minute }}

    </span>
  </div>
</template>

<style scoped>
.clock-container {
  border: 1px solid yellowgreen;
  font-family: 'Arial', sans-serif;
  height: 90vh;
  display: flex;
  place-content: center;
  align-items: center;
}

.time-space {
  margin-left: var(--margin-space);
  margin-right: var(--margin-space);
}

.clock-text {
  margin-top: -10svh;
  font-size: 10rem;
}
</style>
