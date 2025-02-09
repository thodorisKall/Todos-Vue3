<script setup>
import { ref } from "vue"
import { X } from "lucide-vue-next"

const todos = ref([])
const newTodo = ref("")

const addTodo = () => {
  if (newTodo.value.trim() !== "") {
    todos.value.push(newTodo.value)
    newTodo.value = ""
  }
}

const deleteTodo = (i) => {
  todos.value = todos.value.filter((todo, index) => index != i)
}

const deleteAll = () => {
  todos.value = []
}
</script>

<template>
  <div class="todo">
    <header>
      <h1>My Todos</h1>
    </header>
    <main>
      <section class="todo_input">
        <input
          placeholder="new todo"
          @keyup.enter="addTodo"
          v-model="newTodo"
        />
        <button @click="addTodo">Add</button>
      </section>
      <section class="todo_list">
        <ul>
          <li v-for="(todo, index) in todos" :key="index">
            {{ todo }}<button @click="deleteTodo(index)"><X /></button>
          </li>
        </ul>
      </section>
      <button id="todo_delete" v-if="todos.length > 1" @click="deleteAll">
        Delete All
      </button>
    </main>
  </div>
</template>
