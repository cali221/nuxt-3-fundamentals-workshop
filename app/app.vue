<script>
import {defineNuxtComponent} from "#app"

export default defineNuxtComponent({
  data: () => ({
    photoGallery: []
  }),
  methods: {
    fetchPhotoGallery(){
      fetch('https://jsonplaceholder.typicode.com/photos') 
        .then(response => {
          this.photoGallery = response.json()
        })
    }
  }
})
</script>

<template>
  <h1>Photo Gallery</h1>
  <button @click="fetchPhotoGallery">Ftech Data</button>
  <ul>
    <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
      <img :src="photo-url" />
    </li>
  </ul>
</template>

<style></style>
<Script