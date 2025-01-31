<script setup>
import { ref } from "vue"

const todos = ref([])
const newTodo = ref("")

const addTodo = () => {
  if (newTodo.value.trim() !== " ") {
    //prevent empty todos
    todos.value.push(newTodo.value)
    newTodo.value = ""
  }
}
const deleteTodo = (i) => {
  todos.value = todos.value.filter((todo, index) => index != i)
}
</script>

<template>
  <header>
    <h1>My Todos</h1>
  </header>
  <main>
    <input placeholder="new todo" @keyup.enter="addTodo" v-model="newTodo" />
    <button @click="addTodo">Add</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}<button @click="deleteTodo(index)">Delete</button>
      </li>
    </ul>
  </main>
</template>
