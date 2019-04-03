<template>
  <div class='todos'>
    <v-layout wrap>
      <v-flex xs4
        v-for="todo in todos"
        v-bind:key='todo.id'
        mb-2>
        <v-card>
          <TodoItem v-bind:todo='todo' v-on:del-todo="$emit('del-todo', todo.id)"/>
        </v-card>
      </v-flex>
    </v-layout>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ['todos']
}
</script>

<style scoped>

</style>
