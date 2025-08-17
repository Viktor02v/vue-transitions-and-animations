<script setup lang="ts">
import { ref } from 'vue'
const showMessage = ref(false)
</script>

<template>
  <button @click="showMessage = !showMessage">
    {{ showMessage ? 'Hide' : 'Show' }}
    Menu
  </button>

  <Transition>
    <ul v-if="showMessage">
      <li>Menu Item 1</li>
      <li>Menu Item 2</li>
      <li>Menu Item 3</li>
    </ul>
  </Transition>
</template>

<style scoped>
.v-enter-active, .v-leave-active {
  transition: opacity 0.5s;
}
.v-enter, .v-leave-to {
  opacity: 0;
}
</style>