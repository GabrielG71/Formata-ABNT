<template>
  <div class="container">
    <h1>Editor TinyMCE com Vue 3 + Vite</h1>
    <Editor
      v-model="content"
      :init="{
        height: 500,
        menubar: false,
        plugins: 'link image code table lists',
        toolbar:
          'undo redo | formatselect | bold italic | alignleft aligncenter alignright | bullist numlist | link image | code',
      }"
    />
    <h2>Conteúdo:</h2>
    <div v-html="content" class="output"></div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Editor from '@tinymce/tinymce-vue'

const content = ref('<p>Escreva algo aqui...</p>')
</script>

<style>
.container {
  max-width: 800px;
  margin: 2rem auto;
  padding: 1rem;
  font-family: Arial, sans-serif;
}
.output {
  border: 1px solid #ccc;
  padding: 1rem;
  margin-top: 1rem;
  background: #f9f9f9;
}
</style>