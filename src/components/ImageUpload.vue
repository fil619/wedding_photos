<template>
  <div>
    <input type="file" @change="onFileChange" />
    <button @click="uploadFile">Upload</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import { supabase } from '../supabaseClient'

export default defineComponent({
  setup() {
    const file = ref<File | null>(null)

    const onFileChange = (event: Event) => {
      const target = event.target as HTMLInputElement
      if (target.files && target.files.length > 0) {
        file.value = target.files[0]
      }
    }

    const uploadFile = async () => {
      if (file.value) {
        const { data, error } = await supabase
          .storage
          .from('wedding-images')
          .upload(`images/${file.value.name}`, file.value)

        if (error) {
          console.error('Error uploading file:', error)
        } else {
          console.log('File uploaded successfully:', data)
        }
      }
    }

    return { onFileChange, uploadFile }
  }
})
</script>

<style scoped>
/* Add any styles if necessary */
</style>
