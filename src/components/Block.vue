<template>
<br>
<br>
  <button class="btn" v-if="showButton" @click="stopTimer()">Click me!</button>
</template>

<script>

export default {
    name: 'Block',
    props: ['delay'],
    data(){
      return{
        showButton: false,
        timer: null,
        reactionTimer: 0,
      }
    },
    mounted(){
      setTimeout(()=>{
        this.showButton = true,
        this.startTimer();
      }, this.delay)
    },
    methods:{
      startTimer(){
        this.timer = setInterval(()=>{
          this.reactionTimer += 10
        }, 10)
      },
      stopTimer(){
        this.$emit('end',this.reactionTimer);
        clearInterval(this.timer);
      }
    }
}
</script>

<style>
.btn{
  text-align: center;
  padding: 50px;
  background-color: #E53935;
  color: white;
  font-size: 20px;
  border-radius: 7px;
  border: 0px;
  cursor: pointer;
  font-weight: 600;
  border: 1px solid white;
}
</style>