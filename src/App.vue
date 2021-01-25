<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
  <!-- banana -->
  <Header />
  <div class="container">
    <TodoList :todos="todos" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import Header from "./components/Header.vue";
import TodoList from "./components/TodoList.vue";
import { ITodo } from "./models/todo";

@Options({
  components: {
    Header,
    TodoList,
  },
})
export default class App extends Vue {
  todos: ITodo[] = JSON.parse(localStorage.getItem("todos") || "[]");

  updateTodo = (todo: ITodo) => {
    const index = this.todos.findIndex((t) => t.id === todo.id);

    this.todos[index] = todo;

    this.saveTodos();
  };

  removeTodo = (todo: ITodo) => {
    const index = this.todos.findIndex((t) => t.id === todo.id);

    this.todos.splice(index);

    this.saveTodos();
  };

  addTodo = (todo: ITodo) => {
    this.todos.push(todo);
    this.saveTodos();
  };

  private saveTodos = () => {
    localStorage.setItem("todos", JSON.stringify(this.todos));
  };
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: gray;
}

body,
h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0;
}

button {
  border-radius: 5px;
  border: none;
  box-shadow: 0 0 5px black;
  margin: 5px;
}

.container {
  width: 75%;
  margin: 0 auto;
}
</style>
