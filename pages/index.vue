<template>
  <div>
    <HangingNavbar
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
      <div id="mainFigureHanger" class="bounce-in-top z-30 relative">
        <Hanger
          :item-id="'mainFigure'"
        />
        <img
          id="mainFigure"
          class="mx-auto z-30 relative"
          alt="Software Engineer"
          src="~/assets/software-engineer.svg"
          style="height: 30rem"
          @mouseenter="oscillate"
        >
      </div>
      <img
        id="cv"
        class="mx-auto fade-in relative"
        alt="Curriculum Vitae"
        src="~/assets/curriculum-vitae.svg"
        style="width: 30rem"
      >
      <img
        id="name"
        class="w-96 mx-auto mt-8 fade-in relative"
        alt="Name"
        src="~/assets/name.svg"
        style="animation-duration: 3.7s;"
      >
      <img
        id="title"
        class="w-72 mx-auto mt-8 fade-in z-10 relative"
        alt="Title"
        src="~/assets/title.svg"
        style="animation-duration: 3.9s;"
      >
      <h1 id="beginText" class="mt-12 text-gray-400 text-2xl font-bold text-center constant-fade-in relative">
        Scroll or navigate to begin
      </h1>
    </div>
    <div v-if="index === 1" class="h-screen overflow-hidden">
      <Hanger
        :item-id="'agusCard'"
        :double="true"
        class="bounce-in-top"
      />
      <div class="px-20 mx-auto mt-72 max-w-7xl">
        <div id="agusCard" class="bg-gray-100 rounded-3xl flex flex-col p-12 space-y-8 bounce-in-top">
          <div class="flex">
            <div class="rounded-full border-2 border-gray-600">
              <img
                id="profileImage"
                alt="profile image"
                src="~/assets/Profile.png"
                class="rounded-full w-64 h-64"
              >
            </div>
            <div class="flex flex-col justify-center text-gray-900">
              <div class="ml-16 space-y-3">
                <h1 class="font-bold text-4xl">
                  Agustín Millán Jiménez
                </h1>
                <div>
                  <svg
                    fill="#171717"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 48 48"
                    class="w-8 inline"
                  >
                    <path
                      d="M 24 2.0195312 C 23.826 2.0195312 23.6505 2.0998125 23.5625 2.2578125 C 23.4365 2.4848125 20.470719 7.8245781 20.011719 9.8925781 C 19.817719 10.767578 20.045391 11.662969 20.650391 12.417969 C 21.421391 13.378969 22.736 14 24 14 C 25.264 14 26.578609 13.378969 27.349609 12.417969 C 27.954609 11.662969 28.182281 10.767578 27.988281 9.8925781 C 27.529281 7.8255781 24.5635 2.4848125 24.4375 2.2578125 C 24.3495 2.0998125 24.174 2.0195312 24 2.0195312 z M 21.462891 15.451172 C 21.179891 15.904172 21 16.427 21 17 L 21 21 L 27 21 L 27 17 C 27 16.427 26.820109 15.904172 26.537109 15.451172 C 25.738109 15.801172 24.87 16 24 16 C 23.13 16 22.261891 15.801172 21.462891 15.451172 z M 12.5 23 C 9.468 23 7 25.468 7 28.5 L 7 30 C 7 30.874 7 32.5 11.25 32.5 C 13.859 32.5 16.5 31.47 16.5 29.5 C 16.5 28.947 16.947 28.5 17.5 28.5 C 18.053 28.5 18.5 28.947 18.5 29.5 C 18.5 31.156 21.828 32.5 24 32.5 C 26.666 32.5 29.5 31.448 29.5 29.5 C 29.5 28.947 29.947 28.5 30.5 28.5 C 31.053 28.5 31.5 28.947 31.5 29.5 C 31.5 31.47 34.141 32.5 36.75 32.5 C 41 32.5 41 30.874 41 30 L 41 28.5 C 41 25.468 38.532 23 35.5 23 L 12.5 23 z M 17.613281 32.041016 C 16.427281 33.559016 14.134 34.5 11.25 34.5 C 9.43 34.5 8.028 34.191328 7 33.611328 L 7 41 L 41 41 L 41 33.611328 C 39.972 34.191328 38.57 34.5 36.75 34.5 C 33.927 34.5 31.673797 33.597719 30.466797 32.136719 C 29.198797 33.585719 26.861 34.5 24 34.5 C 22.115 34.5 19.196281 33.677016 17.613281 32.041016 z M 4.5 43 C 3.672 43 3 43.672 3 44.5 C 3 45.328 3.672 46 4.5 46 L 43.5 46 C 44.328 46 45 45.328 45 44.5 C 45 43.672 44.328 43 43.5 43 L 4.5 43 z"
                    />
                  </svg>
                  <p class="inline ml-4 text-xl align-bottom">
                    26/09/2000
                  </p>
                </div>
                <div>
                  <svg
                    fill="#171717"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 48 48"
                    class="w-8 inline"
                  >
                    <path
                      d="M24,4C14.626,4,7,11.626,7,21c0,4.036,1.449,7.953,4.093,11.048c0.302,0.343,7.427,8.439,9.807,10.708 C21.769,43.585,22.884,44,24,44s2.231-0.415,3.101-1.244c2.767-2.639,9.524-10.385,9.82-10.725C39.551,28.953,41,25.036,41,21 C41,11.626,33.374,4,24,4z M24,26c-2.761,0-5-2.239-5-5s2.239-5,5-5s5,2.239,5,5S26.761,26,24,26z"
                    />
                  </svg>
                  <p class="inline ml-4 text-xl align-middle">
                    Palafolls, Barcelona, Catalonia, SPain
                  </p>
                </div>
                <div>
                  <svg
                    fill="#171717"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 48 48"
                    class="w-8 inline"
                  >
                    <path
                      d="M 10 8 C 6.86 8 4.2795313 10.42 4.0195312 13.5 L 24 24.289062 L 43.980469 13.5 C 43.720469 10.42 41.14 8 38 8 L 10 8 z M 4 16.890625 L 4 34 C 4 37.31 6.69 40 10 40 L 38 40 C 41.31 40 44 37.31 44 34 L 44 16.890625 L 24.710938 27.320312 C 24.490938 27.440312 24.25 27.5 24 27.5 C 23.75 27.5 23.509062 27.440313 23.289062 27.320312 L 4 16.890625 z"
                    />
                  </svg>
                  <p class="inline ml-4 text-xl">
                    agustimillanjimenez@gmail.com
                  </p>
                </div>
                <div>
                  <svg
                    fill="#171717"
                    xmlns="http://www.w3.org/2000/svg"
                    viewBox="0 0 24 24"
                    class="w-8 inline"
                  >
                    <path
                      d="M16.5,1h-9C6.12,1,5,2.12,5,3.5v17C5,21.88,6.12,23,7.5,23h9c1.38,0,2.5-1.12,2.5-2.5v-17C19,2.12,17.88,1,16.5,1z M12,21.125c-0.622,0-1.125-0.503-1.125-1.125s0.503-1.125,1.125-1.125s1.125,0.503,1.125,1.125S12.622,21.125,12,21.125z M17,18H7 V4h10V18z"
                    />
                  </svg>
                  <p class="inline ml-4 text-xl align-middle">
                    +34652032264
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="bg-gray-400" style="height: 2px;" />
          <div class="text-xl">
            <p>
              I am a passionate Computer Science Student, specialized in Software
              Engineering.
            </p>
            <p>
              Ready to take the next step and start working, but most importantly, eager to
              learn real life skills and to grow as an engineer.
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Hanger from './../components/Hanger.vue'
import HangingNavbar from './../components/HangingNavbar.vue'

export default Vue.extend({
  name: 'App',
  components: {
    Hanger,
    HangingNavbar
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
      e.deltaY > 0 ? this.changeIndex(this.index + 1) : this.changeIndex(this.index - 1)
    })
  },
  destroyed () {
    document.removeEventListener('wheel', (e: WheelEvent) => {
      e.deltaY > 0 ? this.changeIndex(this.index + 1) : this.changeIndex(this.index - 1)
    })
  },
  methods: {
    oscillate (event: MouseEvent) {
      const mainHandler = document.getElementById('mainFigureHanger')
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
            function () {
              return mainHandler?.classList.remove('oscillate-left')
            }
          )
        } else {
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

              mainHandler?.classList.remove('bounce-in-top')
              mainHandler?.classList.remove('oscillate-right')
              mainHandler?.classList.remove('oscillate-left')

              name!.classList.remove('fade-in')
              cv!.classList.remove('fade-in')
              title!.classList.remove('fade-in')
              beginText?.classList.remove('fade-in')
              beginText?.classList.remove('constant-fade-in')

              mainHandler?.classList.add('bounce-out-top')

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
          if (this.index === 0) {
            Promise.all(
              document!.getAnimations().map(
                function (animation) {
                  return animation.finished
                }
              )
            ).then(() => {
              this.visibleNavbarThreads = true
              this.index = -1
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
                    navbar!.style.top = '0'
                    navbar!.style.bottom = 'unset'
                    navbar!.classList.add('mt-12')
                    this.index = newIndex
                    Vue.nextTick(() => {
                      this.bus.$emit('repositionNavbarThreads')
                    })
                    this.transitioning = false
                    hangingNavbar?.classList.remove('bounce-in-bot')
                    Vue.nextTick(() => {
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

<style>
.bounce-in-top {
  animation: bounce-in-top 2s ease-in-out;
  transform-origin: top;
}
@keyframes bounce-in-top {
  0%   { opacity: 0; transform: translateY(0px); }
  1%   { opacity: 1; transform: translateY(-100vh); }
  20%  { transform: translateY(0px); }
  40% { transform: translateY(-50px); }
  60% { transform: translateY(0px); }
  80% { transform: translateY(-10px); }
  100% { transform: translateY(0px); }
}

.bounce-out-top {
  animation: bounce-out-top 2s ease-in-out;
  transform-origin: top;
}
@keyframes bounce-out-top {
  0%   { transform: translateY(0px); }
  10%  { transform: translateY(-50px); }
  50% { transform: translateY(0px); }
  100% { transform: translateY(-100vh); }
}

.bounce-in-bot {
  animation: bounce-in-bot 2s ease-in-out;
  transform-origin: bottom;
}
@keyframes bounce-in-bot {
  0%   { opacity: 0; transform: translateY(0px); }
  1%   { opacity: 1; transform: translateY(100vh); }
  20%  { transform: translateY(0px); }
  40% { transform: translateY(20px); }
  60% { transform: translateY(0px); }
  80% { transform: translateY(10px); }
  100% { transform: translateY(0px); }
}

.fade-in {
  animation: fade-in 3.5s ease;
}
@keyframes fade-in {
  0%   { opacity: 0; }
  50%   { opacity: 0; }
  100% { opacity: 1; }
}

.constant-fade-in {
  animation:
    fade-in 5.5s ease 0s,
    constant-fade 3s ease 4.2s infinite
}
@keyframes constant-fade {
  0%   { opacity: 1; }
  50% { opacity: 0; }
  100% { opacity: 1; }
}

.fade-out-top {
  animation: fade-out-top 2s ease 0s;
}
@keyframes fade-out-top {
  100% {
    transform: translateY(-50px);
    opacity: 0;
  }
}

.oscillate-right {
  animation: oscillate-right 3.5s ease;
  transform-origin: top;
}
@keyframes oscillate-right {
  0%   { transform: rotate(0deg); }
  20%  { transform: rotate(10deg); }
  40% { transform: rotate(-10deg); }
  60% { transform: rotate(5deg); }
  80% { transform: rotate(-5deg); }
  100% { transform: rotate(0deg); }
}

.oscillate-left {
  animation: oscillate-left 3.5s ease;
  transform-origin: top;
}
@keyframes oscillate-left {
  0%   { transform: rotate(0deg); }
  20%  { transform: rotate(-10deg); }
  40% { transform: rotate(10deg); }
  60% { transform: rotate(-5deg); }
  80% { transform: rotate(5deg); }
  100% { transform: rotate(0deg); }
}

.scroll-up {
  animation: scroll-up 2s ease-in-out;
  transform-origin: top;
}
@keyframes scroll-up {
  0%   { transform: translateY(0px); }
  10%  { transform: translateY(-50px); }
  50% { transform: translateY(0px); }
  100% { transform: translateY(calc(-100vh + 10.5rem)); }
}

.scroll-down {
  animation: scroll-down 2s ease-in-out;
  transform-origin: top;
}
@keyframes scroll-down {
  0%   { transform: translateY(0px); }
  10%  { transform: translateY(50px); }
  50% { transform: translateY(0px); }
  100% { transform: translateY(calc(100vh - 10.5rem)); }
}
</style>
