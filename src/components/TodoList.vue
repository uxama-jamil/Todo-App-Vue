<template>
  <div class="container">
    <div class="input-add">
      <input v-model="input" placeholder="Add task" />
      <button @click="add()">Add</button>
    </div>
    <List
      :list="todolist"
      @delete-task="deleteTask"
      @toggle-complete="toggleComplete"
    />
  </div>
</template>

<script setup>
import { defineEmits, ref } from "vue";
import List from "./List.vue";
const todolist = ref([]);
const input = ref();
function add() {
  if (input.value) {
    console.log("innn", todolist);
    todolist.value.push({ task: input.value, completed: false });
  }
}
function deleteTask(e) {
  todolist.value.splice(e, 1);
}
function toggleComplete(e) {
  if (todolist.value.length > 0)
    todolist.value[e].completed = !todolist.value[e]?.completed;
}
const emits = defineEmits(["delete-task", "toggle-complete"]);
</script>

<style>
.container {
  width: 50%;
  display: flex;
  flex-direction: column;
  gap: 10px;
  border: 1px solid black;
  padding: 10px;
}
input {
  padding: 10px;
  border: 1px dashed grey;
}

.input-add {
  display: flex;
  gap: 10px;
}
button {
  border: 1px dashed black;
  padding: 10px 10px;
  background-color: transparent;
}
button:hover,
input:hover,
input:active {
  border-style: solid;
}
.input-add input {
  width: 100%;
}
</style>
