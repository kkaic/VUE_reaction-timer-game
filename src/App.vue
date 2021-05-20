<template>
<h1>Reaction Timer</h1>
<h2>測試你的反應速度</h2>
<p>點選“開始遊戲”後，請於綠色按鈕出現時點選它。</p>
<button @click="start" :disabled="isPlaying">開始遊戲</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<!-- <p v-if="showResults">你的反應時間是：{{ score }}  秒</p> -->
<Results v-if="showResults" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: { Block , Results},
  data(){
      return{
      isPlaying: false,
      delay: null,      
      score: null,
      showResults: false
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      // console.log(this.delay)
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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
</style>
