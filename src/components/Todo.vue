<template>
  <div  class="todo-div">
    <div v-bind:key="todo.id" v-for="todo in todos" style="width: 100%">
      <TodoItem
        v-bind:todoitem="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
        v-on:update-todo="$emit('update-todo', todo)"
        v-on:updated="$emit('updated', updateTodo);"
        v-bind:updateTodo="updateTodo"

      />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "Todo",
  props: ["todos","updateTodo"],
  components: {
    TodoItem,
  },
  data() {
    return {
      todoText: "",
    };
  },
  methods: {
    getValue(e) {
      this.todoText = e.target.value;
    },
   
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.todo-div {
  border: 1px solid;
  width: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  min-height: 50px;
  margin-top: 40px;
}
input {
  margin-top: 10px;
  width: 80%;
  height: 30px;
}
</style>
