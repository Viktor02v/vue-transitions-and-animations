<script setup lang="ts">
import { ref } from 'vue'
import FadeTransition from './components/FadeTransition.vue'
const show = ref(true)
const showMessage = ref(false)
</script>

<template>
  <div
    class="w-full h-[100vh] flex flex-col space-y-[2rem] items-center justify-center"
  >
    <!-- Named Transition -->
    <Transition name="appear" :duration="1500" appear>
      <h1 class="text-2xl font-bold" v-if="show">Hello there!!</h1>
    </Transition>
    <div class="">
      <button
        class="bg-gray-100 border border-gray-300 p-2 rounded-md relative w-fill"
        @click="showMessage = !showMessage"
      >
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
        <ul class="absolute w-full" v-if="showMessage">
          <li>Menu Item 1</li>
          <li>Menu Item 2</li>
          <li>Menu Item 3</li>
        </ul>
      </FadeTransition>
    </div>
  </div>
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
