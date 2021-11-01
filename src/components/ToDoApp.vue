<template>
   <div>
     <div class="item">
      <p>Nowe zadanie:</p>
        <input type="text" placeholder="Wpisz nowe zadanie" v-model="newItem">
      <button @click="addItem">Dodaj</button>
     </div>
      <toDoItem v-for="item in items" 
      v-bind:key="item.id"
      v-bind:item="item"
      @removeClicked="removeItem"
      />


    </div>

</template>

<script>
import toDoItem from './toDoItem.vue';
export default {
  components:{
    toDoItem
  },
  data(){
    return{
      newItem:"",
        items:[
          {id:1,title:"Zrobić zakupy", completed:true},
          {id:2,title:"Zrobić obiad", completed:false},
          {id:3,title:"Pozmywać naczynia", completed:false},
          {id:4,title:"Kupić książkę", completed:false},
        ]
      }
  },
  methods:{
        addItem(){
          this.items.push({id:Math.random(0,1),title:this.newItem, completed:false}),
          this.newItem = "";
        },
        removeItem(id){
          const index = this.items.findIndex(el => el.id === id);
          this.items[index].completed = true;
          return 0;
        }
    }
}

</script>

<style scoped>
  .item{
    border: 1px solid grey;
    margin: 8px;
    padding: 10px;
  }
  .completed{
    opacity: 0.5;
    text-decoration: line-through;

  }
  

</style>