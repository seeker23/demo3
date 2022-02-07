<template>
  <header class="header">
    <h1>{{ title }}</h1>
    <input
      class="new-todo"
      @keyup.enter="createTodo"
      placeholder="What needs to be done?"
      autofocus
    />
  </header>
</template>
<script>
export default {
  name: "TodosInput",
  props: {
    title: {
      type: String,
    },
  },
  methods: {
    createTodo(ev) {
      this.$emit("createTodo", ev.target.value);
      console.log("from component" + ev.target.value);
      ev.target.value = "";
    },
  },
};
</script>
