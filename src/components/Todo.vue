<template>
  <div>
    <TodoItem
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:todoProps="todo"
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
    return {
      todos,
    };
  },
};
</script>

<style></style>
