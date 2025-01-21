// ClockCustomization.vue
<script setup lang="ts">
import { ref, computed } from 'vue';

const backgroundChoice = ref<'white' | 'black' | 'red' | 'image'>('white');

const styles = computed(() => {
  const baseStyle = { backgroundImage: 'none' };

  switch (backgroundChoice.value) {
    case 'black':
      return { ...baseStyle, color: '#000' };
    case 'red':
      return { ...baseStyle, color: '#FF0000' };
    case 'image':
      return baseStyle;
    default:
      return { ...baseStyle, color: '#FFF' };
  }
});

defineExpose({
  backgroundChoice,
  styles
});
</script>

<template>
  <div class="customization-container">
    <select v-model="backgroundChoice">
  <option value="white">Branco</option>
  <option value="black">Preto</option>
  <option value="red">Vermelho</option>
  <option value="image">Imagem</option>
</select>
  </div>
</template>

<style>
.image-bg {
  -webkit-background-clip: text;
  color: transparent !important;
  background-image: url('../../assets/black_bullet_img.jpg') !important;
  background-clip: text;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
