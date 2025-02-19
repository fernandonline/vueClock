<script setup lang="ts">
import { ref, computed } from 'vue';

const clockColorChoice = ref<'white' | 'black' | 'red' | 'image'>('white');

const styles = computed(() => {

  switch (clockColorChoice.value) {
    default:
      return { color: '#FFFFFF'
    }

    case 'black':
    return { color: '#000000'
    }
    case 'red':
      return { color: '#FF0000'
    }

    //case 'image':
      //return ;
  }
});

defineExpose({
  clockColorChoice,
  styles
});
</script>

<template>
  <div class="customization-container">
    <select v-model="clockColorChoice">
      <option value="white">Branco</option>
      <option value="black">Preto</option>
      <option value="red">Vermelho</option>
      <!-- <option value="image">Imagem</option> -->
    </select>
  </div>
</template>

<style>
.image-bg {
  -webkit-background-clip: text;
  color: transparent;
  background-image: url('../../assets/hatsune-street-wallpapper.png');
  background-clip: text;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
