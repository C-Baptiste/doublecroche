<script setup>
import Metronome from "./components/Metronome.vue"
import Exercice from "./components/Exercice.vue"
</script>

<template>  
<main class="relative">
  <div class="fixed -left-96 -top-72
            -z-10
            ">
            <svg id="visual" viewBox="0 0 900 600" width="900" height="600" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><rect x="0" y="0" width="900" height="600" fill="#FFFFFF"></rect><g transform="translate(446.9271986150405 314.5926450878909)"><path d="M178.9 -252.8C247.1 -234.5 328.2 -210.7 322.3 -164.5C316.4 -118.4 223.5 -49.8 196.5 17.1C169.5 83.9 208.3 149 189.2 154.9C170 160.8 92.9 107.4 34.5 130.5C-24 153.7 -63.8 253.4 -88.9 263.8C-114 274.3 -124.2 195.4 -169.5 145.5C-214.7 95.7 -294.9 74.8 -312.5 37.1C-330.1 -0.6 -285.1 -55.1 -254.4 -113.6C-223.7 -172.1 -207.3 -234.5 -167.3 -265.8C-127.2 -297 -63.6 -297 -4.1 -290.5C55.3 -284.1 110.7 -271.2 178.9 -252.8" fill="#f1f5f9"></path></g></svg>
  </div>
  <div class="fixed right-0 bottom-0
            -z-20
            ">
    <svg id="visual" viewBox="0 0 900 600" width="900" height="600" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><rect x="0" y="0" width="900" height="600" fill="#FFFFFF"></rect><g transform="translate(934.4716498235847 566.6262025166385)"><path d="M149.3 -151.4C187.8 -110.8 209.4 -55.4 216.3 7C223.3 69.3 215.6 138.6 177.1 193.1C138.6 247.6 69.3 287.3 13.8 273.5C-41.7 259.7 -83.4 192.4 -145.9 137.9C-208.4 83.4 -291.7 41.7 -287.4 4.3C-283.1 -33.1 -191.3 -66.3 -128.8 -107C-66.3 -147.6 -33.1 -195.8 11.1 -206.9C55.4 -218.1 110.8 -192.1 149.3 -151.4" fill="#f1f5f9"></path></g></svg>
  </div>
  <div class="flex
              justify-end
              ">
    <div class="m-10">Exercices</div>
    <div class="m-10">Guitar Roadmap</div>
    <div class="m-10">Login</div>
  </div>
  <div class="flex 
              justify-center
              ">
    <div class="m-10">
      <Exercice/>
    </div>
    <div class="m-10">
      <Metronome/>
    </div>
  </div>
</main>
</template>