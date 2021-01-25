<template>
  <ul>
    <!-- <li v-for="todo in todos" v-bind:key="todo.id">{{todo.desc}}</li> -->
    <TodoListItem @updateTodo="$emit('updateTodo', $event)" v-for="todo in todos" v-bind:key="todo.id" :todo="todo" />
  </ul>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import TodoListItem from './TodoListItem.vue';
import {ITodo} from '../models/todo';
@Options ({
  props: {
    todos: Array
  },
  components: {
    TodoListItem
  },
  emits: ['updateTodo']
})
export default class TodoList extends Vue {
  todos!: ITodo[]
}
</script>

<style lang="scss" scoped>
ul {
  list-style: none;
  border-left: 1px solid black;
  padding: 0;
  background: linear-gradient(to right, #00000050, #00000000);
}

ul>li:nth-child(odd) {
  background: linear-gradient(to right, #00000050, #00000000, #00000000);
}

li {
  padding: 0 5px;
}

.not-done {
  color: red;
}

.done {
  color: green;
}
</style>