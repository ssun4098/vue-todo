<template>
  <todo-header></todo-header>
  <todo-input v-on:addTodo="addTodo"></todo-input>
  <todo-list v-bind:propsdata="todoItems" @removeTodo="removeTodo"></todo-list>
  <todo-footer v-on:removeAll="clearAll"></todo-footer>
</template>

<script>
import todoList from "@/components/TodoList";
import todoInput from "@/components/TodoInput";
import todoHeader from "@/components/TodoHeader";
import todoFooter from "@/components/TodoFooter";

export default {
  name: 'App',
  components: {
    'TodoHeader': todoHeader,
    'TodoFooter': todoFooter,
    'TodoList': todoList,
    'TodoInput': todoInput
  },
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    }
  },
  created() {
    if(localStorage.length > 0) {
      for(let i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  }
}
</script>
<style>
body {
  text-align: center;
  background: #F6F6F8;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
</style>