<template>
  <v-container :fluid="true">
    character
  </v-container>
</template>

<script setup>
  import { ref } from 'vue'
  import { onMounted } from 'vue'

  import axios from 'axios'
  
  let characterData;

  onMounted(() => {
    axios.get("https://api-blue-archive.vercel.app/api/characters?page=1&perPage=500")
      .then(function(response){
        //get
        characterData = response.data.data;
        console.log(characterData);
      }).catch(function(error){
        //error
        console.log(error);
      }).then(function(){
        //always work
      })
  })

  
</script>
