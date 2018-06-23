<template>
  <div id="add-blog">
    <h2>添加博客</h2>
    <form v-if="!submmited">
        <label for="">博客标题</label>
        <input type="text" v-model="blog.title" required>
        <label for="">博客内容</label>
        <textarea v-model="blog.content"></textarea>
        <div id="checkboxes">
            <label for="">Vue.js</label>
            <input type="checkbox" value="Vue.js" v-model="blog.categories">
            <label for="">Node.js</label>
            <input type="checkbox" value="Node.js" v-model="blog.categories">
            <label for="">Aagular</label>
            <input type="checkbox" value="Aagular" v-model="blog.categories">
            <label for="">React.js</label>
            <input type="checkbox" value="React.js" v-model="blog.categories">
        </div>
        <label class="authors" for="">作者</label>
        <select v-model="blog.author">
            <option v-for="author in authors">
                {{author}}
            </option>
        </select>
        <button v-on:click.prevent="post">添加博客</button>
    </form>

    <div v-if="submmited">
        <h3>您的博客发布成功!</h3>
    </div>

    <div class="preview">
        <h3>博客总览</h3>
        <h1 class="title">博客标题：{{blog.title}}</h1>
        <p>博客内容：</p>
        <p class="content">{{blog.content}}</p>
        <h4>博客分类:</h4>
        <ul class="clear">
            <li v-for="categorie in blog.categories">
                <span>{{categorie}}</span>
            </li>
        </ul>
        <p>作者：{{blog.author}}</p>
    </div>
    </div>
</template>

<script>
export default {
  name: "add-blog",
  data() {
    return {
      blog: {
        title: "",
        content: "",
        categories: [],
        author: ""
      },
      authors: ["刘泽", "张三", "李四"],
      submmited: false
    };
  },
  methods: {
    post: function() {
      this.$http
        .post("http://jsonplaceholder.typicode.com/posts", {
          title: this.blog.title,
          body: this.blog.content,
          userId: 1
        })
        .then(data => {
          //   console.log(data);
          this.submmited = true;
        });
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#add-blog * {
  box-sizing: border-box;
}
#add-blog {
  margin: 20px auto;
  max-width: 840px;
  padding: 20px;
}
label {
  display: block;
  margin: 20px 0 10px;
}
input[type="text"],
textarea,
select {
  display: block;
  width: 100%;
  padding: 8px;
}
textarea {
  min-height: 200px;
  resize: none;
  line-height: 1.4em;
  text-indent: 2em;
  text-align: justify;
  border: 1px solid #ccc;
  outline: none;
  letter-spacing: 1px;
}
select {
  padding: 2px;
  font-size: 12px;
}
#checkboxes label {
  display: inline-block;
  margin-top: 5px;
}
#checkboxes input {
  display: inline-block;
  margin-right: 10px;
}
#add-blog .authors {
  margin: 5px 0 5px;
}
button {
  display: block;
  width: 120px;
  height: 40px;
  margin: 20px 0;
  background: crimson;
  color: #fff;
  border: 0;
  font-size: 16px;
  cursor: pointer;
  border-radius: 4px;
  letter-spacing: 1px;
}
button:hover {
  background: #ff0000;
}
.preview {
  padding: 10px 20px;
  border: 1px dotted #ccc;
  margin: 30px 0;
}
.preview h1 {
  font-size: 16px;
}
.preview .title {
  font-size: 20px;
}
.preview .content {
  width: 100%;
  min-height: 200px;
  border: 1px solid #ccc;
  box-sizing: border-box;
  padding: 8px;
  line-height: 1.4em;
  text-indent: 2em;
  text-align: justify;
  letter-spacing: 1px;
}
ul {
    padding: 0;
    margin: 0;
}
ul li{
    list-style: none;
    float: left;
    margin-right: 10px;
}
.preview h4{
    float: left;
    margin: 0 20px 0 0;
}
</style>
