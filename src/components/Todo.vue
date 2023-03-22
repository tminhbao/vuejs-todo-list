<template>
  <div>
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
import TodoItem from "./TodoItem.vue";
export default {
  name: "Todo",
  components: { TodoItem },
  setup() {
    const todos = ref([
      {
        id: 1,
        title: "Việc 1",
        completed: false,
      },
      {
        id: 2,
        title: "Việc 2",
        completed: false,
      },
      {
        id: 3,
        title: "Việc 3",
        completed: false,
      },
    ]);

    const markCompleted = (id) => {
      todos.value = todos.value.map((todo) => {
        if (todo.id === id) todo.completed = !todo.completed;
        return todo;
      });
    };

    const deleteTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id !== id);
    };

    return {
      todos,
      markCompleted,
      deleteTodo,
    };
  },
};
</script>

<style></style>
