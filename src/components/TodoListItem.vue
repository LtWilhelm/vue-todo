<template>
  <li :class="{done: todo.done, 'not-done': !todo.done}">{{todo.desc}}</li>
</template>

<script lang="ts">
import { ITodo } from '@/models/todo';
import {Options, Vue} from 'vue-class-component';

@Options({
  props: {
    todo: {
      id: String,
      desc: String,
      done: Boolean
    }
  }
})
export default class TodoListItem extends Vue{
  todo!: ITodo;
}
</script>