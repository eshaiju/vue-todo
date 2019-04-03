<template>
  <div id="app">
    <AddTodo />
    <Todos v-bind:todos="allTodos" v-on:del-todo="this.deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos'
import AddTodo from '../components/AddTodo'
import { mapGetters, mapActions } from "vuex";

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return{
      todos: []
    }
  },
  computed: mapGetters(['allTodos']),
  methods: {
    ...mapActions(['fetchTodos', 'deleteTodo']),
  },
  created() {
    this.fetchTodos();
  }
}
</script>

<style>
</style>
