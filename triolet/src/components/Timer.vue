<script>
export default {
    data () {
        return {
            Countdown: "",
            BgColor: {
                backgroundColor: ""
            }
        }
    },
    methods: {
        setColor () {
            this.BgColor.background = "linear-gradient(#5F00BA, #A09BE7)"
        },
        startCountdown () {
            this.Countdown = "5'"
            setInterval(this.setColor, 3000)
        }
    }
}
</script>

<template>
<div @click="startCountdown" v-bind:style="BgColor"
        class="">
    {{ Countdown }}
</div>

</template>