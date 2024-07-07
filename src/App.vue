<template>
  <div id="app">
    <ImageUpload />
    <CameraApp />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ImageUpload from './components/ImageUpload.vue'
import CameraApp from './components/CameraApp.vue'

export default defineComponent({
  components: {
    ImageUpload,
    CameraApp
  }
})
</script>

<style>
/* Add any global styles if necessary */
</style>
