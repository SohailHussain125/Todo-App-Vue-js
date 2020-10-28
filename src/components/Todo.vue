<template>
  <div style="margin: auto 0%" class="todo-div">
     <!-- <div class="flex -center">
    <input type="text" v-on:change="getValue" /><button
      v-on:click="$emit('add-todo', todoText)"
    >
      +
    </button>
  </div> -->
    <div v-bind:key="todo.id" v-for="todo in todos" style="width: 100%">
      <TodoItem
        v-bind:todoitem="todo"
        v-on:del-todo="$emit('del-todo', todo.id)"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: "Todo",
  props: ["todos"],
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
    AddTodo() {
      console.log("======", this.todoText);
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
}
input {
  margin-top: 10px;
  width: 80%;
  height: 30px;
}
</style>
