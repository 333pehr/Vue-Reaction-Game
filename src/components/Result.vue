<template>
  <div class="result">
    <h2>{{score}} ms</h2>
    <h3>{{result}}</h3>
  </div>
</template>

<script>
export default {
    name: 'Result',
    props: ['score'],
    data(){
      return {
        showScore: false,
        result: '',
      }
    },
    mounted(){
      this.finalResult();
    },
    methods: {
      finalResult(){
        if(this.score <= 200){
          this.result = 'What a nice reaction';
        } 
        else if ( 200 < this.score && this.score <= 300){
          this.result = 'Good Reaction'
        } 
        else if ( 300 < this.score && this.score < 500){
          this.result = 'Normal Reaction'
        } 
        else if (500 <= this.score) {
          this.result = 'Just like a little snail'
        }
      },
    }
}
</script>

<style>
.result h3, h2{
  color: white;
  letter-spacing: 1.5px;
}
</style>