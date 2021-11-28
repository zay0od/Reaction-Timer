<template>
  <h1>Zayed Reaction Timer </h1>
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score: null,
      showResult:false
    }
  },  
  methods:{
    start(){
      //2 to 7sec delay before showing the block
      this.delay = 2000 + Math.random()*5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;

}
h1{
  font-size: 3.2rem;
}
button{
  padding: 12px 45px;
  font-size: .98rem;
  border-radius:9px;
  background:#0faf87;
  font-weight: bold;
  letter-spacing: 3px;

}
</style>
