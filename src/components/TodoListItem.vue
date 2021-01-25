<template>
  <li :class="{ done: todo.done, 'not-done': !todo.done }">
    {{ todo.desc }}
    <button @click="$emit('updateTodo', {...todo, done: !todo.done})">{{!todo.done ? 'Do' : 'Undo'}} Thing</button>
    <button @click="$emit('removeTodo', todo)">Remove</button>
  </li>
</template>

<script lang="ts">
import { ITodo } from "@/models/todo";
import { Options, Vue } from "vue-class-component";

@Options({
  props: {
    todo: {
      id: String,
      desc: String,
      done: Boolean,
    },
  },
  emits: ['updateTodo', 'removeTodo']
})
export default class TodoListItem extends Vue {
  todo!: ITodo;
}
</script>