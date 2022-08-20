<template>
  <div id="app">
   <Todolist></Todolist>
  </div>
</template>

<script>
import todolist from './components/todolist.vue'
import Todolist from './components/todolist.vue';

export default {
  name: 'App',
  components: {
    todolist,
    Todolist
}
}
</script>
