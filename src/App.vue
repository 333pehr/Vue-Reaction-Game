<template>
  <div class="main">
    <h1>Welcome to the Reaction Game</h1>
    <h5>Made by Sepehr Latifi Azad</h5>
    <button @click="start()" :disabled="isStarted" :class="{btnAfter: isStarted}">Start</button>
  </div>
    <BlockVue v-if="isStarted" :delay="delay" @end="endGame"/>
    <ResultVue :score="score" v-if="showResult"/>
</template>

<script>
import BlockVue from './components/Block.vue';
import ResultVue from './components/Result.vue';

export default {
  name: 'App',
  components: {
    BlockVue,
    ResultVue,
  },
  data(){
    return{
      delay: null,
      isStarted: false,
      score: null,
      showResult: false,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + (Math.random()*5000);
      this.isStarted = true;
      this.showResult = false;
    },
    endGame(reactionTimer){
      this.score = reactionTimer;
      this.isStarted = false;
      this.showResult = true;
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
.main h1{
  color: white;
  
}

.main button{
  margin-top: 250px;
  background-color: #00796B;
  padding: 15px 25px;
  border: 3px white solid;
  color: white;
  font-weight: 600;
  font-size: 20px;
  letter-spacing: 1.5px;
  border-radius: 10px;
}
.main button:hover{
  rotate: 5deg;
  transition: 500ms;
}
.btnAfter{
  cursor: no-drop;
}
.main h5{
  color: white;
  opacity: 0.6;
}
</style>
