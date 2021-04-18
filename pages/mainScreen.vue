<template>
  <div>
    <div id="mainFigureHanger" class="bounce-in-top z-30 relative">
      <hanger
        :item-id="'mainFigure'"
        :visible="true"
      />
      <img
        id="mainFigure"
        class="mx-auto z-30 relative w-80 xs:w-96 md:w-5/12 xl:w-4/12"
        alt="Software Engineer"
        src="~/assets/software-engineer.svg"
        @mouseenter="oscillate"
      >
    </div>
    <img
      id="cv"
      class="mx-auto fade-in relative w-60 xs:w-2/6 lg:w-1/4"
      alt="Curriculum Vitae"
      src="~/assets/curriculum-vitae.svg"
    >
    <img
      id="name"
      class="w-44 xs:w-3/12 2xl:w-80 mx-auto mt-4 xl:mt-6 2xl:mt-8 fade-in relative"
      alt="Name"
      src="~/assets/name.svg"
      style="animation-duration: 3.7s;"
    >
    <img
      id="title"
      class="w-32 xs:w-1/5 2xl:w-64 mx-auto mt-4 xl:mt-6 2xl:mt-8 fade-in z-10 relative"
      alt="Title"
      src="~/assets/title.svg"
      style="animation-duration: 3.9s;"
    >
    <h1 id="beginText" class="mt-4 lg:mt-6 xl:mt-8 2xl:mt-12 text-gray-400 text-xs sm:text-sm md:text-md lg:text-lg xl:text-2xl font-bold text-center constant-fade-in relative">
      Scroll or navigate to begin
    </h1>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Hanger from '../components/Hanger.vue'
export default Vue.extend({
  name: 'MainScreen',
  components: {
    Hanger
  }
})
</script>
