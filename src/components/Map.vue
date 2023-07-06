<template>
    <div class="q-pa-md q-gutter-sm">
  
      <q-img
        src="../assets/map/zentai.jpg"
        spinner-color="white"
        style="height: 800px; max-width: 100%"
  
      />
    </div>
  </template>
  
  <script >
  import { ref } from 'vue'
  
  export default {
    setup () {
      const url = ref('../assets/map/zentai.jpg')
  
      return {    
        url,
        refresh () {
          url.value = 'https://picsum.photos/500/300?t=' + Math.random()
        }
      }
    }
  }
  </script>