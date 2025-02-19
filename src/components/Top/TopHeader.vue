<script setup lang="ts">
const props = defineProps<{
  toggleCustomization: () => void;
}>();

const { toggleCustomization } = props;
</script>

<template>
  <header class="header">
    <button @click="toggleCustomization" class="customize-btn">
      CLICK
    </button>
  </header>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: flex-end;
  height: 9.8vh;
}

.customize-btn {

  cursor: pointer;
  font-size: 1em;
}
</style>
