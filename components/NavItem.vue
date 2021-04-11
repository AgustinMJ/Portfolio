<template>
  <div
    class="p-2 xl:p-3 2xl:p-4 bg-gray-100 rounded-full flex-grow text-center text-gray-600 shadow-lg max-h-8 xs:max-h-12 md:max-h-12 xl:max-h-14 2xl:max-h-16 relative"
    :class="{'text-gray-900' : active, 'mt-2 md:mt-4 lg:mt-6 xl:mt-12' : active}"
    @mouseenter="$emit('hovered')"
    @click="$emit('clicked')"
  >
    <h1 class="text-xs xs:text-md md:text-lg lg:text-xl xl:text-2xl 2xl:text-3xl font-bold">
      {{ text }}
    </h1>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'NavItem',
  props: {
    text: {
      type: String,
      default: ''
    },
    active: Boolean
  }
})
</script>

<style scoped>
div {
    cursor: pointer;
}
</style>
