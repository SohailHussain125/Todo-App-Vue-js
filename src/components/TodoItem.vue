<template>
  <div class="todo-item">
    <p
      v-if="updateTodo.id !== todoitem.id"
      v-bind:class="{ 'is-completed': todoitem.isCompleted }"
    >
      <input
        type="checkbox"
        v-on:change="markCompleted"
    
      />
      {{ todoitem.title }}
    </p>
    <div v-else>
      <input type="text" name="update-todo" v-model="TextUpdateTodo" />
    </div>
    <div class="flex">
      <div
        v-if="updateTodo.id !== todoitem.id"
        class="update"
        v-on:click="
          $emit('update-todo', todoitem);
          setValueForUpdate(todoitem.title);
        "
      >
        update
      </div>
      <div v-else class="update" v-on:click="onUpdatedValue">
        Done
      </div>
      <div class="cross" v-on:click="$emit('del-todo', todoitem.id)">x</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoitem", "updateTodo"],
  methods: {
    markCompleted() {
      this.todoitem.isCompleted = !this.todoitem.isCompleted;
    },
    setValueForUpdate(title) {
      this.TextUpdateTodo = title;
    },
    onUpdatedValue() {
      this.updateTodo.title=this.TextUpdateTodo
      this.$emit("updated", this.updateTodo);
    },
  },
  data() {
    return {
      TextUpdateTodo: "",
    };
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
.flex {
  display: flex;
  align-items: center;
}
.update {
  font-size: 13px;
  color: blue;
  font-weight: 600;
  margin-right: 10px;
  cursor: pointer;
}
</style>