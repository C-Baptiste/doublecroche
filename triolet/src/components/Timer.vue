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
            this.BgColor.backgroundColor = "#a7f3d0"
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