<template>
  <div id="show-blogs">
    <h1>博客总览</h1>
    <input type="text" placeholder="搜索" v-model="search">
    <div v-for="blog in filteredBlogs" class="single-blogs">
        <h1 v-rainbow>{{blog.title | to-uppercase}}</h1>
        <article>{{blog.body | snippet}}</article>
    </div>
  </div>
</template>

<script>

export default {
  name: "show-blogs",
  data() {
      return {
          blogs: [],
          search: ""
      }
  },
  created() {
      this.$http.get("http://jsonplaceholder.typicode.com/posts").then(data => {
        this.blogs= data.body;
          console.log(this.blogs);
      })
  },
  computed: {
      filteredBlogs: function() {
          return this.blogs.filter(blog => {
              return blog.title.match(this.search);
          })
      }
  },
  // 自定义过滤器
  filters: {
      toUppercase(value) {
          return value.toUpperCase();
      },
      snippet(value) {
          return value.slice(0, 200) + "....";
      }
  },
  // 自定义指令
  directives: {
      "rainbow": {
          bind(el, binding, vnode) {
              el.style.color = "#" + Math.random().toString(16).slice(2,8);
          }
      }
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
