<script>
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
        var ac = new AudioContext()
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
        this.source.start(0)
      },
        stopSound () {
            this.source.stop()
        }
    }
}
</script>

<template>
    <div 
        class="bg-gradient-to-b from-rose-900 to-rose-50
        w-36 
        h-96
        rounded
        ">        
        <ul>
            <li @click="setup(timeButton.text)" v-for="timeButton in timeButtons">
                {{timeButton.text}}
            </li>
        </ul>
    </div>
    <div @click="stopSound"
        class="bg-slate-200">
        stop
    </div>
</template>
