<template>
  <div v-if="!this.done" class="todo-item">
    <div class="container">
      <p class="title">
        {{ title }}
      </p>
      <p class="checksign" v-on:click="makeDone">&#10004;</p>
      <p class="deletebtn" v-on:click="deleteTodo">X</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.title,
      done: false
    };
  },
  props: ["title"],
  methods: {
    deleteTodo() {
      this.done = !this.done;
    },
    makeDone() {
      //Send up to parrent (App.vue)
      this.$emit("delete-todo", this.id);
    }
  }
};
</script>

<style lang="css" scoped>
.container {
  display: flex;
}
p {
  display: flex;
  background: #eaeaea;
  padding: 8px;
}
p {
  margin: 3px;
}
.title {
  flex-grow: 1;
}
.checksign {
  color: white;
  background-color: rgb(70, 241, 47);
  border-radius: 5px;
}
.deletebtn {
  color: white;
  background-color: rgb(252, 61, 61);
  border-radius: 5px;
}
.checksign:hover,
.deletebtn:hover {
  cursor: pointer;
}
</style>
