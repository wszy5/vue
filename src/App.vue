<template>
  <div>
    <h1>Lista zadań</h1>
    <ToDoApp/>
  </div>
</template>

<script>
import Todo from './components/toDoApp.vue';

export default {
  components:{
    ToDoApp:Todo
  }
}
</script>