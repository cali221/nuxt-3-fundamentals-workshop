<script setup>
import { computed, ref } from 'vue'
import PhotoGallery from './components/PhotoGallery.vue'
import ToDoViewer from './components/ToDoViewer.vue'
</script>

<template>
  <div class="container">
    <div class="section">
      <div class="columns">
        <div class="column">
          <ToDoViewer title="This is fun!">
            <template v-slot:metrics="slotProps">
              <strong>{{ slotProps.completed.length }} items completed</strong>
              <h2>Does this really work?</h2>
              <img src="./public/todo.jpg" />
            </template>
            <template v-slot:hero>
              <h3>Hello this works</h3>
            </template>
          </ToDoViewer>
        </div>
        <div class="column">
          <PhotoGallery />
        </div>
      </div>
    </div>
  </div>
</template>


<style lang="scss">
@import './node_modules/bulma/bulma.sass';
@import './assets/styles/main.scss';
.photo-gallery-list{
  display: grid;
  grid-template-columns: repeat(5, 1fr);
}

</style>
