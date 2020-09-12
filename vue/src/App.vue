<template>
  <div id="app">
     <!-- <show-blogs></show-blogs> -->
     <!-- <add-blog></add-blog> -->
     <blog-header></blog-header>   
     <router-view></router-view>    
  </div>
</template>

<script>

import AddBlog from './components/AddBlog'

import ShowBlogs from './components/ShowBlogs'
import BlogHeader from './components/BlogHeader'

export default {
  name: 'app',
  components: {
    AddBlog,ShowBlogs,BlogHeader
  }
}
</script>

<style>



</style>
