<template>
  <div class="flex -center">
    <form @submit="onAddTodo">
      <input
        type="text"
        v-model="todoText"
        name="todoText"
        class="input-style"
      /><input type="submit" value="+" class="submit-style" />
    </form>
  </div>
</template>

<script>
// import uuid from 'uuid/v4'
export default {
  name: "AddTodo",
  data() {
    return {
      todoText: "",
    };
  },
  methods: {
    onAddTodo(e) {
      e.preventDefault();
      const newTodo = {
        // id: uuid(),
        title: this.todoText,
        isCompleted: false,
      };
      console.log("===", newTodo);
      this.$emit("add-todo", newTodo);
      this.todoText = "";
    },
  },
};
</script>

<style lang="scss" scoped>
form {
  display: flex;
  height: 50px;
  .submit-style {
    width: 50px;
    background: #42b983;
    border:none;
    border-radius: 5px;
    color: #fff;
    font-weight: 600;
    font-size: 19px;
  }
  .input-style {
    width: calc(100% - 50px);
  }
}
</style>
