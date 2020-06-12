<template>
  <div>
    <div id="mainApp">
      <!-- 1-usul -->
        <!-- <ul>
          <li>
            <a href="#" v-on:click="component='add-blog'">Add Blog</a> 
          </li>
          <li>
            <a href="#" v-on:click="component='show-blogs'">Show Blogs</a> 
          </li>
          <li>
            <a href="#" v-on:click="component='list-blogs'">List Blogs</a> 
          </li>
        </ul> -->
        <!-- 2-usul -->
        <!-- <show-blogs></show-blogs>
        <list-blogs></list-blogs> -->

        <!-- 3-usul -->
        <app-header></app-header>
        <router-view></router-view>

    </div>
    <component v-bind:is="component"></component>
  </div>
</template>

<script>
  import addBlog from './components/addBlog.vue';
  import showBlogs from './components/showBlogs.vue';
  import listBlogs from './components/listBlogs.vue';
  import header from './components/header.vue';
import singleBlog from './components/singleBlog.vue';

  export default {
    components:{
      'add-blog': addBlog,
      'show-blogs': showBlogs,
      'list-blogs': listBlogs,
      'app-header': header,
      // 'single-blog': singleBlog,
    },  
    data () {
      return {
        // component: 'add-blog',
      }
    },
    methods: {
      
    },
  }
</script>


<style>
body{
  margin: 0;
  padding: 0;
  font-family: 'Nunito SemiBold';
}
/* #mainApp *{
    box-sizing: border-box;
}
#mainApp{
    margin: 20px auto;
    max-width: 500px;
} */
/* ul{
  margin: 0;
  padding: 0;
  list-style-type: none;
}
ul li{
  display: inline-block;
}
li a{
  padding: 5px;
  margin: 5px;
  border: 1px solid #ddd;
  text-decoration: none;
} */
</style>
