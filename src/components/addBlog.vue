<template>
  <div id="add-blog">
    <h2> Add a New Blog Post </h2>
    <form v-if="!submitted">
        <label>Blog title: </label>
        <input type="text" required v-model.lazy="blog.title">
        <label>Blog Content: </label>
        <textarea v-model="blog.content"></textarea>
        <div id="checkboxes">
          <label>Programming</label>
          <input type="checkbox" value="Programming" v-model="blog.categories">
          <label>Web Programming</label>
          <input type="checkbox" value="Web Programming" v-model="blog.categories">
          <label>Databases</label>
          <input type="checkbox" value="Databases" v-model="blog.categories">
          <label>Networking</label>
          <input type="checkbox" value="Networking" v-model="blog.categories">
        </div>
        <div id="forSelect">
          <label>Author: </label>
          <select v-model="blog.author">
            <option v-for="author in authors" v-bind:key="author"> {{author}} </option>
          </select>
        </div>
        <!-- <input type="submit" value="Add Blog" v-on:click.prevent="post"> -->
        <button v-on:click.prevent="post">Add Blog</button>
    </form>
    <div v-if="submitted">
      <h3>Thank you for post</h3>
    </div>
    <div id="preview">
        <h3>Preview Blog</h3>
        <p>Blog title: {{ blog.title }}</p>
        <p>Categories: </p>
        <p>Author: {{ blog.author }}</p>
        <ul>
          <li v-for="cg in blog.categories" v-bind:key="cg"> {{ cg }} </li>
        </ul>
        <p>Blog content: </p>
        <p>{{ blog.content }}</p>
    </div>
  </div>
</template>

<script>

  export default {  
    data () {
      return {
          blog: {
            title: "",
            content: "",
            categories: [],
            author: "",
          },
          authors: [
            "Admin",
            "Webadmin",
            "Bobur",
          ],
          submitted: false,
      }
    },
    // methods: {
    //   post: function(){
    //     this.$http.post('http://jsonplaceholder.typicode.com/posts', {
    //       title: this.blog.title,
    //       body: this.blog.content,
    //       userId: 1,
    //     }).then(function(data){
    //         console.log(data);
    //         this.submitted = true;
    //     });
    //   }
    // },
    methods: {
      post: function(){
        this.$http.post('https://vue01myblog.firebaseio.com/posts.json', this.blog).then(function(data){
            console.log(data);
            this.submitted = true;
        });
      }
    },
  }
</script>


<style>
#add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
input[type="submit"]{
    background-color: #2BA940;
    color: white;
    padding: 8px;
    border-color: #2BA940;
    margin: 10px 0;
    box-shadow: 1px 1px 12px #2BA940;
    border-radius: 5px;
    cursor: pointer;
}
textarea{
    height: 150px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input{
  display: inline-block;
  margin-right: 10px;
}
#checkboxes label{
  display: inline-block;
}
#forSelect *{
  display: inline-block;
  padding: 5px;
}
</style>
