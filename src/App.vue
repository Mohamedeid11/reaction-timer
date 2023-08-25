<template>
  <h1>Mohamed Reaction Timer</h1>

  <button @click="start" :disabled="isPlaying"> Play </button>
  
  <Block v-if="isPlaying"  :delay="delay" @end="stop" />

  <Result v-if="score != null" :result="score"/>

</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: { Block , Result },

  data(){
    return {
      isPlaying : false,
      delay : null,
      score : null
    }
  },

  methods : {

    start() {
      console.log('you started the game')
      this.isPlaying = true
      this.delay = 2000 + Math.random() * 5000
      this.score = null
    },
    
    stop (reactionTime){
      console.log('score' , reactionTime)
      this.score = reactionTime
      this.isPlaying = false
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
</style>
