<template>
  <div id="app">
    <show-blogs></show-blogs>
    <!-- <add-blog></add-blog> -->
  </div>
</template>

<script>
import AddBlog from "./components/AddBlog";
import ShowBlogs from "./components/ShowBlogs";

export default {
  name: "App",
  components: {
    AddBlog,ShowBlogs
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
