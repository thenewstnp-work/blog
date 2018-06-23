<template>
  <div id="app">
    <!-- <show-blogs></show-blogs> -->
    <!-- <add-blog></add-blog> -->
    <blog-header></blog-header>
    <router-view></router-view>
  </div>
</template>

<script>
import AddBlog from "./components/AddBlog";
import ShowBlogs from "./components/ShowBlogs";
import BlogHeader from "./components/BlogHeader";
import SingleBlog from "./components/SingleBlog";

export default {
  name: "App",
  components: {
    AddBlog,ShowBlogs,BlogHeader
  }
};
</script>

<style>
.clear:after {
  content: "";
  display: block;
  clear: both;
  height: 0;
  overflow: hidden;
  visibility: hidden;
}
.clear {
  zoom: 1;
}
</style>
