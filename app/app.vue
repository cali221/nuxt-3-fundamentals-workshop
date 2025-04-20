<script setup>
import { computed, ref } from 'vue'

let todoList = ref([])

const completedItems = computed(() => {
  return todoList.value.filter(item => item.completed)
}) 

const remainingItems = computed(() => {
  return todoList.value.filter(item => !item.completed)
})

function fetchToDoList() {
  fetch('https://jsonplaceholder.typicode.com/todos')
    .then(response => response.json())
    .then(json => {
      todoList.value = json
    })
}
</script>

<template>
  <div class="section">
    <img src="/todo.jpg" alt="Todo photo by Glenn Casterns-Peters" />
    <p>
      Photo by <a href="https://unsplash.com/@glenncarstenspeters?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Glenn Carstens-Peters</a> on <a href="https://unsplash.com/photos/person-writing-bucket-list-on-book-RLw-UC03Gwc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
    </p>
    <h1 class="title">Hello world!</h1>
    <button @click="fetchToDoList">Fetch Data</button>

    <p>{{ completedItems.length }} completed | {{ remainingItems.length }} remaining</p>

    <ul class="list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed"> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<style lang="scss">
@use './node_modules/bulma/bulma.scss' as *;
@use '@/assets/styles/main.scss' as *;

// If you're not using scoped styles, just use class names directly.
:root {
  --text-color: #{$textColor};  // Ensure `$textColor` is defined in main.scss
}

.heading {
  color: var(--text-color);
}

.list {
  color: var(--text-color);
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
</style>
