<template>
  <div class="flex -center">
    <form v-on:submit.prevent="onAddTodo">
      <input type="text" v-model="todoText" v-on:change="getValue" /><input
        type="submit"
        value="+"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      todoText: "",
    };
  },
  methods: {
    onAddTodo() {
      console.log("===",this.todoText);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>
