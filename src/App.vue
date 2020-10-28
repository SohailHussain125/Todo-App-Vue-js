<template>
  <div id="app">
    <div>
      <Header/>
      <AddTodo />
      <Todo
        v-bind:todos="todos"
        v-on:del-todo="deleteTodo"
      />
    </div>
  </div>
</template>

<script>
import Todo from "./components/Todo.vue";
import AddTodo from "./components/AddTodo.vue";
import Header from "./components/layout/Header.vue";


export default {
  name: "App",
  components: {
    Todo,
    AddTodo,
    Header
  },
  data() {
    return {
      todos: [
        { id: 1, title: "todoasdas 1", isCompleted: true },
        {
          id: 2,
          title: "todoasdasd 2",
          isCompleted: false,
        },
        {
          id: 3,
          title: "tododsad 3",
          isCompleted: true,
        },
        {
          id: 4,
          title: "tododsad 4",
          isCompleted: true,
        },
      ],
    };
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    // AddTodo(e) {
    //   this.todos = [
    //     ...this.todos,
    //     { id: this.todos.length + 1, title: e, isCompleted: false },
    //   ];
    // },
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
