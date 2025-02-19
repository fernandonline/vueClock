<template>
  <div class="options-menu">
    <h3>Opções</h3>

    <ClockColorOption @update:clockCustomStyles="onClockUpdate" />

    <BackgroundColorOption @update:backgroundCustomStyles="onBackgroundUpdate" />

    <button @click="$emit('close')">Fechar</button>
  </div>
</template>

<script setup lang="ts">
import ClockColorOption from '@/components/Menu/ClockColorOption.vue';
import BackgroundColorOption from '@/components/Menu/BackgroundColorOption.vue';
import { defineEmits } from 'vue';

const emit = defineEmits<{
  (event: 'update:clockCustomStyles', value: Record<string, string>): void;
  (event: 'update:backgroundCustomStyles', value: Record<string, string>): void;
  (event: 'close'): void;
}>();

const onClockUpdate = (value: Record<string, string>) => {
  emit('update:clockCustomStyles', value);
};

const onBackgroundUpdate = (value: Record<string, string>) => {
  emit('update:backgroundCustomStyles', value);
};
</script>

<style scoped>
.options-menu {
  background: rgba(0, 0, 0, 0.8);
  padding: 1rem;
  border-radius: 8px;
  text-align: center;
  color: #fff;
  position: absolute;
  top: 100px;
  left: 50%;
  transform: translateX(-50%);
}

button {
  background: #fff;
  color: #000;
  border: none;
  padding: 0.5rem 1rem;
  cursor: pointer;
}
</style>
