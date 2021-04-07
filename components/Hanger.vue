<template>
  <div class="flex-grow">
    <transition name="fade-progressively">
      <div v-show="visible" :id="itemId + 'thread'" class="thread" />
    </transition>
    <transition name="fade-progressively">
      <div v-show="visible && double" :id="itemId + 'thread2'" class="thread" />
    </transition>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'Hanger',
  props: {
    itemId: {
      type: String,
      default: ''
    },
    visible: {
      type: Boolean,
      default: true
    },
    double: {
      type: Boolean,
      default: false
    },
    bus: {
      type: Vue,
      default: null
    }
  },
  watch: {
    visible () {
      this.rePositionThread()
    }
  },
  mounted () {
    this.rePositionThread()
    if (this.bus !== null) {
      this.bus.$on('repositionNavbarThreads', () => this.rePositionThread())
    }
  },
  beforeMount () {
    window.addEventListener('resize', this.rePositionThread)
  },
  destroyed () {
    window.removeEventListener('resize', this.rePositionThread)
  },
  methods: {
    rePositionThread () {
      const itemPosition = document.getElementById(this.itemId)?.getBoundingClientRect()
      const thread = document.getElementById(this.itemId + 'thread')
      if (!this.double) {
        const x = itemPosition!.x + itemPosition!.width / 2
        const y = itemPosition!.y + itemPosition!.height / 2 + 100
        thread!.style.left = x.toString() + 'px'
        thread!.style.height = y.toString() + 'px'
      } else {
        const thread2 = document.getElementById(this.itemId + 'thread2')
        const x1 = itemPosition!.x + itemPosition!.width / 6
        const x2 = itemPosition!.x + itemPosition!.width * 5 / 6
        const y = itemPosition!.y + itemPosition!.height / 2 + 100
        thread!.style.left = x1.toString() + 'px'
        thread!.style.height = y.toString() + 'px'
        thread2!.style.left = x2.toString() + 'px'
        thread2!.style.height = y.toString() + 'px'
      }
    }
  }
})
</script>

<style scoped>
.thread {
    width: 2px;
    height: 400px;
    position: fixed;
    top: -100px;
    background-color: #737373;
    z-index: -1;
    opacity: 0.8;
}

.fade-progressively-enter-active, .fade-progressively-leave-active {
    transition: all 0.5s;
}
.fade-progressively-enter, .fade-progressively-leave-to /* .fade-leave-active below version 2.1.8 */ {
  transform: translateY(-100vh);
}
</style>
