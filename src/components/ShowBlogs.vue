<template>
  <div id="show-blogs">
    <h1>博客总览</h1>
    <div v-for="blog in blogs" class="single-blogs">
        <h1>{{blog.title}}</h1>
        <article>{{blog.body}}</article>
    </div>
  </div>
</template>

<script>

export default {
  name: "show-blogs",
  data() {
      return {
          blogs: []
      }
  },
  created() {
      this.$http.get("http://jsonplaceholder.typicode.com/posts").then(data => {
        this.blogs= data.body;
          console.log(this.blogs);
      })
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#show-blogs{
    max-width: 840px;
    margin: 0 auto;
}
.single-blogs{
    padding: 10px 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
.single-blogs h1{
    font-size: 24px;
    font-weight: 400;
    line-height: 1.4em;
}
</style>
