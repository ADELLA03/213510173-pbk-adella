<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(true)
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <div class="container mx-auto">
    <div class="text-center">
      <form @submit.prevent="addTodo">
        <div class="mb-6">
          <label class="block mb-2 text-lg font-medium text-gray-900 dark:text-white">Tambahkan Kegiatan</label>
          <input type="text"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 p-2 w-1/2 "
            v-model="newTodo">
        </div>
        <button
          class="text-white bg-pink-700 hover:bg-pink-800 focus:outline-none focus:ring-4 focus:ring-pink-300 font-medium rounded-md text-sm px-5 py-2.5 text-center mr-2 mb-2">Tambahkan</button>
      </form>
    </div>
    <ul
      class="w-1/2 mt-4 flex-row mx-auto items-center text-sm font-medium text-gray-900 bg-pink-200 border border-pink-200 bg-opacity-80 rounded-lg">
      <li class="p-2" v-for="todo in filteredTodos" :key="todo.id">
        <div class="items-center flex justify-center">
          
          <input type="checkbox"
            class="w-4 h-4 text-pink-600 bg-gray-100 border-gray-300 rounded focus:ring-pink-500 mr-2"
            v-model="todo.done">
          <button class="mr-2 rounded-lg bg-red-400 hover:bg-red-600" @click="removeTodo(todo)">✖</button>
          <span :class="{ done: todo.done }">{{ todo.text }}</span>
          
        </div>
      </li>
    </ul>
    <div class="text-center">
      <button
        class="mt-4 text-white bg-pink-700 hover:bg-pink-800 focus:outline-none focus:ring-4 focus:ring-pink-300 font-medium rounded-md text-sm px-5 py-2.5 mr-2 mb-2"
        @click="hideCompleted = !hideCompleted">
        {{ hideCompleted ? 'Tampilkan Semua' : 'Tampilkan yang belum selesai' }}
      </button>
    </div>
  </div>
</template>

<style>
.done {
  text-decoration: line-through;
}</style>

