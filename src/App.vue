<template>
  <div class="container">
  <h1>How fast can u catch me?</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
      <BlockComponent :delay="delay" @endGame="endGame"/>
  </div>
  <div v-if="end">
      <ResultComponent :score="score"/>
  </div>
  </div>
</template>
<script>
import BlockComponent from "./components/BlockComponent.vue"
import ResultComponent from './components/ResultComponent.vue'
export default {
  name:'App',
  data(){
    return {
      isPlaying :false,
      delay:null,
      score:0,
      end:false
    }
  },

  //Register component
  components:{
    BlockComponent,
    ResultComponent
  },
  methods:{
   start(){
    this.isPlaying= true;
    this.delay =2000+Math.random()*5000
   },
   endGame(score){
    this.score = score;
    this.isPlaying= false;
    this.end = true;
   }
  }
}
</script>

<style scoped>

</style>