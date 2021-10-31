<template>
  <div>
    <div class="item">
      <p>Nowe zadanie:</p>
        <input type="text" placeholder="Wpisz nowe zadanie" v-model="newItem">
      <button @click="addItem">Dodaj</button>
    </div>
    <div 
    class="item"
    v-for="item in items" 
    v-bind:key="item.id"
    v-bind:class="
    {
      completed:item.completed
    }">

        <h2>{{item.title}}</h2>
        <button v-if=!item.completed @click="removeItem(item.id)">Zrobione</button>
    </div>

  </div>
</template>

<script>

export default {
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
    /* text-align: center; */
  }
  .completed{
    opacity: 0.5;
  }
  .completed h2{
    text-decoration: line-through;
    }

</style>