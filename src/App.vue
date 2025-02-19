<script setup lang="ts">
import {ref, watch} from 'vue';
import TopHeader from '@/components/Top/TopHeader.vue';
import DisplayClock from '@/components/Clock/DisplayClock.vue';
import OptionsMenu from '@/components/Menu/OptionsMenu.vue';

const isMenuOpen = ref(false)
const clockCustomStyles = ref({color: '#FFFFFF'})
const bgCustomStyles = ref({backgroundColor: '#000000'})
const toggleCustomization = () => {
  isMenuOpen.value = !isMenuOpen.value
}

watch(bgCustomStyles, (newStyles) => {
  if (newStyles.backgroundColor) {
    document.body.style.backgroundColor = newStyles.backgroundColor;
  }
});
</script>

<template>
  <TopHeader :toggleCustomization="toggleCustomization"/>
  <DisplayClock :customStyles="clockCustomStyles"/>
  <OptionsMenu
    v-if="isMenuOpen"
    v-model:clockCustomStyles="clockCustomStyles"
    v-model:backgroundCustomStyles="bgCustomStyles"
    @close="toggleCustomization"
  />
</template>

<style scoped>


</style>
