<script>
let id = 0
export default {
    data() {
        return {
            exercices: [
            { id: id++, text: 'accent double croche' },
            { id: id++, text: 'bend gamme majeure' },
            { id: id++, text: 'sultans of swing' }
            ]
        }
    }
}
</script>

<template>
<ul>
    <li v-for="exercice in exercices" :key="exercice.id">
        {{ exercice.text }}
    </li>
</ul>
</template>