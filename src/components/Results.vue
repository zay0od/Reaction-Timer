<template>
    <p class="score">Reaction Time: {{score}} ms</p>
    <p class="rank">{{rank}}</p>

</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank:null
        }
    },
    mounted(){

        if (this.score < 250)
            this.rank = "Ninja Fingers"
        else if (this.score < 400)
            this.rank = "Great"
        else
            this.rank = "umm, Good"

    }
}
</script>

<style>
    .rank{
        color: #0faf87;
        font-size:3rem;
        padding:100px 
    }
    .score{
        margin:30px auto;
        font-weight: bold;
    }
</style>