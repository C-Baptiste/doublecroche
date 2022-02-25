<script>



export default {
    data() {
        return {
            oscillateur: ""
        }
    },
    methods: {
        startSound () {
            var contexteAudio = new (window.AudioContext || window.webkitAudioContext)()

            this.oscillateur = contexteAudio.createOscillator()
            var noeudGain = contexteAudio.createGain()

            this.oscillateur.connect(noeudGain)
            noeudGain.connect(contexteAudio.destination)

            this.oscillateur.type = 'sine' // onde sinusoïdale — les autres valeurs possible sont : 'square', 'sawtooth', 'triangle' et 'custom'
            this.oscillateur.frequency.value = 500 // valeur en hertz
            this.oscillateur.start()
        },
        stopSound () {
            this.oscillateur.stop()
        }
    }
}


</script>

<template>
    <div @click="startSound"
        class="bg-gradient-to-b from-rose-900 to-rose-50
        w-48 
        h-96 
        rounded
        ">
        150
    </div>
    <div @click="stopSound"
        class="bg-slate-200">
        stop
    </div>
</template>