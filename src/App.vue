<script setup lang="ts">
import { ref } from 'vue'
const show = ref(true)
const showMessage = ref(false)
</script>

<template>
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
  <Transition name="fade">
    <ul v-if="showMessage">
      <li>Menu Item 1</li>
      <li>Menu Item 2</li>
      <li>Menu Item 3</li>
    </ul>
  </Transition>
</template>

<style scoped>
/* Named Transitions to diversify */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease, transform 0.5s ease;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}

.appear-enter-active,
.appear-leave-active {
  transition: opacity 1500ms ease;
}
.appear-enter-from,
.appear-leave-to {
  opacity: 0;
}
</style>
