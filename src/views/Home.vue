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
    this.fetchTodos()
  }
}
</script>

<style>
  * {
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
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
