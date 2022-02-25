<script>
let id = 0
export default {
    data() {
        return {
            newExercice: '',
            exercices: [
            { id: id++, text: 'accent double croche' },
            { id: id++, text: 'bend gamme majeure' },
            { id: id++, text: 'sultans of swing' }
            ]
        }
    },
    methods: {
        addExercice() {
            this.exercices.push({ id: id++, text: this.newExercice})
            this.newExercice = ''
        }
    }
}
</script>

<template>
<ul>
    <li v-for="exercice in exercices" :key="exercice.id"
        class="bg-slate-50
                    border-b-2
                    rounded                    
                    w-96
                    h-24">
        <div class="text-center
                    pt-6">
            {{ exercice.text }}
        </div>
    </li>    
</ul>
<input v-model="newExercice" @keyup.enter="addExercice">
<button @click="addExercice">+</button>
</template>