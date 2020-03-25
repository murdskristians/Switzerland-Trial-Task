<template>
  <div id="app">
    <h1>To do:</h1>

    <div v-for="todo in todos" :key="todo">
      <Todo @delete-todo="deleteTodo" :title="todo" />
    </div>

    <AddTodo @add-todo="addTodo" />

    <h1>Done:</h1>
    <div v-for="doneTodo in doneTodos" :key="doneTodo">
      <Todo :title="doneTodo" />
    </div>
  </div>
</template>

<script>
import AddTodo from "./components/AddTodo.vue";
import Todo from "./components/Todo.vue";

export default {
  name: "App",
  data() {
    return {
      todos: ["Wake up", "Eat brackfast", "Go to work"],
      doneTodos: []
    };
  },
  methods: {
    addTodo(object) {
      this.todos.push(object.title);
    },
    deleteTodo(value) {
      console.log(value);

      for (let i = this.todos.length - 1; i >= 0; i--) {
        if (this.todos[i] === value) {

          this.doneTodos.push(value);
          this.todos.splice(i, 1);
        }
      }
    }
  },

  components: {
    AddTodo,
    Todo
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');

#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  padding: 20px;
}
h1 {
  display: flex;
}
</style>
