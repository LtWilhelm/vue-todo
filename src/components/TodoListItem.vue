<template>
  <li :class="{ done: todo.done, 'not-done': !todo.done }">
    {{ todo.desc }}
    <button @click="updateTodo({...todo, done: !todo.done})">{{!todo.done ? 'Do' : 'Undo'}} Thing</button>
    <button @click="removeTodo(todo)">Remove</button>
    <!-- <button @click="$emit('updateTodo', {...todo, done: !todo.done})">{{!todo.done ? 'Do' : 'Undo'}} Thing</button>
    <button @click="$emit('removeTodo', todo)">Remove</button> -->
  </li>
</template>

<script lang="ts">
import { ITodo } from "@/models/todo";
import { Options, Vue } from "vue-class-component";
import {Inject} from 'vue-property-decorator';

@Options({
  props: {
    todo: {
      id: String,
      desc: String,
      done: Boolean,
    },
  },
  // emits: ['updateTodo', 'removeTodo'],
  // inject: ['updateTodo, removeTodo']
})
export default class TodoListItem extends Vue {
  todo!: ITodo;
  @Inject('updateTodo') private updateTodo!: Function;
  @Inject('removeTodo') private removeTodo!: Function;
}
</script>