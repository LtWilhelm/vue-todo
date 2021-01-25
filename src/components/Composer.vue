<template>
  <form @submit="addTodo">
    <div class="form">
      <div>
        <textarea v-model="desc" placeholder="Add Todo..."></textarea>
      </div>
      <div>
        <button>Add Todo</button>
      </div>
    </div>
  </form>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import {v4} from 'uuid';
@Options({
  emits: ["addTodo"],
})
export default class Composer extends Vue {
  desc = "";

  addTodo(e: Event) {
    e.preventDefault();
    const todo = {
      id: v4(),
      desc: this.desc,
      done: false
    }
    this.desc = '';
    this.$emit('addTodo', todo);
  }
}
</script>
<style lang="scss" scoped>
textarea {
  resize: none;
  width: 100%;
  height: 50px;
  background-color: darkgray;
  border: none;
  box-shadow: inset 0 0 10px black;
  border-radius: 10px;
  padding: 10px;
}

.form {
  width: 50%;
}

.form button {
  float: right;
  background-color: #3e0070;
  color: #dcdcdc;
}
</style>