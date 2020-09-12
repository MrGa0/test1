<template>
  <div id="show-blogs">
    <h1>博客总览</h1>
    <input type="text" v-model="search" placeholder="搜索">
     <div v-for="blog in filteredBlogs" class="single-blog">
         <router-link v-bind:to="'/blog/' + blog.id">
          <h2 v-rainbow>{{blog.title | to-uppercase}}</h2>
        </router-link>
         <article>
            {{blog.body | snippet}}
         </article>
      </div>
   </div>
</template>

<script>

export default {
  name:'show-blogs',
  data(){
    return {
        blogs:[],
        search:"" 
    }
  },
    created(){
      this.$http.get('https://jsonplaceholder.typicode.com/posts')
      .then(function(data){
        this.blogs = data.body.slice(0,10);
      })
    },
      computed:{
        filteredBlogs:function(){
          return this.blogs.filter((blog) =>{
            return blog.title.match(this.search);
          })
        }
      }
}
</script>

<style>
#showblogs {
  max-width:  800px;
  margin:0 auto;
}
.single-blog {
  padding: 20px;
  margin:20px 0;
  box-sizing: border-box;
  background: #eee;
}

</style>
