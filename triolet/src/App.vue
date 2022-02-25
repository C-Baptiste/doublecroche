<script setup>
import Metronome from "./components/Metronome.vue"
import Exercice from "./components/Exercice.vue";
</script>

<template>  
<main>
  <div class="flex flex-row">
    <div class="m-8">
      <Exercice/>
    </div>
    <div class="m-8">
      <Metronome/>
    </div>
  </div>
</main>
</template>