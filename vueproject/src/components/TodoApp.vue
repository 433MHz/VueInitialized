<template>
<div>
  <div class="item">
    <h3>{{newItem}}</h3>
    <input type="text" placeholder="ToDo" v-model="newItem">
    <button v-on:click='addItem()'>Dodaj</button>
  </div>

  <div 
  v-for="item in items" 
  v-bind:key='item.id'
  v-bind:class='{completed: item.completed === true}'
  >
    <h2 class="item">{{item.title}}</h2>
    <button 
    v-on:click='removeItem(item.id)'
    v-if="item.completed === false"
    >Zrobione</button>
  </div>

</div>
</template>

<script>

export default {
  data(){
    return{
      newItem: 'default',
    items: [
      {id: 1, title: 'Zrobić zakupy', completed: false},
      {id: 2, title: 'Kupić świece', completed: true}
    ]
    }
  },

  methods:{
    
    addItem(){
      this.items.push({
        title: this.newItem,
        completed: false,
        id: Math.random() 
      }),
      this.newItem = ''
    },


    removeItem(id){
      var index =  this.items.findIndex(item => item.id === id)
      this.items[index].completed = true
    }
  }
}
</script>

<style>

body{
  text-align: center;
}

.item{
  border: 1px solid black;
  padding: 5px;
  margin: 5px;
}

.completed{
  opacity: 0.5;
}

.completed h2{
  text-decoration: line-through;
}
</style>