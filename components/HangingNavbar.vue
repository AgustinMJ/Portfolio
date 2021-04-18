<template>
  <div class="navbar w-full h-full justify-between">
    <hanger :bus="bus" :item-id="'profileNavItem'" :visible="visibleThreads" />
    <hanger :bus="bus" :item-id="'educationNavItem'" :visible="visibleThreads" />
    <hanger :bus="bus" :item-id="'skenNavItem'" :visible="visibleThreads" />
    <hanger :bus="bus" :item-id="'exprNavItem'" :visible="visibleThreads" />
    <div id="navbar" class="navItem w-full mb-8 xl:mb-12 px-4 md:px-8 lg:px-14 xl:px-20 flex justify-between space-x-4 md:space-x-10 lg:space-x-16 xl:space-x-24 2xl:space-x-28">
      <nav-item id="profileNavItem" :text="'Profile'" :active="activeIndex === 1" @hovered="bounceUp('profileNavItem')" @clicked="$emit('clicked', 1)" />
      <nav-item id="educationNavItem" :text="'Education'" :active="activeIndex === 2" @hovered="bounceUp('educationNavItem')" @clicked="$emit('clicked', 2)" />
      <nav-item id="skenNavItem" :text="'Skills'" :active="activeIndex === 3" @hovered="bounceUp('skenNavItem')" @clicked="$emit('clicked', 3)" />
      <nav-item id="exprNavItem" :text="'Projects'" :active="activeIndex === 4" @hovered="bounceUp('exprNavItem')" @clicked="$emit('clicked', 4)" />
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
</style>
