<template>
  <div 
    class='todo-item'
    @dblclick="markAsCompleted(todo)"
    v-bind:class="{ 'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change='markAsCompleted(todo)'>
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class='del'>x</button>
    </p>
  </div>
</template>

<script>
  import { mapActions } from "vuex";

  export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
      ...mapActions(['updateTodo']),
      markAsCompleted(todo) {
        const updTodo = {
          id: todo.id,
          title: todo.title,
          completed: !todo.completed
        };
        this.updateTodo(updTodo);
      }
    }
  }
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
  }
</style>
