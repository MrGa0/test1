<template>
	<div id="single-blog">
		<h1>{{blog.title}}</h1>
        <article>{{blog.body}}</article>
	</div>
</template>

<script>
	export default{
       name:"single-blog",
       data(){
       	return{
       		id:this.$route.params.id,
       		blog:{}
       	}
       },

       created(){
       	this.$http.get('https://jsonplaceholder.typicode.com/posts/' + this.id).then(function(data){
       		this.blog = data.body;
       	})
       }
	}
</script>					