<template>
  <div class="about">
    <h1>This is an about page</h1>
    <input type="text" v-model="newTodo" />
    <button @click="addItem">Add</button>
    <hr />
    <div class="todoBody">
      <h3 v-if="isEmpty">Your to do list is empty. Please, add some items</h3>
      <div class="todoList" v-else>
        <ul v-for="(todo, index) in todoList" :key="index">
          <li>{{ todo.text }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isEmpty: true,
      newTodo: "",
      todoList: []
    };
  },
  methods: {
    addItem() {
      let newItem = new Object();
      newItem.text = this.newTodo;
      newItem.index = new Date();
      newItem.isCompleated = false;
      newItem.isEdit = false;
      this.todoList.push(newItem);
      this.newTodo = "";
      this.isEmpty = false;
    }
  }
};
</script>

<style></style>
