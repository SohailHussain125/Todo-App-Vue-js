<template>
  <div class="todo-item">
    <p v-bind:class="{ 'is-completed': todoitem.isCompleted }">
      <input
        type="checkbox"
        v-on:change="markCompleted"
        v-model="todoitem.isCompleted"
      />
      {{ todoitem.title }}
    </p>
    <div class="cross" v-on:click="$emit('del-todo', todoitem.id)">x</div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoitem"],
  methods: {
    markCompleted() {
      this.todoitem.isCompleted = !this.todoitem.isCompleted;
    },
  },
};
</script>
<style scoped>
.todo-item {
  background: cornsilk;
  padding: 5px 20px;
  border-bottom: 1px dotted;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.is-completed {
  text-decoration: line-through;
}
.cross {
  color: #fff;
  background: crimson;
  display: flex;
  align-content: center;
  justify-content: center;
  width: 20px;
  height: 20px;
  border-radius: 50px;
  cursor: pointer;
}
</style>