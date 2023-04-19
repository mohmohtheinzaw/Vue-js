<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{success:theme =='success',danger:theme=='delete'}"> 
        <h2>{{header}}</h2>
        <p>{{content}}</p>
    </div>
  </div>
</template>

<script>

export default {
  //get data from parent component to child component
  props:['header','content','theme'],
  methods:{
    closeModal(){
      //use data emit when we need to change the data of the parent component (from child component)
      this.$emit("close")
    }
  }
}
</script>

<style>
.backdrop{
    position: fixed;
    top:0;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
}
.modal{
    width: 400px;
    padding: 30px;
    margin: 100px auto;
    background-color: white;
    border-radius: 10px;
}
.success{
  background-color: green;
  color: white;
}
.danger{
  background-color: red;
  color: white;
}
</style>