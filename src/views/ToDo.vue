<template>
  <b-container class="todo-app">
    <h1>This is an about page</h1>
    <b-input-group>
      <b-form-input
        type="text"
        class="add-field"
        v-model="newTodo"
        @keyup.enter="addItem"
        placeholder="Add something"
      />
      <b-button class="add-btn" @click="addItem">Add</b-button>
    </b-input-group>

    <hr />
    <div class="todoBody">
      <h3 v-if="isEmpty">Your to do list is empty. Please, add some items</h3>
      <div
        class="todoList"
        v-for="(todo, index) in todoList"
        :key="index"
        v-else
      >
        <div class="todoItem" v-if="!todo.isEdit">
          <b-form-checkbox></b-form-checkbox>
          <p @click="onEdit(todo)">{{ todo.text }}</p>
          <div class="remove-item" @click="deleteItem(index)">&times;</div>
        </div>
        <div class="editItem" v-else>
          <input
            type="text"
            v-model="todo.text"
            @keyup.enter="doneEdit(todo)"
            @blur="doneEdit(todo)"
            @keyup.esc="cancelEdit(todo)"
            v-focus
          />
        </div>
      </div>
    </div>
  </b-container>
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
      if (this.newTodo.trim().length == 0) {
        return;
      }
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
    cancelEdit(todo) {
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
  .input-group {
    width: 50%;
    display: flex;
    margin: auto;
  }
  .todoBody {
    .todoList {
      .todoItem {
        width: 30%;
        display: flex;
        flex-direction: row;
        justify-content: flex-start;
        margin: auto;
      }
    }
  }
}
.remove-item {
  &:hover {
    cursor: pointer;
  }
}
</style>
