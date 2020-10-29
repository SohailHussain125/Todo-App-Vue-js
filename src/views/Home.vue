<template>
  <div id="app">
    <div style="margin: auto;">
      <!-- <Header /> -->
      <AddTodo v-on:add-todo="onAddTodo" />
      <Todo
        v-bind:todos="todos"
        v-on:del-todo="deleteTodo"
        v-on:update-todo="UpdateTodo"
        v-bind:updateTodo="updateTodo"
        v-on:updated="onUpdated"
      />
    </div>
  </div>
</template>

<script>
import Todo from "../components/Todo.vue";
import AddTodo from "../components/AddTodo.vue";
// import Header from "../components/layout/Header.vue";
import axios from "axios";

export default {
  name: "App",
  components: {
    Todo,
    AddTodo,
    // Header,
  },
  data() {
    return {
      todos: [],
      updateTodo: {},
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then(() => {
          this.todos = this.todos.filter((todo) => todo.id !== id);
        })
        .catch((err) => console.log(err));
    },
    onAddTodo(newTodo) {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", newTodo)
        .then((res) => {
          newTodo.id = res.data.id;
          this.todos = [...this.todos, newTodo];
        })
        .catch((err) => console.log(err));
    },
    UpdateTodo(todo) {
      this.updateTodo = todo;
    },
    onUpdated(updatedTodo) {
      this.todos = this.todos.map((todo) =>
        todo.id === updatedTodo.id ? updatedTodo : todo
      );
      this.updateTodo = {};
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
}
</style>
