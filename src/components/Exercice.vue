<script>
import Timer from "./Timer.vue"
let id = 0
export default {
    data() {
        return {
            newExercice: "",
            exercices: []
        };
    },
    methods: {
        addExercice() {
            this.exercices.push({ id: id++, text: this.newExercice })
            localStorage[id] = this.newExercice
            this.newExercice = ""
        }
    },
    mounted() {
        if (localStorage) {
            for (const [key, value] of Object.entries(localStorage)) {
                this.exercices.push({ id: parseInt(key), text: value })    
            }
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
                    bg-slate-100
                    pt-9
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
<div class="
            border-b-2                    
            w-96
            h-24
            flex flex-row">
    <div class="text-center
                    rounded-full
                    bg-slate-100
                    pt-9
                    border-r-2
                    basis-3/4
                    exercice_font
                    text-slate-800">
            <input v-model="newExercice" @keyup.enter="addExercice"
                    class="bg-slate-100">
    </div>
    <div class="basis-1/4">
        <button @click="addExercice"
                class="h-24 
                w-24
                rounded-full
                shadow-inner
                border-b-2
                exercice_font
                text-3xl
                font-bold
                text-slate-400">
        +
        </button>
    </div>
</div>
</template>

<style>
.exercice_font{
    font-family: 'Architects Daughter', cursive;
}
</style>