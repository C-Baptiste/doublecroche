<script>
export default {
    data () {
        return {
            Countdown: "",
            BgColor: {
                backgroundColor: "",
                display: "none"
            },
            Player_Visibility: {
                display: ""
            }
        }
    },
    methods: {
        setColor () {
            this.BgColor.background = "linear-gradient(#736CED, #6C8EAD)"
        },
        startCountdown () {
            this.Player_Visibility.display = "none"
            this.BgColor.display = ""
            this.Countdown = ""
            setInterval(this.setColor, 300000)
        }
    }
}
</script>

<template>
<button @click="startCountdown"
        v-bind:style="Player_Visibility"
        class="pt-7 pl-8"
        >
    <svg xmlns="http://www.w3.org/2000/svg" height="36px" viewBox="0 0 24 24" width="36px" fill="#94a3b8"><path d="M0 0h24v24H0V0z" fill="none"/><path d="M10 8.64L15.27 12 10 15.36V8.64M8 5v14l11-7L8 5z"/></svg>
</button>
<div  v-bind:style="BgColor"
        class="h-24 
                w-24
                rounded-full                
                border-b-2">
    <div class="pt-9
                pl-10
                timer_font
                text-slate-800
                bg-white
                h-16
                w-16
                rounded-full">
        {{ Countdown }}
    </div>
</div>
</template>

<style>
.timer_font{
    font-family: 'Architects Daughter', cursive;
}
</style>