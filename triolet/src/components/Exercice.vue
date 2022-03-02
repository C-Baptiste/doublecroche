<script>
import Timer from "./Timer.vue"
let id = 0
export default {
    data() {
        return {
            newExercice: "",
            exercices: [
                { id: id++, text: "accent double croche" },
                { id: id++, text: "bend gamme majeure" },
                { id: id++, text: "sultans of swing" }
            ]
        };
    },
    methods: {
        addExercice() {
            this.exercices.push({ id: id++, text: this.newExercice })
            this.newExercice = ""
        }
    },
    components: { Timer }
}
</script>

<template>
<ul>
    <li v-for="exercice in exercices" :key="exercice.id"
        class="
            border-b-2                    
            w-96
            h-24
            flex flex-row">
        <div class="text-center
                    rounded-full
                    bg-slate-50
                    pt-6
                    border-r-2
                    basis-3/4
                    exercice_font">
            {{ exercice.text }}
        </div>
        <div class="basis-1/4">
            <Timer/>
        </div>
    </li>
</ul>
<input v-model="newExercice" @keyup.enter="addExercice">
<button @click="addExercice">+</button>
</template>

<style>
.exercice_font{
    font-family: 'Architects Daughter', cursive;
    color: #412722;
}
</style>