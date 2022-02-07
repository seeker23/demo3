<template>
  <div>
    <section class="todoapp">
      <todos-input :title="title" @createTodo="createTodoHandler" />
      <!-- This section should be hidden by default and shown when there are todos -->
      <todos-list :todos="todos" @deleteTodo="deleteTodoHandler" />

      <!-- This footer should hidden by default and shown when there are todos -->
      <footer class="footer">
        <!-- This should be `0 items left` by default -->
        <span class="todo-count"> <strong>0</strong> item left </span>
        <!-- Remove this if you don't implement routing -->
        <ul class="filters">
          <li>
            <a class="selected" href="#/">All</a>
          </li>
          <li>
            <a href="#/active">Active</a>
          </li>
          <li>
            <a href="#/completed">Completed</a>
          </li>
        </ul>
        <!-- Hidden if no completed items are left ↓ -->
        <button class="clear-completed">Clear completed</button>
      </footer>
    </section>
    <footer class="info">
      <p>Double-click to edit a todo</p>
      <!-- Remove the below line ↓ -->
      <p>
        Template by
        <a href="http://sindresorhus.com">Sindre Sorhus</a>
      </p>
      <!-- Change this out with your name and url ↓ -->
      <p>
        Created by
        <a href="http://todomvc.com">you</a>
      </p>
      <p>
        Part of
        <a href="http://todomvc.com">TodoMVC</a>
      </p>
    </footer>
  </div>
</template>

<script>
import TodosInput from "./components/TodosInput";
import TodosList from "./components/TodosList";

export default {
  name: "App",
  components: {
    TodosInput,
    TodosList,
  },
  methods: {
    createTodoHandler(todoTitle) {
      console.log("from app " + todoTitle);
      if (todoTitle) {
        console.log("in if " + todoTitle);
        this.todos.push({
          id: this.todos.length + 1,
          title: todoTitle,
          isCompleted: false,
        });
        console.log(this.todos);
      }
    },
    deleteTodoHandler(todo) {
      this.todos.splice(this.todos.indexOf(todo), 1);
    },
  },
  data() {
    return {
      title: "Adrian TodoList",
      todos: [
        { id: 1, title: "Taste JavaScript", isCompleted: true },
        { id: 2, title: "Buy a unicorn", isCompleted: false },
        { id: 3, title: "Buy adsadasdas unicorn", isCompleted: false },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
