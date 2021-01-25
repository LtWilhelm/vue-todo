<template>
  <Header />
  <div class="container">
    <TodoList :todos="todos" />
    <Composer @addTodo="addTodo" />
  </div>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Provide } from "vue-property-decorator";
import Header from "./components/Header.vue";
import TodoList from "./components/TodoList.vue";
import Composer from "./components/Composer.vue";
import { ITodo } from "./models/todo";
// import { provide } from "vue";

@Options({
  components: {
    Header,
    TodoList,
    Composer,
  },
})
export default class App extends Vue {
  todos: ITodo[] = JSON.parse(localStorage.getItem("todos") || "[]");

  @Provide("updateTodo") private updateTodo = (todo: ITodo) => {
    const index = this.todos.findIndex((t) => t.id === todo.id);

    this.todos[index] = todo;
    this.saveTodos();
  };

  @Provide("removeTodo") private removeTodo = (todo: ITodo) => {
    const index = this.todos.findIndex((t) => t.id === todo.id);

    this.todos.splice(index, 1);

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
