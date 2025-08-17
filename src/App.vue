<script setup lang="ts">
import { ref } from 'vue'
import FadeTransition from './components/FadeTransition.vue'
const show = ref(true)
const showMessage = ref(false)
</script>

<template>
  <!-- Named Transition -->
  <Transition name="appear" :duration="1500" appear>
    <div v-if="show">Hello there!!</div>
  </Transition>
  <button @click="showMessage = !showMessage">
    {{ showMessage ? 'Hide' : 'Show' }}
    Menu
  </button>

  <!-- Available props:
        mode: 'out-in'
        mode: 'in-out'
        :duration=''
        :key=''
  -->

  <!-- Reusable Transition -->
  <FadeTransition>
    <ul v-if="showMessage">
      <li>Menu Item 1</li>
      <li>Menu Item 2</li>
      <li>Menu Item 3</li>
    </ul>
  </FadeTransition>
</template>

<style scoped>
.appear-enter-active,
.appear-leave-active {
  transition: opacity 1500ms ease;
}
.appear-enter-from,
.appear-leave-to {
  opacity: 0;
}
</style>
