<template>
    <v-card
    title="Posts"
    flat
  >
    <template v-slot:text>
        <v-text-field
          v-model="search"
          label="Search"
          prepend-inner-icon="mdi-magnify"
          variant="outlined"
          hide-details
          single-line
        ></v-text-field>
      </template>

  
    <div v-if="posts">
        <v-data-table :items="posts"     :search="search"></v-data-table>
    
    </div> 
    </v-card>
</template>

<script setup>
import {ref, onMounted} from 'vue'
import getAllPosts from "@/services/getAllPosts"
const  search = ref('')
const {posts, error, load} = getAllPosts()

onMounted(() => {
  load()
});
</script>

<style scoped>

</style>