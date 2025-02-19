<template>
  <div class="option-section">
    <h4>Cor do Fundo</h4>
    <select v-model="backgroundColorChoice">
      <option value="white">Branco</option>
      <option value="black">Preto</option>
      <option value="red">Vermelho</option>
    </select>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue';

const emit = defineEmits<{
  (event: 'update:backgroundCustomStyles', value: Record<string, string>): void;
}>();

const backgroundColorChoice = ref<'white' | 'black' | 'red'>('black');

function getBackgroundStyles(choice: string) {
  switch (choice) {
    case 'white':
      return { backgroundColor: '#FFFFFF' };
    case 'black':
      return { backgroundColor: '#000000' };
    case 'red':
      return { backgroundColor: '#FF0000' };
    default:
      return { backgroundColor: '#000000' };
  }
}

const computedBackgroundStyles = computed(() => getBackgroundStyles(backgroundColorChoice.value));

watch(backgroundColorChoice, () => {
  emit('update:backgroundCustomStyles', computedBackgroundStyles.value);
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
