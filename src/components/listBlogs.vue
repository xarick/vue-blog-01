<template>
  <div v-theme:column="'narrow'" id="list-blogs">
    <h1>List Blogs Titles</h1>
    <input type="text" v-model="search" placeholder="search blogs">
    <!-- <div v-for="blog in blogs" v-bind:key="blog" class="single-blog">
        <h2 v-rainbow>{{ blog.title | to-uppercase }}</h2>
        <p>{{blog.body | snipped }}</p>
    </div> -->
    <div v-for="blog in filteredBlogs" v-bind:key="blog" class="single-blog">
        <h2 v-rainbow>{{ blog.title | to-uppercase }}</h2>
        <!-- <p>{{blog.body | snipped }}</p> -->
    </div>
  </div>
</template>

<script>
import searchMixin from '../mixins/searchMixins';

  export default {
    data () {
      return {
         blogs: [],
         search: '',
      }
    },
    methods: {

    },
    created() {
        this.$http.get('http://jsonplaceholder.typicode.com/posts').then(function(data){
            this.blogs = data.body.slice(0,15);
        });
    },
    computed: {
    //   filteredBlogs: function(){
    //     return this.blogs.filter((blog) => {
    //         return blog.title.match(this.search);
    //     });
    //   }

    },
    filters: {
      // 'to-uppercase': function(value){
      //   return value.toUpperCase();
      // }
      // ikkovi bir xil vazifani bajaradi
      toUppercase(value){
        return value.toUpperCase();
      }
    },
    directives: {
      'rainbow': {
        bind(el, binding, vnode){
          el.style.color = "#" + Math.random().toString().slice(2,8);
        }
      }
    },
    mixins: [
        searchMixin
    ]
  }
</script>

<style>
#list-blogs{
    max-width: 800px;
    margin: 0 auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;

}
input[type="text"]{
    width: 100%;
    padding: 8px;
}
</style>
