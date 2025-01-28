<script setup>

import BlogEditor from "@/components/BlogEditor.vue";
import Blogs from "@/components/Blogs.vue";
import {useBlogs} from "@/composable/useBlogs.js";
import {ref} from "vue";

const {blogs,isLoading,error,addItem,deleteItem}=useBlogs();
const showEditor=ref(false);
</script>

<template>
  <div>
    <button @click="showEditor = !showEditor" v-if="!showEditor">Add new blog</button>
    <BlogEditor v-else @addNewItem="addItem"/>
    <Blogs :blogs="blogs" :is-loading="isLoading" :error="error" @deleteBlog="deleteItem"/>
  </div>
</template>

<style scoped>
  *{
    text-align: center;
    margin: 60px auto 0;
    max-width: 800px;
  }
  input {
    padding: 6px;
  }
</style>