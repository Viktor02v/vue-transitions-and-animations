<template>
  <!-- Class Override props 
  enter-from-class
  enter-active-class
  enter-to-class
  leave-from-class
  leave-active-class
  leave-to-class -->
  <Transition enter-active-class="transition-opacity duration-500" name="fade">
    <slot />
  </Transition>
</template>

<style scoped>
/* Named Transitions to diversify */
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
</style>
