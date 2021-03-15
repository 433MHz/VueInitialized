<template>
<div>
    <h1>{{title}}</h1>
    <button v-on:click='showAlert()'> show alert</button>
</div>
</template>

<script>

export default {
  data(){
    return{
      title: 'Hello vue.js'
    }
  },

  methods:{
    showAlert(){
      alert('Method called')
    }
  }
}
</script>

<style>

body{
  text-align: center;
}
</style>