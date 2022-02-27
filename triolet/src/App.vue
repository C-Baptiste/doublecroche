<script setup>
import Metronome from "./components/Metronome.vue"
import Exercice from "./components/Exercice.vue"
</script>

<template>  
<main class="">
  <div class="flex
              justify-end
              ">
    <div class="m-10">exercices</div>
    <div class="m-10">login</div>
    <div class="m-10">logout</div>
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