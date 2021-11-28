<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
</template>

<script>
export default {
    props:['delay'],

    data(){
        return{
            showBlock:false,
            timer: null,
            reactionTime:0
        }},

    //Run this after the component is mounted
    mounted(){
        console.log("Block Component Mounted")
        //Show the Block after Delay
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay )

    }, 

    //Run this after a data is updated after passed in 
    updated(){
        console.log("Component Updated")
    },

    //This run when the compounded is removed after its mounted 
    unmounted(){
        console.log("unmounted")
    },
    methods:{
        startTimer(){
            //increment reactionTime each 10ms by 10
            this.timer = setInterval(() =>{
                this.reactionTime += 10
            }, 10)

        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }

}
</script>

<style>
    .block{
        cursor: pointer;
        width:600px;
        background:#0faf87;
        text-align:center;
        padding:150px 0 ;
        margin:40px auto;
        border-radius:20px;
        color: rgba(0, 0, 0, 0.685);
        font-weight:bold;
        font-size: 1.5rem;
        letter-spacing:2px
    }

</style>