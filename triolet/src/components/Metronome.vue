<script>
let ac = null
export default {
    data() {
        return {
            source: "",
            tempo: "120",
            timeButtons: [
                {text: "180"},
                {text: "170"},
                {text: "160"},
                {text: "150"},
                {text: "140"},
                {text: "130"},
                {text: "120"},
                {text: "110"},
                {text: "100"},
                {text: "90"},
                {text: "80"},
                {text: "70"},
                {text: "60"},
                {text: "50"},
                {text: "40"}
            ]
        }
    },
    methods: {
      clamp(v, min, max) {
        return Math.min(max, Math.max(min, v))
      },
      clampTempo(t) {
        return this.clamp(t, 30, 300)
      },
      getTempo() {
        return this.clampTempo(parseFloat(this.tempo))
      },
      setup(timeText) {
        this.tempo = timeText
        if (ac !== null) {ac.close()}
        ac = new AudioContext()
        var buf = ac.createBuffer(1, ac.sampleRate * 2, ac.sampleRate)
        var channel = buf.getChannelData(0)
        var phase = 0
        var amp = 1
        var duration_frames = ac.sampleRate / 50
        const f = 330
        for (var i = 0; i < duration_frames; i++) {
            channel[i] = Math.sin(phase) * amp
            phase += 2 * Math.PI * f / ac.sampleRate
            if (phase > 2 * Math.PI) {
              phase -= 2 * Math.PI
            }
            amp -= 1 / duration_frames
          }
        this.source = ac.createBufferSource()
        this.source.buffer = buf
        this.source.loop = true
        this.source.loopEnd = 1 / (this.getTempo() / 60)
        this.source.connect(ac.destination)
        this.source.start()
      },
        stopSound () {
            this.source.stop()
        }
    }
}
</script>

<template>
    <div 
        class="bg-gradient-to-b from-red-400 to-orange-200
        rounded-full
        w-36 
        h-96
        shadow-md
        ">        
        <ul class="pt-3">
            <li v-for="timeButton in timeButtons" >
                <button @click="setup(timeButton.text)"
                    class="w-36
                            text-gray-100
                            hover:font-bold
                            ">
                    {{timeButton.text}}
                </button>
            </li>
        </ul>
    </div>
    <div class="flex
                justify-center">
        <div @click="stopSound"
        class="bg-gradient-to-b from-orange-200 to-orange-50
                h-16
                w-16
                text-center                
                rounded-full
                shadow-inner">
            <button class="pt-3
                        ">
                       <svg xmlns="http://www.w3.org/2000/svg" height="36px" viewBox="0 0 24 24" width="36px" fill="#FFFFFF"><path d="M0 0h24v24H0V0z" fill="none"/><path d="M16 8v8H8V8h8m2-2H6v12h12V6z"/></svg> 
            </button>
        </div>
    </div>
</template>
