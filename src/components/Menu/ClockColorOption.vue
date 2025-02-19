<template>
  <div class="option-section">
    <h4>Cor do Relógio</h4>
    <select v-model="clockColorChoice">
      <option value="white">Branco</option>
      <option value="black">Preto</option>
      <option value="red">Vermelho</option>
    </select>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue';

const emit = defineEmits<{
  (e: 'update:clockCustomStyles', value: Record<string, string>): void;
}>();

const clockColorChoice = ref<'white' | 'black' | 'red'>('white');

function getClockStyles(choice: string) {
  switch (choice) {
    case 'black':
      return { color: '#000000' };
    case 'red':
      return { color: '#FF0000' };
    default:
      return { color: '#FFFFFF' };
  }
}

const computedClockStyles = computed(() => getClockStyles(clockColorChoice.value));

watch(clockColorChoice, () => {
  emit('update:clockCustomStyles', computedClockStyles.value);
});
</script>

<style scoped>
.option-section {
  margin-bottom: 1rem;
}

select {
  padding: 0.5rem;
  font-size: 1rem;
}
</style>
