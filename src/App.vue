<template>
  <h1>Reaction Timmer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
    <Results v-if="showResult" :score="score"/>
</template>

<script>
import Block from './components/block.vue'
import Results from './components/result.vue'
export default {
  name: 'App',
  data(){
    return {
      isPlaying:false,
      delay:null,
      score:null,
      showResult:false
    }
  },
  components: {
    Block,Results
},
  methods:{
    start(){
      this.delay = 2000+Math.random()*5000
      this.isPlaying = true
      this.showResult =false
    },
    endGame(reactionTime){
      this.score = reactionTime/1000
      this.isPlaying =false
      this.showResult=true
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
  color: #2c3e50;
  margin-top: 60px;
}
button{
  background-color: rgb(31, 138, 102);
  color: white;
  width: 60px;
  height: 40px;
  border-radius: 20px;
  cursor: pointer;
  border: none;
}
button[disabled]{
  opacity: .2;
  cursor: not-allowed;
}
</style>
