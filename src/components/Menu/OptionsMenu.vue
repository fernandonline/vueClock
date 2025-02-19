<script setup lang="ts">
import { ref } from 'vue';
import CustomClock from '../Clock/CustomClock.vue';

const isMenuOpen = ref(false);
const customizationRef = ref();

const onClick = () => {
  isMenuOpen.value = !isMenuOpen.value
}
</script>

<template>
  <div @click="onClick">
    CLICK
  </div>

  <div v-if="isMenuOpen">
    <CustomClock ref="customizationRef" />
  </div>
</template>
