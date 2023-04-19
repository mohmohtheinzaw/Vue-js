<template>
  <div class="container">
  <h1>How fast can u catch me?</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
      <BlockComponent :delay="delay" />
  </div>
  </div>
</template>
<script>
import BlockComponent from "./components/BlockComponent.vue"
export default {
  name:'App',
  data(){
    return {
      isPlaying :false,
      delay:null,
    }
  },

  //Register component
  components:{
    BlockComponent
  },
  methods:{
   start(){
    this.isPlaying= true;
    this.delay =2000+Math.random()*5000
   }
  }
}
</script>

<style scoped>

</style>