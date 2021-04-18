<template>
  <div>
    <hanging-navbar
      id="hangingNavbar"
      class="z-20 bounce-in-bot"
      :bus="bus"
      :visible-threads="visibleNavbarThreads"
      :active-index="index"
      @clicked="(newIndex) => {
        changeIndex(newIndex);
      }"
    />
    <div v-if="index === 0" class="h-screen overflow-hidden">
      <main-screen />
    </div>
    <div v-if="index === 1" class="h-screen overflow-hidden">
      <profile-screen />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import HangingNavbar from './../components/HangingNavbar.vue'
import MainScreen from './mainScreen.vue'
import ProfileScreen from './profileScreen.vue'
const debounce = require('debounce')

export default Vue.extend({
  name: 'App',
  components: {
    HangingNavbar,
    MainScreen,
    ProfileScreen
  },
  data () {
    return {
      index: 0,
      animatingMainFigure: false,
      visibleNavbarThreads: false,
      transitioning: false,
      bus: new Vue()
    }
  },
  beforeMount () {
    document.addEventListener('wheel', (e: WheelEvent) => {
      debounce(e.deltaY > 0 ? this.changeIndex(this.index + 1) : this.changeIndex(this.index - 1), 6000)
    })
  },
  destroyed () {
    document.removeEventListener('wheel', (e: WheelEvent) => {
      debounce(e.deltaY > 0 ? this.changeIndex(this.index + 1) : this.changeIndex(this.index - 1), 6000)
    })
  },
  methods: {
    // Method to make an element oscillate
    oscillate (event: MouseEvent) {
      const mainHandler = document.getElementById('mainFigureHanger')
      // If there are no animations and we are not transitioning between screens then animate
      if (mainHandler?.getAnimations().length === 0 && !this.transitioning) {
        if (event.pageX < window.innerWidth / 2) {
          mainHandler?.classList.remove('bounce-in-top')
          mainHandler?.classList.add('oscillate-left')
          Promise.all(
            mainHandler?.getAnimations().map(
              function (animation) {
                return animation.finished
              }
            )
          ).then(
            // When animation is done, remove it.
            function () {
              return mainHandler?.classList.remove('oscillate-left')
            }
          )
        } else {
          // Same but on the other side
          mainHandler?.classList.remove('bounce-in-top')
          mainHandler?.classList.add('oscillate-right')
          Promise.all(
            mainHandler?.getAnimations().map(
              function (animation) {
                return animation.finished
              }
            )
          ).then(
            function () {
              return mainHandler?.classList.remove('oscillate-right')
            }
          )
        }
      }
    },
    // Method to navigate between screens
    changeIndex (newIndex: number) {
      if (newIndex > this.index) {
        if (this.index < 4) {
          this.transitioning = true
          switch (this.index) {
            case 0: {
              const mainHandler = document.getElementById('mainFigureHanger')
              const cv = document.getElementById('cv')
              const name = document.getElementById('name')
              const title = document.getElementById('title')
              const beginText = document.getElementById('beginText')

              // Remove all previous animations in order to add the new ones
              mainHandler?.classList.remove('bounce-in-top')
              mainHandler?.classList.remove('oscillate-right')
              mainHandler?.classList.remove('oscillate-left')

              name!.classList.remove('fade-in')
              cv!.classList.remove('fade-in')
              title!.classList.remove('fade-in')
              beginText?.classList.remove('fade-in')
              beginText?.classList.remove('constant-fade-in')

              mainHandler?.classList.add('bounce-out-top')

              // This animationDuration change is needed because it was set to some value previously
              cv!.style.animationDuration = '2s'
              cv!.classList.add('fade-out-top')

              name!.style.animationDuration = '2s'
              name!.classList.add('fade-out-top')

              title!.style.animationDuration = '2s'
              title!.classList.add('fade-out-top')

              beginText?.classList.add('fade-out-top')

              break
            }
            case 1: {
              const agusCard = document.getElementById('agusCard')
              agusCard?.classList.remove('bounce-in-top')
              agusCard?.classList.add('bounce-out-top')
              const threadOne = document.getElementById('agusCardthread')
              const threadTwo = document.getElementById('agusCardthread2')
              threadOne?.classList.remove('bounce-in-top')
              threadOne?.classList.add('bounce-out-top')
              threadTwo?.classList.remove('bounce-in-top')
              threadTwo?.classList.add('bounce-out-top')
              break
            }
            default: {
              this.index = newIndex
              break
            }
          }
          // If index is 0 we have to make the navbar threads appear
          if (this.index === 0) {
            Promise.all(
            document!.getAnimations().map(
              function (animation) {
                return animation.finished
              }
            )
            ).then(() => {
              this.visibleNavbarThreads = true
              // We set index to -1 in order to hide everything. This way we avoid bugs due to animation durations.
              this.index = -1
              // Wait until the threads have completed their animation to move the navbar
              setTimeout(() => {
                const navbar = document.getElementById('navbar')
                const hangingNavbar = document.getElementById('hangingNavbar')
                hangingNavbar?.classList.add('scroll-up')
                Promise.all(
                hangingNavbar!.getAnimations().map(
                  function (animation) {
                    return animation.finished
                  }
                )
                ).then(
                  () => {
                    // Stablish new navbar position
                    navbar!.style.top = '0'
                    navbar!.style.bottom = 'unset'
                    navbar!.classList.add('mt-12')
                    // As all animations end, we can finally set the new screen index
                    this.index = newIndex
                    Vue.nextTick(() => {
                      this.bus.$emit('repositionNavbarThreads')
                    })
                    this.transitioning = false
                    hangingNavbar?.classList.remove('bounce-in-bot')
                    Vue.nextTick(() => {
                      // This is needed to reposition threads
                      this.bus.$emit('repositionNavbarThreads')
                    })
                  }
                )
              }, 500)
            })
          } else {
            Promise.all(
              document.getAnimations().map(
                function (animation) {
                  return animation.finished
                }
              )
            ).then(() => {
              this.index = newIndex
              this.transitioning = false
              Vue.nextTick(() => {
                this.bus.$emit('repositionNavbarThreads')
              })
            })
          }
        }
      } else if (this.index > 0) {
        this.transitioning = true
        switch (this.index) {
          case 1: {
            const agusCard = document.getElementById('agusCard')
            agusCard?.classList.remove('bounce-in-top')
            agusCard?.classList.add('bounce-out-top')
            const threadOne = document.getElementById('agusCardthread')
            const threadTwo = document.getElementById('agusCardthread2')
            threadOne?.classList.remove('bounce-in-top')
            threadOne?.classList.add('bounce-out-top')
            threadTwo?.classList.remove('bounce-in-top')
            threadTwo?.classList.add('bounce-out-top')
            Promise.all(
              document.getAnimations().map(
                function (animation) {
                  return animation.finished
                }
              )
            ).then(() => {
              this.index = -1
              Vue.nextTick(() => {
                this.bus.$emit('repositionNavbarThreads')
                this.visibleNavbarThreads = false
                const navbar = document.getElementById('navbar')
                const hangingNavbar = document.getElementById('hangingNavbar')
                hangingNavbar?.classList.remove('scroll-up')
                hangingNavbar?.classList.add('scroll-down')
                document.getElementById('profileNavItemthread')?.classList.add('enlarge-down')
                Promise.all(
                hangingNavbar!.getAnimations().map(
                  function (animation) {
                    return animation.finished
                  }
                )
                ).then(
                  () => {
                  navbar!.style.top = 'unset'
                  navbar!.style.bottom = '0'
                  navbar!.classList.add('mb-12')
                  this.index = newIndex
                  Vue.nextTick(() => {
                    this.bus.$emit('repositionNavbarThreads')
                  })
                  this.transitioning = false
                  hangingNavbar?.classList.remove('scroll-down')
                  Vue.nextTick(() => {
                    this.bus.$emit('repositionNavbarThreads')
                  })
                  }
                )
              })
            })
            break
          }
          default: {
            this.index = newIndex
            Vue.nextTick(() => {
              this.bus.$emit('repositionNavbarThreads')
            })
          }
        }
      }
    }
  }
})
</script>
