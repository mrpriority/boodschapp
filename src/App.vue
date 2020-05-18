<template>
  <div id="app">
    <Header />
    <AddItem v-on:add-item="addItem"/>
    <items v-bind:items="Items" v-on:delItem="deleteItem" v-on:plusAmount="plusAmount" v-on:minAmount="minAmount" v-on:markComplete="markComplete" v-on:plusIndex="plusIndex" v-on:minIndex="minIndex"> </items>
  </div>
</template>

<script>
import items from './components/items';
import AddItem from './components/AddItem';
import Header from './components/Layout/Header'

export default {
  name: 'App',
  components: {
    items,
    Header,
    AddItem
  },
  data() {
    return {
      Items: [
        {
          id:1,
          title:'Appels',
          completed: false,
          amount: 2
        },
        {
          id:2,
          title:'Peren',
          completed: false,
          amount: 4
        },
        {
          id:3,
          title:'Nutella',
          completed: false,
          amount: 1
        }
      ]
    }

    },
  methods: {
    deleteItem(id){
      this.Items = this.Items.filter(item => item.id !== id);
    },
    addItem(newItem){
      this.Items = [...this.Items, newItem];
    },
    plusAmount(id){
      this.Items.find(item => item.id == id).amount += 1;
    },
    minAmount(id){
      if(this.Items.find(item => item.id == id).amount > 0) {
        this.Items.find(item => item.id == id).amount -= 1;
      }
    },
    markComplete(id){
      const arrayMove = require('array-move');
      let itemIndex = this.Items.indexOf(this.Items.find(item => item.id == id));
      if(this.Items[itemIndex].completed == true){
      this.Items = arrayMove(this.Items,itemIndex ,-1);
      } else {
        this.Items = arrayMove(this.Items,itemIndex ,0);
      }
    },
    plusIndex(id){
     const arrayMove = require('array-move');
     let itemIndex = this.Items.indexOf(this.Items.find(item => item.id == id));
      if(itemIndex > 0){
        this.Items = arrayMove(this.Items, itemIndex ,itemIndex -1);
      }
    },
    minIndex(id){
      const arrayMove = require('array-move');
      let itemIndex = this.Items.indexOf(this.Items.find(item => item.id == id));
      if(itemIndex < this.Items.length){
        this.Items = arrayMove(this.Items, itemIndex ,itemIndex +1);
      }
    }
  }
}
</script>

<style>
 *{
   box-sizing: border-box;
   margin: 0;
   padding: 0;
 }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
       }

</style>
