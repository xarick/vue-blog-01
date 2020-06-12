<template>
    <div id="single-blog">
        <h1>{{ blog.title }}</h1>
        <i>Creator: {{ blog.author }}</i>
        <article>{{ blog.content }}</article>
        <h2>Categories</h2>
        <ul>
            <li v-for="category in blog.categories" v-bind:key="category"> {{ category }}</li>
        </ul>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            id: this.$route.params.id,
            blog: {},
        }
    },
    created() {
        this.$http.get('https://vue01myblog.firebaseio.com/posts/' + this.id + '.json').then(function(data){
            // console.log(data);
            // this.blog = data.body;
            return data.json();
        }).then(function(data){
            this.blog = data;
        });
    },
}
</script>

<style scoped>
#single-blog{
    background: #ddd;
    padding: 10px;
    border-radius: 5px;
    max-width: 960px;
    margin: 0 auto;
}
</style>