<template>
  <p :class="['todo-item-wrapper', todoProps.completed ? 'is-completed' : '']">
    <input type="checkbox" name="" id="" :checked="todoProps.completed" />
    {{ todoProps.title }}
    <button class="del-btn">Delete</button>
  </p>
</template>

<script>
import { ref } from "vue";

export default {
  name: "TodoItem",
  props: ["todoProps"],
  setup() {
    const new_id = ref("my-new-id");
    return {
      new_id,
    };
  },
};
</script>

<style>
.todo-item-wrapper {
  margin: 8px 0;
  background-color: #34568b;
  color: white;
  font-weight: 600;
  max-width: 60vw;
  margin: 4px auto;
  padding: 8px 12px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.del-btn {
  background-color: #d83939;
  border-radius: 8px;
  border-style: none;
  box-sizing: border-box;
  color: #ffffff;
  cursor: pointer;
  display: inline-block;
  font-size: 14px;
  font-weight: 500;
  height: 40px;
  line-height: 20px;
  list-style: none;
  margin: 0;
  outline: none;
  padding: 10px 16px;
  position: relative;
  text-align: center;
  text-decoration: none;
  transition: color 100ms;
  vertical-align: baseline;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}

.del-btn:hover,
.del-btn:focus {
  background-color: #cc2e2e;
}

.is-completed {
  text-decoration: line-through;
}
</style>
