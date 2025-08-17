<script setup lang="ts">
import { ref } from 'vue'
import FadeTransition from './components/FadeTransition.vue'
import GsapTransition from './components/GsapTransition.vue'
const show = ref(true)
const showMessage = ref(false)
</script>

<template>
  <div
    class="w-full relative h-[100vh] flex flex-col space-y-[2rem] items-center justify-center"
  >
    <!-- Named Transition -->
    <Transition name="appear" :duration="1500" appear>
      <h1 class="text-2xl font-bold z-20" v-if="show">Hello there!!</h1>
    </Transition>

    <div class="relative h-[100px]">
      <button
        class="bg-gray-100 border border-gray-300 p-2 rounded-md w-full"
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
        <ul
          class="absolute text-nowrap left-[50%] translate-x-[-50%] z-20"
          :class="{'text-white': showMessage }"
          v-if="showMessage"
        >
          <li>Menu Item 1</li>
          <li>Menu Item 2</li>
          <li>Menu Item 3</li>
        </ul>
      </FadeTransition>
    </div>

    <GsapTransition>
      <div v-if="showMessage" @click="showMessage = false" class="circle"/>
    </GsapTransition>
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

.circle {
  @apply absolute left-[50%] flex items-center justify-center translate-x-[-50%] top-[50%] translate-y-[-50%] z-10 w-[480px] h-[480px] bg-[#3490dc] rounded-full;
}
</style>
