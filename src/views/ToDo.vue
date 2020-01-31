<template>
  <div class="todo-app">
    <h1>This is an about page</h1>
    <b-field-input
      type="text"
      class="add-field"
      v-model="newTodo"
      @keyup.enter="addItem"
    />
    <button class="add-btn" @click="addItem">Add</button>
    <hr />
    <div class="todoBody">
      <h3 v-if="isEmpty">Your to do list is empty. Please, add some items</h3>
      <div class="todoList" v-else>
        <div v-for="(todo, index) in todoList" :key="index">
          <div>
            <p v-if="!todo.isEdit" @click="onEdit(todo)">{{ todo.text }}</p>
            <div class="editItem" v-else>
              <input
                type="text"
                v-model="todo.text"
                @keyup.enter="doneEdit(todo)"
                @blur="doneEdit(todo)"
                v-focus
              />
            </div>
          </div>
          <div class="remove-item" @click="deleteItem(index)">&times;</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isEmpty: true,
      initialText: "",
      newTodo: "",
      todoList: []
    };
  },
  directives: {
    focus: {
      inserted: function(el) {
        el.focus();
      }
    }
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
    },
    onEdit(todo) {
      this.initialText = todo.text;
      todo.isEdit = true;
    },
    doneEdit(todo) {
      if (todo.text.trim().length == "") {
        todo.text = this.initialText;
      }
      todo.isEdit = false;
    },
    deleteItem(index) {
      this.todoList.splice(index, 1);
    }
  }
};
</script>

<style lang="scss">
.todo-app {
  .add-field {
  }
}
.remove-item {
  &:hover {
    cursor: pointer;
  }
}
</style>
