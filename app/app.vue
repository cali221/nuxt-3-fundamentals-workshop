<script>
import { defineNuxtComponent } from '#app'

export default defineNuxtComponent({
  data: () => ({
    todoList: []
  }),
  methods: {
    fetchToDoList(){
      fetch('https://jsonplaceholder.typicode.com/todos')
        .then(response => response.json())
        .then(json => {
          this.todoList = json
        })
    }
  }

})
</script>

<template>
  <div>
    <img src="/todo.jpg" alt="Todo photo by Glenn Casterns-Peters" />
    <p>
      Photo by Photo by <a href="https://unsplash.com/@glenncarstenspeters?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Glenn Carstens-Peters</a> on <a href="https://unsplash.com/photos/person-writing-bucket-list-on-book-RLw-UC03Gwc?utm_content=creditCopyText&utm_medium=referral&utm_source=unsplash">Unsplash</a>
    </p>
    <h1>Hello world!</h1>
    <button @click="fetchToDoList">Fetch Data</button>

    <ul>
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed"> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>
