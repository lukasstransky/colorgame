<template>
  <div id="app">
    <Start :currentHighscore="highscore" v-on:startGame="currentStep = 1" v-if="currentStep == 0"/>
    <ColorGame v-if="currentStep == 1" v-on:gameFinished="played"/>
    <Finish v-if="currentStep == 2" :isHighscore="isHighscore" :score="lastScore" v-on:backToStart="currentStep = 0"/>
  </div>
</template>

<script>
import Start from './components/Start.vue'
import ColorGame from './components/ColorGame'
import Finish from './components/Finish'

export default {
  name: 'app',
  components: {
    Start,
    ColorGame,
    Finish
  },
  methods: {  
    played(ev){ //ev = last score
      this.currentStep = 2
      this.lastScore = ev
      if(ev > this.highscore){
        this.highscore = ev
        this.isHighscore = true
      }
      else{
        this.isHighscore = false;
      }
    }
  },
  data:() => ({
    currentStep: 0,
    highscore: 0,
    lastScore: 0,
    isHighscore: false
  })
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
