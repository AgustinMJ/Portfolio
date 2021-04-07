<template>
  <div class="navbar w-full h-full justify-between">
    <Hanger :bus="bus" :item-id="'profileNavItem'" :visible="visibleThreads" />
    <Hanger :bus="bus" :item-id="'educationNavItem'" :visible="visibleThreads" />
    <Hanger :bus="bus" :item-id="'skenNavItem'" :visible="visibleThreads" />
    <Hanger :bus="bus" :item-id="'exprNavItem'" :visible="visibleThreads" />
    <div id="navbar" class="navItem w-full mb-12 px-20 flex justify-between space-x-28">
      <NavItem id="profileNavItem" :text="'Profile'" :active="activeIndex === 1" @hovered="bounceUp('profileNavItem')" @clicked="$emit('clicked', 1)" />
      <NavItem id="educationNavItem" :text="'Education'" :active="activeIndex === 2" @hovered="bounceUp('educationNavItem')" @clicked="$emit('clicked', 2)" />
      <NavItem id="skenNavItem" :text="'Skills & Endorsements'" :active="activeIndex === 3" @hovered="bounceUp('skenNavItem')" @clicked="$emit('clicked', 3)" />
      <NavItem id="exprNavItem" :text="'Experience & Projects'" :active="activeIndex === 4" @hovered="bounceUp('exprNavItem')" @clicked="$emit('clicked', 4)" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import NavItem from './NavItem.vue'
import Hanger from './Hanger.vue'
export default Vue.extend({
  name: 'HangingNavbar',
  components: {
    NavItem,
    Hanger
  },
  props: {
    activeIndex: {
      type: Number,
      default: 0
    },
    visibleThreads: Boolean,
    bus: Vue
  },
  methods: {
    bounceUp (id: string) {
      const mainHandler = document.getElementById(id)
      if (mainHandler?.getAnimations().length === 0) {
        mainHandler?.classList.add('bounce-up')
        Promise.all(
          mainHandler?.getAnimations().map(
            function (animation) {
              return animation.finished
            }
          )
        ).then(
          function () {
            return mainHandler?.classList.remove('bounce-up')
          }
        )
      }
    }
  }
})
</script>

<style scoped>
.navbar {
    position: fixed;
    top: 0;
}

.navItem {
    position: fixed;
    bottom: 0;
}
.bounce-up {
    animation: bounce-up 0.5s ease-out;
}
@keyframes bounce-up {
  0%   { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
  100% { transform: translateY(0px); }
}
</style>
