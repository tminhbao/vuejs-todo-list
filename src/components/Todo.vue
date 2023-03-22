<template>
  <div>
    <AddTodo @add-todo="addTodo" />
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todoProps="todo"
      @item-completed="markCompleted"
      @item-deleted="deleteTodo"
    />
  </div>
</template>

<script>
import { ref } from "vue";
import axios from "axios";
import TodoItem from "./TodoItem.vue";
import AddTodo from "./AddTodo.vue";
export default {
  name: "Todo",
  components: { TodoItem, AddTodo },
  setup() {
    const todos = ref([]);

    const getAllTodos = async () => {
      try {
        const res = await axios.get(
          "https://jsonplaceholder.typicode.com/todos?_limit=5"
        );
        todos.value = res.data;
      } catch (error) {
        console.log(error);
      }
    };

    getAllTodos();

    const markCompleted = (id) => {
      todos.value = todos.value.map((todo) => {
        if (todo.id === id) todo.completed = !todo.completed;
        return todo;
      });
    };

    const deleteTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };

    const addTodo = (newTodo) => {
      todos.value.push(newTodo);
    };

    return {
      todos,
      markCompleted,
      deleteTodo,
      addTodo,
    };
  },
};
</script>

<style></style>
