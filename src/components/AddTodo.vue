<template>
  <div class="addTodoField">
    <form @submit="addTodo">
      <div class="container">
        <h4>Task</h4>
        <input
          class="text"
          type="text"
          v-model="title"
          name="title"
          placeholder="What do you need to do?"
        />
      </div>

      <input type="submit" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      //Prevents default submision to file so we can emit
      e.preventDefault();

      if (this.title == "") return;

      const newTodo = {
        title: this.title,
        completed: false
      };
      //Send up to parrent (App.vue)
      this.$emit("add-todo", newTodo);
      this.title = "";
    }
  }
};
</script>

<style>
form {
  display: block;
}
input[type="text"] {
  padding: 5px;
}
.container {
  display: flex;
}
h4 {
  width: 20%;
}
.btn {
  position: relative;
  top: 30px;
  right: -45%;

  background-color: rgb(94, 104, 245); /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  border-radius: 10px;
}
.text {
  width: 80%;
  border-radius: 10px;
}
.addTodoField {
    margin-top: 50px;
}
</style>
