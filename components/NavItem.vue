<template>
  <div
    class="p-4 bg-gray-100 rounded-full flex-grow text-center text-gray-600 shadow-lg max-h-16 relative"
    :class="{'text-gray-900' : active, 'mt-12' : active}"
    @mouseenter="$emit('hovered')"
    @click="$emit('clicked')"
  >
    <h1 class="text-3xl font-bold">
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
